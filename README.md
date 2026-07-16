# 🕹️ Tournament - Game Suite (TV + Mobile)

Une application de party games multijoueur local en temps réel où l'**Android TV** sert d'écran principal (déroulement, dessins et classements) et les **Téléphones Mobiles Android** (ou navigateurs web via HTTP/WebSocket) servent de télécommandes individuelles privées pour tous les joueurs.

---

## 🌟 Modes de Jeu Disponibles

L'application intègre douze types de party games distincts, sélectionnables depuis l'écran de démarrage :

### 1. 📝 **Question Tournament (Quiz de rapidité)**
*   **Description** : Répondez à des questions de culture générale le plus rapidement possible. Tout le monde répond en même temps sur son smartphone.
*   **Scoring** : Une bonne réponse rapporte des points bonifiés selon votre rapidité de réponse :
    $$\text{Points} = 500 + (\text{Temps restant en secondes} \times 25)$$
    *(Max 1 000 pts à 20s, Min 500 pts à 0s. 0 point si mauvaise réponse).*
*   **Catégories** : Plus de 1200 questions variées sans puzzle mathématique dans les rubriques classiques.

### 2. 🤥 **Fake News (Jeu de Bluff)**
*   **Description** : Remplissez les blancs avec vos pires mensonges, puis votez pour démasquer la vérité.
*   **Déroulement** :
    *   **Mensonge** : La TV affiche une anecdote vraie mais incomplète. Les joueurs tapent un mensonge sur leur téléphone en lettres majuscules.
    *   **Vote** : La TV mélange la vérité et les mensonges des joueurs. Les joueurs votent sur leur téléphone pour la proposition qu'ils pensent être la vérité.
*   **Scoring** :
    *   Trouver la bonne réponse : **+500 points**.
    *   Piéger un autre joueur avec votre mensonge : **+250 points** par joueur piégé.

### 3. 🎨 **Esquisse Masquée (Dessin et Devises)**
*   **Description** : Dessinez un mot secret sur votre téléphone et devinez ce que vos amis ont tenté de dessiner.
*   **Déroulement** :
    *   **Dessin** : Chaque joueur reçoit un sujet secret sur son écran tactile et dispose d'une ardoise tactile plein écran pour le dessiner.
    *   **Showcase & Vote** : La TV affiche les dessins un par un. L'artiste ne peut pas voter. Les autres joueurs votent en QCM sur le thème d'origine du dessin.
*   **Scoring** :
    *   Deviner correctement le thème du dessin d'un ami : **+500 points**.
    *   L'artiste gagne **+150 points** par joueur ayant trouvé son dessin (récompensant les bons dessinateurs).

### 4. 🕵️ **Le Double Jeu (Jeu d'Infiltration)**
*   **Description** : Infiltrez discrètement votre mot secret dans la discussion de salon sans vous faire démasquer.
*   **Déroulement** :
    *   **Attribution** : Chaque joueur reçoit un mot secret privé lié à un thème général commun, sauf le "Double Jeu" qui reçoit un sujet légèrement décalé.
    *   **Débat & Vote** : Les joueurs débattent librement à voix haute. À la fin du temps imparti, tout le monde vote sur son téléphone pour démasquer l'intrus.

### 5. 🧠 **Test QI (Épreuves Cognitives)**
*   **Description** : Mesurez vos capacités intellectuelles à travers quatre types d'épreuves inspirées de véritables tests psychotechniques.
*   **Épreuves** :
    *   **Suites Logiques (Matrices de Raven)** : Grille 3x3 de formes géométriques complexes (canvas Compose) évoluant selon une logique de couleur, rotation et type. Les joueurs choisissent l'option manquante (QCM sur mobile).
    *   **Intrus Spatial (Patrons & Cubes 3D)** : Tracé 2D du patron d'un cube déplié et rendu 3D temps réel à 60fps de 3 cubes en rotation. Il faut identifier le cube impossible à plier.
    *   **Intrus Sémantiques (Logique Verbale)** : Complétez des analogies de vocabulaire complexes (soit par QCM, soit par saisie de texte libre sur mobile).
    *   **Calcul Mental Flash (Cascade d'opérations)** : Une cascade d'opérateurs mathématiques défile rapidement dans un cercle sur la TV. Les joueurs doivent saisir le résultat final sur un pavé numérique (Numpad mobile).
*   **Scoring & IQ final** : 
    *   Scores cumulés avec bonus de vitesse et verrouillage de multiplicateur x2 pour le premier répondant correct (Intrus Spatial).
    *   Les scores généraux sont traduits à la fin de la partie en un score d'IQ final standardisé (de 75 à 145) affiché sur la TV et les téléphones.

### 6. 🧸 **Bazar Quiz (Jeu d'Observation)**
*   **Description** : Observez une chambre d'ado chaotique pendant 25 secondes et répondez à des questions sur les moindres détails.
*   **Gameplay** : Phase de mémorisation puis questions en QCM sur le mobile.

### 7. 🔁 **Echo Simon (Mémoire et Rythme)**
*   **Description** : Écoutez la séquence de couleurs et de notes de musique jouée par la TV et reproduisez-la exactement sur l'interface circulaire de votre mobile.
*   **Variantes** :
    *   *Classique* : Reproduction standard.
    *   *Invisible* : Les quadrants colorés de la TV restent noirs, seule la note de musique indique la touche à presser.
    *   *Chaises Musicales* : L'emplacement physique des boutons sur le téléphone est mélangé à chaque phase de réponse.
    *   *Coopératif* : Les joueurs se partagent la séquence en jouant chacun leur tour.

### 8. 🔗 **Brain Link (Association d'Idées & Rapidité)**
*   **Description** : Trouvez le mot mystère associé à une série d'indices révélés un à un toutes les 5 secondes sur la TV.
*   **Variantes** :
    *   *Standard* : Indices révélés l'un après l'autre. Rapidité récompensée.
    *   *L'Intrus Caché* : Trouvez le mot mystère et identifiez l'intrus parmi les 4 indices proposés pour doubler vos points.
    *   *Le Maillon Faible (Coopératif)* : La TV n'affiche qu'un chrono. Les indices sont partagés en secret entre les téléphones des joueurs qui doivent communiquer à voix haute pour taper le même mot.
*   **Tolérance orthographique (Levenshtein)** : L'application intègre un algorithme de comparaison orthographique pour valider les propositions des joueurs même en cas de faute de frappe mineure (ex: "pino" au lieu de "piano").
*   **Scoring** : $+300$ pts (1er indice), $+200$ pts (2e), $+100$ pts (3e+), et $-50$ pts par mauvaise proposition (permettant de retenter).

### 9. 🧱 **Brick Break Coop (Casse-briques coopératif)**
*   **Description** : Un casse-briques / arkanoid multijoueur où les joueurs déplacent leurs raquettes sur le même écran.
*   **Mécanique tactile modernisée** : Les segments où les raquettes des joueurs se chevauchent deviennent des zones "fantômes" non solides (les balles passent au travers) et font vibrer les smartphones des joueurs concernés pour encourager la coordination spatiale.

### 10. 🐍 **Snack Attack (Arcade Snake & Sabotage)**
*   **Description** : Un jeu de type Snake / Tron multijoueur sur la TV où le but est de survivre et forcer les autres serpents à percuter votre corps.
*   **Mode Sabotage smartphone** : Les joueurs éliminés sur la TV ne s'ennuient pas ! Leurs smartphones se transforment en lanceurs de malus pour saboter la partie en cours (faire apparaître des murs de briques, inverser les commandes d'un joueur vivant, ou accélérer brutalement la vitesse globale).

### 11. 📳 **Vibro-Synchro (Rythme Haptique Coopératif)**
*   **Description** : Un jeu de synchronisation collective basé sur les vibrations des smartphones. La TV affiche un pulsar visuel qui bat la mesure ; chaque téléphone vibre avec un décalage aléatoire au départ.
*   **Gameplay** : Chaque joueur tape sur son écran au moment exact du battement TV. Un tap précis resynchronise progressivement sa vibration sur le tempo commun ; un tap hors-rythme le désynchronise. L'objectif : que toute la salle vibre à l'unisson avant la fin des 30 secondes.
*   **Énergie Globale** : La TV affiche une jauge d'énergie collective (moyenne de synchronisation de tous les joueurs). Atteindre 100% déclenche la victoire immédiate.
*   **Scoring** : Chaque joueur marque son taux d'alignement final (0 à 100) × 10 points.

### 12. 🖼️ **L'Imposteur de l'Art (Dessin Collaboratif & Bluff)**
*   **Description** : Tous les joueurs dessinent ensemble le même mot secret sur une toile TV partagée... sauf l'imposteur, qui ne connaît pas le mot et doit improviser sans se faire repérer.
*   **Déroulement** :
    *   **Dessin à tour de rôle** : Chaque joueur ajoute un unique trait à la toile commune pendant son tour de 5 secondes, sur 2 tours de table complets. L'imposteur doit dessiner de façon crédible en observant les traits des autres.
    *   **Vote** : À la fin des tours de dessin, tous les joueurs votent sur leur téléphone pour désigner l'imposteur (15 secondes).
*   **Scoring** :
    *   Voter correctement pour l'imposteur : **+1 000 points**.
    *   L'imposteur non démasqué (pas majoritaire au vote) : **+1 500 points**.

---

## 🎨 Fonctionnalités & Expérience Utilisateur

*   **Zéro configuration Cloud** : Fonctionne entièrement sur votre réseau Wi-Fi local grâce à un protocole WebSocket ultra-rapide.
*   **Ressources Sonores Double Canal** :
    *   *Menu & Lobby* : Musique relaxante et chaleureuse (`lobby.mp3`) en fond sonore lors de la sélection des jeux et dans le salon d'attente.
    *   *Chronos Actifs* : Bande-son tendue et rythmée (`countdown.mp3`) jouée sur tous les comptes à rebours de jeu.
*   **Mascotte Interactive & Dynamique** : Une mascotte animée sur TV réagit aux événements du jeu (devient K.O. lorsqu'il reste 5 secondes ou moins au chrono, exulte lors des révélations).
*   **Sécurité Navigation Télécommande TV** : Appuyer sur la touche Retour ou Échap de la télécommande TV dans le salon d'attente (`LOBBY`), la sélection de questions (`SETUP_COUNT`) ou l'écran final (`GAME_OVER`) renvoie proprement à la sélection des jeux au lieu de fermer brutalement l'application.
*   **Ardoise Tactile fluide** : Intégration d'un Canvas de dessin tactile plein écran avec boutons "Effacer" et "Envoyer" sur mobile. Les dessins sont compressés et transférés instantanément par Base64 (environ 20 Ko).
*   **Anti-Cheat (Écrans de Verrouillage)** : Dès qu'une réponse ou un vote est soumis sur le smartphone, l'interface de choix est instantanément masquée et remplacée par un écran de chargement discret. Les réponses et options ne sont plus visibles, éliminant tout risque de triche ou de copie entre joueurs dans la même pièce.
*   **Configuration TV D-Pad intuitive** : Sélection des jeux et du nombre de questions via la télécommande de la TV avec focus visuels cyan/verts et contours de sélection blancs épais.
*   **Boucle de Rejouabilité Fluide** :
    *   **Depuis la TV** : Bouton `[Recommencer la partie]` pour relancer directement avec les mêmes joueurs.
    *   **Depuis les Téléphones** : Bouton `[Prêt à rejouer !]` pour redémarrer automatiquement dès que tous les joueurs se sont déclarés prêts.

---

## 🏗️ Architecture du Projet

Le projet est divisé en deux modules Android natifs structurés selon une architecture modulaire découplée (1 dossier = 1 jeu) :

### 📂 Structure Modulaire Commune
Chaque jeu est implémenté de manière autonome dans son propre package sous `com.ticonetv.tournament.games.<jeu>` :
*   **Logique TV (`*Game.kt`)** : Implémente `GameModule` (pour gérer l'état initial, les messages réseau et les ticks du jeu) et `TvGameRenderer` (pour le rendu sur l'écran TV).
*   **Logique Mobile (`*Mobile.kt`)** : Implémente `MobileGameRenderer` (pour rendre l'interface tactile sur les smartphones des joueurs).
*   **Enregistrement dynamique** : Les modules s'enregistrent dynamiquement auprès de `GameRegistry` (sur la TV) et de `MobileGameRegistry` (sur le mobile), permettant d'ajouter ou d'enlever des jeux simplement sans modifier le cœur de l'application.

### 📺 Module `:tv` (Host)
*   Démarre un serveur WebSocket local (port `8080`) pour gérer les messages temps réel.
*   Gère le moteur général de salon (`GameViewModel`), le serveur Web pour les télécommandes, les scores globaux et les bruitages de fond (`lobby` et `countdown`).
*   Affiche l'écran TV partagé et délègue le rendu du jeu actif au module sélectionné.

### 📱 Module `:mobile` (Remote)
*   Se connecte au serveur WebSocket de la TV via l'IP locale.
*   Affiche l'ardoise de dessin tactile, les pavés numériques (Numpad) ou les grilles de choix selon le jeu actif reçu via l'état `MODULAR_PLAY` délégué au module mobile correspondant.
*   Sert également une version Web de la télécommande sur le port `8081` (`controller.html`) pour permettre de jouer depuis n'importe quel appareil connecté au Wi-Fi.

---

## 🛠️ Configuration et Compilation

### Prérequis
*   **Android SDK (API 29+)** installé sur votre machine.
*   Un réseau Wi-Fi local reliant la TV (ou l'émulateur) et les téléphones.

### Compilation
Pour compiler et générer les fichiers APK de debug pour la TV et les téléphones, exécutez à la racine :

```powershell
./gradlew assembleDebug
```

Les fichiers APK se trouvent dans :
*   TV : `tv/build/outputs/apk/debug/tv-debug.apk`
*   Mobile : `mobile/build/outputs/apk/debug/mobile-debug.apk`

---

## 🎮 Comment Jouer

1.  **Configurer la Partie sur la TV** :
    *   Lancez l'application `:tv`.
    *   Sélectionnez l'un des jeux à l'aide des flèches directionnelles de la télécommande.
    *   L'écran de lobby s'affiche avec l'adresse IP locale de la TV (ex: `192.168.1.100`).
2.  **Connecter les Téléphones** :
    *   Lancez l'application `:mobile` (ou accédez à l'IP de la TV sur port 8081 via un navigateur).
    *   Saisissez votre pseudo et l'adresse IP de la TV, puis appuyez sur **Rejoindre la TV**.
3.  **Lancer la Partie** :
    *   Lorsque tous les pseudos apparaissent dans le lobby de la TV, le premier joueur connecté (l'hôte) peut appuyer sur **Commencer la partie !** sur son smartphone.
4.  **Fin et Revanche** :
    *   À l'écran final, appuyez sur **Recommencer la partie** sur la TV ou sur **Prêt à rejouer !** sur tous les téléphones pour relancer instantanément une nouvelle partie !
