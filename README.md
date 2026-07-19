# 🕹️ Tournament - Game Suite (TV + Mobile)

Une application de party games multijoueur local en temps réel où l'**Android TV** sert d'écran principal (déroulement, dessins et classements) et les **Téléphones Mobiles Android** (ou navigateurs web via HTTP/WebSocket) servent de télécommandes individuelles privées pour tous les joueurs.

---

## 🌟 Modes de Jeu Disponibles

L'application intègre seize types de party games distincts, sélectionnables depuis l'écran de démarrage :

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
*   **Description** : Un jeu de type Snake / Tron multijoueur sur la TV où le but est de survivre et forcer les autres serpents à percuter votre corps. Compte à rebours "3, 2, 1, GO !" au départ, rendu fluide interpolé (mouvement continu, yeux orientés, particules, secousses d'écran pendant le séisme) et bruitages arcade (miam, power-up, cri d'élimination).
*   **Contrôles** : Joystick virtuel sur smartphone et navigateur (glisser dans la direction voulue, retour haptique à chaque changement de direction).
*   **Bonus sur la grille** : 🍎 Pomme (+10, grandit), ⭐ Fruit doré (+50, grandit ×2, disparaît si on tarde), 🛡️ Bouclier (+10, invincible + traverse les murs quelques secondes), ⚡ Turbo (+10, vitesse double personnelle), 🧪 Potion rétrécissante (+15 et raccourcit le serpent). Chaque joueur a son propre score, crédité au classement en fin de manche (+50 pour le survivant).
*   **Mode Sabotage smartphone** : Les joueurs éliminés sur la TV ne s'ennuient pas ! Leurs smartphones se transforment en lanceurs de malus pour saboter la partie en cours (faire apparaître des murs de briques, inverser les commandes d'un joueur vivant, accélérer brutalement la vitesse globale, ou mélanger la position des fruits).

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

### 13. 🎤 **Punchline Battle (Humour & Duels de Votes)**
*   **Description** : Chaque joueur reçoit un thème et écrit la meilleure vanne possible sur son téléphone, puis la salle vote lors de duels en tête-à-tête.
*   **Déroulement** :
    *   **Écriture** : Un appariement circulaire fait que chaque joueur participe à exactement deux duels et rédige donc deux punchlines.
    *   **Vote** : La TV affiche les duels un par un (auteur A vs auteur B, anonymisés). Les joueurs non concernés votent pour la punchline la plus drôle.
*   **Scoring** : Des points sont attribués selon les votes reçus par chaque punchline dans son duel.

### 14. ☠️ **Quiz Mortel (Quiz de Survie & Épreuves)**
*   **Description** : Un quiz de culture générale à élimination : répondre juste vous garde en vie, une mauvaise réponse vous envoie dans une épreuve de la "salle des supplices".
*   **Épreuves de danger** : les joueurs ayant échoué à la question passent au hasard par la *Roulette* (choisir une case non piégée), le *Matraquage* (marteler un bouton) ou le *Calcul* (résoudre une opération en QCM) — échouer élimine le joueur.
*   **Objectif** : être le dernier survivant / accumuler le plus de bonnes réponses.

### 15. 🚀 **Panique en Cabine (Coopératif sous Pression)**
*   **Description** : Un jeu coopératif de coordination effrénée façon "salle des machines". Chaque joueur dispose d'un panneau de contrôle unique (boutons, interrupteurs et curseurs aux noms loufoques comme « Turbo-cornichon »).
*   **Déroulement** : La TV donne à chaque joueur une consigne qui concerne… la commande d'un **autre** joueur. Il faut donc crier les instructions à voix haute pour que le bon coéquipier actionne la bonne commande avant la fin du compte à rebours.
*   **Enjeu collectif** : Chaque consigne ratée endommage la coque du vaisseau (jauge d'intégrité commune). Tenez le plus longtemps possible et faites grimper le score d'équipe.

### 16. 📊 **Sondage Piège (Estimation & Paris)**
*   **Description** : Un jeu de pari basé sur des statistiques surprenantes. À chaque manche, un joueur actif estime la réponse chiffrée (souvent un pourcentage) à une question de sondage.
*   **Déroulement** : Une fois l'estimation posée, les autres joueurs parient sur leur téléphone : la vraie valeur est-elle **plus haute** ou **plus basse** que l'estimation ? Chaque joueur passe à tour de rôle dans le rôle de l'estimateur.
*   **Scoring** : Points aux joueurs ayant correctement parié plus haut / plus bas par rapport à la vraie réponse.

---

## 🎨 Fonctionnalités & Expérience Utilisateur

*   **Zéro configuration Cloud** : Fonctionne entièrement sur votre réseau Wi-Fi local grâce à un protocole WebSocket ultra-rapide.
*   **Reconnexion automatique** : Un joueur qui perd le Wi-Fi ou met son téléphone en veille reste dans la partie (score conservé) pendant 30 secondes le temps de revenir ; l'app mobile et la télécommande web retentent la connexion automatiquement (backoff 1→5 s) au lieu de renvoyer à l'écran de connexion.
*   **Écran "Comment jouer"** : Au lancement de chaque jeu, la TV affiche 7 secondes de règles résumées (3 puces + mascotte) avant la manche 1, pour que les nouveaux joueurs ne perdent pas la première manche par méconnaissance des règles.
*   **Identité visuelle par jeu** : Chaque jeu a sa couleur d'accent (menu TV, écran de règles, contrôleur mobile et navigateur), pour une reconnaissance immédiate du jeu en cours sur tous les écrans.
*   **Transitions animées** : Tout changement d'écran sur la TV (sélection, salon, jeu, fin de partie) se fait en fondu-glissement plutôt qu'en cut sec.
*   **Cérémonie de podium** : L'écran de fin de partie révèle le classement en 3 temps (3ᵉ place, 2ᵉ place, roulement de tambour puis 1ᵉʳ) avec pluie de confettis, plutôt qu'un classement affiché d'un coup.
*   **Ressources Sonores Double Canal** :
    *   *Menu & Lobby* : Musique relaxante et chaleureuse (`lobby.mp3`) en fond sonore lors de la sélection des jeux et dans le salon d'attente.
    *   *Chronos Actifs* : Bande-son tendue et rythmée (`countdown.mp3`) jouée sur tous les comptes à rebours de jeu.
*   **Réglages audio** : Volumes musique et bruitages réglables séparément (0-100 %) depuis un écran dédié sur la TV, persistés entre les sessions.
*   **Mascotte Interactive & Dynamique** : Une mascotte animée sur TV réagit aux événements du jeu (devient K.O. lorsqu'il reste 5 secondes ou moins au chrono, exulte lors des révélations, présente les règles et le podium).
*   **Sécurité Navigation Télécommande TV** : Appuyer sur la touche Retour ou Échap de la télécommande TV dans le salon d'attente (`LOBBY`), la sélection de questions (`SETUP_COUNT`) ou l'écran final (`GAME_OVER`) renvoie proprement à la sélection des jeux au lieu de fermer brutalement l'application.
*   **Ardoise Tactile fluide** : Intégration d'un Canvas de dessin tactile plein écran avec boutons "Effacer" et "Envoyer" sur mobile. Les dessins sont compressés et transférés instantanément par Base64 (environ 20 Ko).
*   **Anti-Cheat (Écrans de Verrouillage)** : Dès qu'une réponse ou un vote est soumis sur le smartphone, l'interface de choix est instantanément masquée et remplacée par un écran de chargement discret. Les réponses et options ne sont plus visibles, éliminant tout risque de triche ou de copie entre joueurs dans la même pièce.
*   **Configuration TV D-Pad intuitive** : Sélection des jeux et du nombre de questions via la télécommande de la TV avec focus visuels cyan/verts et contours de sélection blancs épais, tuiles agrandies et surlignées par la couleur du jeu au focus.
*   **Boucle de Rejouabilité Fluide** :
    *   **Depuis la TV** : Bouton `[Recommencer la partie]` pour relancer directement avec les mêmes joueurs.
    *   **Depuis les Téléphones** : Bouton `[Prêt à rejouer !]` pour redémarrer automatiquement dès que tous les joueurs se sont déclarés prêts.
*   **Contenu enrichi** : Les banques de contenu des jeux les plus légers (Le Double Jeu, Sondage Piège, Brain Link, Punchline Battle, Esquisse Masquée) ont été considérablement étoffées pour limiter les répétitions d'une partie à l'autre.

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
