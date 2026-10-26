# IA Bible ✝

**IA Bible** est un site bilingue de découverte de la Bible et de la foi catholique. Il rassemble un assistant de questions-réponses, des repères bibliques et liturgiques, des prières et des ressources musicales dans une interface accessible depuis un navigateur.

<img width="1456" height="802" alt="image" src="https://github.com/user-attachments/assets/9bf1f42a-b504-4460-a216-11fe9d1e9d61" />


## Ce que le site propose

- **Assistant biblique et catholique** : pose des questions comme « Qui est Jésus ? », sur un passage biblique, la prière, les sacrements ou l’enseignement catholique. Avec le serveur lancé, les réponses sont produites par le modèle local configuré dans Ollama (par défaut `gemma4:e2b`). Le serveur recherche si possible des paragraphes du Catéchisme via TheoFons et les lectures du jour via l’AELF lorsque la question les concerne. Les réponses peuvent citer des références et doivent être vérifiées auprès des sources.
- **Français et anglais** : le bouton de langue traduit l’interface et adapte la langue des réponses de l’assistant.
- **Mode clair et sombre** : le thème choisi est mémorisé dans le navigateur.
- **Verset du jour** : le site essaie de charger le verset depuis Holy Bible API, avec un verset AELF en solution de repli.
- **Lectures liturgiques du jour** : recherche des lectures publiées par l’API AELF.
- **Louanges** : liste filtrable de chants et psaumes, avec recherche de vidéos sur YouTube. Sans clé API configurée, le site propose d’ouvrir les résultats sur YouTube ; avec une clé, il peut afficher jusqu’à cinq résultats sur le site.
- **Prières à connaître** : prières de la tradition catholique, dont le Je crois en Dieu et le Je confesse à Dieu, avec leur texte et des liens de référence.
- **Calendrier liturgique** : prochaines fêtes catholiques, dont les dates mobiles calculées à partir de Pâques. Clique sur un événement pour lire ce qu’il représente. Les explications suivent la langue sélectionnée.
- **Explorer et pratiquer** : recherche web limitée aux pages AELF, parcours de lecture biblique sur sept jours, prière et repère chrétien du jour, quiz biblique, intention de prière enregistrée localement, favoris, historique récent, réglage de la taille du texte et navigation mobile.
- **Actions sur les réponses** : copier, partager avec les fonctions de l’appareil, enregistrer dans les favoris et poursuivre avec des questions suggérées. Les réponses plus longues de l’agent suivent des sections courtes.
- **Lecteur biblique AELF** : choisis un livre et un chapitre, puis navigue au chapitre précédent ou suivant. Le chapitre s’affiche depuis le site AELF dans le lecteur intégré ; un bouton permet aussi de l’ouvrir directement sur AELF.
- **Paramètres personnalisables** : modifie la taille du texte et choisis une couleur de fond (sauge, rose, bleu, jaune ou lavande). Le choix reste mémorisé sur l’appareil.
- **Carte des églises** : cherche les lieux de culte par ville ou code postal, ou autorise la géolocalisation après avoir cliqué sur « Utiliser ma position ». La carte et les résultats sont fournis par Google Maps.
- **Mise en page adaptée** aux écrans d’ordinateur et de téléphone, avec une signature dans le pied de page.

## Deux façons d’utiliser le site

### Aperçu sans installation

Tu peux ouvrir `index.html` directement dans ton navigateur ou publier les fichiers statiques sur GitHub Pages. L’interface, les prières, les louanges et le calendrier restent disponibles, et certaines réponses guidées sont intégrées. Les chargements de données externes dépendent de la disponibilité des API et des règles du navigateur.

Cette version ne lance pas Ollama ni Python. Pour utiliser l’assistant génératif Ollama, suis les étapes ci-dessous.

### Tester le projet depuis GitHub

**Pour simplement découvrir le site**, ouvre le lien GitHub Pages communiqué par la personne qui publie le projet. Il est généralement de la forme `https://NOM-GITHUB.github.io/NOM-DU-DEPOT/`. Si aucun lien Pages n’est indiqué, la personne qui gère le dépôt peut le trouver ou l’activer dans **Settings → Pages**. La page GitHub du dépôt permet de consulter le code, mais ce n’est pas à elle seule le site web.

**Pour tester aussi le véritable assistant IA sur ton ordinateur**, il faut récupérer le projet et installer Ollama :

1. Installe [Git pour Windows](https://git-scm.com/download/win), [Python](https://www.python.org/downloads/windows/) et [Ollama](https://ollama.com/download/windows), si tu ne les as pas déjà.
2. Sur la page GitHub du projet, clique sur **Code → HTTPS** et copie l’adresse du dépôt.
3. Dans le terminal de VS Code, clone le dépôt en remplaçant l’adresse d’exemple par celle que tu as copiée :

```powershell
git clone https://github.com/VOTRE-NOM/Christianisme.git
cd Christianisme
```

4. Suis ensuite les étapes de la section **Tester l’agent avec Ollama sur Windows** : vérifie Ollama avec `ollama list`, télécharge le modèle avec `ollama pull gemma4:e2b`, puis lance `python server.py`.
5. Ouvre **http://127.0.0.1:8000** dans ton navigateur. Le site tourne sur le port **8000** et Ollama sur le port **11434**.

L’aperçu Pages ne demande aucune installation, mais il n’utilise pas le modèle Ollama de ton ordinateur. Pour tester l’assistant génératif, chaque testeur doit lancer Ollama et le serveur localement, sauf si le propriétaire du projet a déployé un serveur IA public.

## Installer et lancer Ollama sur Windows

Suis ces étapes dans l’ordre pour tester l’agent IA en local. Il faut deux terminaux VS Code : Ollama communique sur le port **11434** et le site web sur le port **8000**.

### Étape 1 — Installer Ollama

1. Télécharge Ollama depuis le [site officiel](https://ollama.com/download/windows).
2. Ouvre `OllamaSetup.exe`, termine l’installation et démarre l’application Ollama.
3. L’API locale d’Ollama est accessible sur **http://127.0.0.1:11434**. Garde Ollama ouvert pendant l’utilisation.

### Étape 2 — Vérifier Ollama dans le premier terminal

Dans VS Code, ouvre **Terminal → Nouveau terminal** et exécute :

```powershell
ollama list
```

Si Ollama ne répond pas, démarre son service dans ce premier terminal :

```powershell
ollama serve
```

Laisse ce terminal ouvert. Si Ollama signale que le port **11434** est déjà utilisé, son service fonctionne probablement déjà ; tu peux continuer.

### Étape 3 — Ouvrir le dossier du projet dans un deuxième terminal

Ouvre **un deuxième terminal** dans VS Code, puis va dans le dossier où tu as cloné le dépôt. Remplace le chemin d’exemple par le chemin réel de ton dossier :

```powershell
cd "C:\chemin\vers\Christianisme"
```

### Étape 4 — Télécharger le modèle IA

Dans ce deuxième terminal, exécute :

```powershell
ollama pull gemma4:e2b
```

Le téléchargement peut prendre quelques minutes et n’est nécessaire qu’une seule fois.

### Étape 5 — Démarrer le site

Toujours dans le deuxième terminal, lance le serveur web :

```powershell
python server.py
```

Le site démarre sur le port **8000**. Laisse le terminal ouvert ; `Ctrl+C` arrête le serveur. Le serveur Python contacte Ollama sur le port **11434**.

### Étape 6 — Ouvrir le site

Dans ton navigateur, ouvre exactement : **http://127.0.0.1:8000**

N’ouvre pas `index.html` directement si tu veux utiliser le modèle : l’agent IA fonctionne par le serveur sur le port **8000**, qui appelle Ollama sur le port **11434**.

Récapitulatif : 
Terminale 1 
<img width="1116" height="312" alt="image" src="https://github.com/user-attachments/assets/7c8f38e2-9811-4e2b-b8a1-300d571724b1" />

Terminale 2 :
<img width="942" height="266" alt="image" src="https://github.com/user-attachments/assets/223449e8-fb7e-4a51-9c5c-dab1c03f2a40" />
Puis : Dans ton navigateur, ouvre exactement : **http://127.0.0.1:8000**


### Activer les résultats YouTube intégrés (facultatif)

Le bouton YouTube ouvre une recherche YouTube même sans configuration. Pour afficher les résultats vidéo directement sur le site, crée une clé dans Google Cloud, active **YouTube Data API v3**, puis définis la clé dans le terminal avant de lancer le serveur :

```powershell
$env:YOUTUBE_API_KEY = "TA_CLE_API"
python server.py
```

La recherche utilise l'API officielle `search.list` et le serveur limite son usage à 80 recherches par jour. Le quota standard documenté par YouTube est de 100 appels de recherche par jour. Garde la clé dans cette variable d'environnement : ne la place pas dans `app.js`, dans le HTML ou dans GitHub. Voir [la documentation YouTube Data API](https://developers.google.com/youtube/v3/docs/search/list) et [la création des identifiants](https://developers.google.com/youtube/registering_an_application).

### Utiliser un autre port pour le site (facultatif)

Le port par défaut est **8000**. Pour en choisir un autre, définis la variable avant de démarrer le serveur :

```powershell
$env:PORT = "8080"
python server.py
```

Le site sera alors à `http://127.0.0.1:8080`.

## Hébergement public

GitHub Pages peut héberger la version HTML d'aperçu, mais ne peut pas exécuter `server.py` ni le modèle Ollama. Pour que d'autres personnes utilisent le véritable agent sans rien installer, héberge le serveur Python sur une machine qui peut joindre Ollama. Sur un hébergeur, configure `HOST=0.0.0.0` et utilise le port fourni par celui-ci (`PORT`). Ne rends pas directement public le port Ollama **11434**.

Le serveur utilise la bibliothèque standard de Python ; aucun `pip install` n'est requis. `OLLAMA_MODEL` permet de choisir le modèle et `OLLAMA_URL` l'adresse du serveur Ollama. Le backend limite le nombre de requêtes par adresse IP et ne conserve pas les conversations.

### Ce que signifie « accessible sur Internet »

GitHub Pages publie les fichiers de la page, mais **ne démarre pas le modèle Ollama**. Avec l’hébergement statique seul, tout le monde peut consulter les fonctions du site qui marchent dans le navigateur, mais l’assistant Ollama ne répondra pas aux visiteurs. Pour cela, il faut aussi déployer `server.py` sur un hébergeur capable d’exécuter Python, et rendre le modèle Ollama joignable par ce serveur. Les visiteurs n’auront alors besoin que d’un navigateur ; l’installation et l’hébergement du modèle se font côté serveur. Une configuration de l’URL de l’API côté site sera également nécessaire si le site et le serveur sont hébergés sur des domaines différents.

## Fichiers du projet

- `index.html` : structure et contenu de la page.
- `style.css` : mise en page, affichage mobile et thèmes clair/sombre.
- `app.js` : changement de langue, interface de discussion, ressources, calendrier et appels aux API publiques.
- `server.py` : serveur web local, connexion à Ollama, récupération de références documentaires et recherche YouTube facultative.
- `README.md` : présentation et étapes de lancement.

## Sources utilisées

- [Bible AELF](https://www.aelf.org/bible) et [API AELF](https://api.aelf.org/) pour les textes et les lectures liturgiques.
- [Holy Bible API](https://holy-bible-api.com/docs/) pour essayer de charger le verset du jour ; le verset AELF reste affiché en solution de repli.
- [YouTube Data API](https://developers.google.com/youtube/v3/docs/search/list) pour rechercher des vidéos de louange si la clé facultative `YOUTUBE_API_KEY` est configurée. Sinon, le site ouvre directement la recherche YouTube.
- [TheoFons](https://theofons.net/la/api) pour retrouver un paragraphe pertinent du Catéchisme. C'est un corpus tiers ; ses textes restent soumis aux droits de leurs ayants droit.
- Références officielles : [Catéchisme de l'Église catholique](https://www.vatican.va/archive/FRA0013/_INDEX.HTM), [site du Vatican](https://www.vatican.va/content/vatican/fr.html) et [documents pontificaux](https://www.vatican.va/offices/papal_docs_list_fr.html).

Le texte final est généré par le modèle Ollama et peut contenir des erreurs. L'assistant ne remplace ni un prêtre ni une autorité de l'Église. Vérifie les citations et les questions doctrinales auprès des sources officielles.

Les favoris, l’intention de prière, la taille du texte et l’historique sont enregistrés dans le stockage local du navigateur. Ils ne sont pas synchronisés entre appareils ; l’historique peut être effacé depuis la page.

## Lience
Réalisé par ANTON NELCON Steve

La position n’est pas demandée au chargement du site. Si tu choisis la recherche autour de toi, les coordonnées servent à former la recherche envoyée à Google Maps. Tu peux aussi chercher une ville sans partager ta position.
