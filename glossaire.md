# GLOSSAIRE

- [Général](#général)
- [Front-end](#front-end)
- [UX / UI](#ux-ui)
- [Architecture](#architecture)
- [Modélisation / Base de données](#modélisation---base-de-données)
- [Symfony](#symfony)
- [Sécurité](#sécurité)
- [RGPD](#rgpd)
- [SEO](#seo)
- [Gestion de projets / DevOps](#gestion-de-projets---devops)
- [English](#english)

## Général
1.	Quel est l’environnement à installer pour exécuter un script PHP ? Citer 2 exemples de logiciels permettant ce contexte
    VS code et Laragon / MAMP

2.	Qu’est-ce qu’un algorithme ?  
    C'est une suite d'instructions organisées (séquentiel (exécution d'instructions) et procédurale (exécution de fonctions))

3.	Qu’est-ce qu’une variable ? Par quel symbole est préfixée une variable en PHP ?
    Emplacement mémoire permettant de stocker une valeur symbolisé par le dollar $.

4.	Qu’est-ce que la portée d’une variable ?
    La portée d'une variable correspond à son champ d'action (superglobale / globale / locale)

5.	Qu’est-ce qu’une constante ? Quelle est la différence avec une variable ?
    Une constante a une valeur qui n'a pas vocation a changé contrairement à la variable qui varie.

6.	Qu’est-ce qu’une superglobale, combien en existent-ils et donner un exemple d’utilisation 

    La portée de la superglobale est externe à son script.

    $_GET : Contient les données envoyés en paramètre d'url (ex : récupérer l'id d'un article dans l'url pour l'afficher)
    $_POST : Contient les données envoyées par le biais d'un formulaire
    $_SESSION : Permet de stocket et de récupérer les données de sessions du user (ex: garder le user connecté d'une page à l'autre)
    $_COOKIE : Contient les cookies (locaux) envoyés par le navigateur du user (ex: se souvenir de sa langue préféré)
    $_SERVER : Fournit les infos sur le serveur et l'environnement d'exécution (ex : connaitre l'adresse ip du user)
    $_FILES : Permet de gérer les fichiers envoyés via un formulaire HTML (dl une photo de profil via un formulaire)
    $_REQUEST : Contient les données envoyés par GET, POST, COOKIE, SERVER (ex : accéder aux données d'un form peut importe la méthode get ou post)

7.	Quels sont les différents types (primitifs) que l’on peut associer à une variable en PHP ? Les citer et en donner des exemples (ne pas oublier le type d’une variable sans valeur)
    - string/str : chaine de caractères  = "bonjour";
    - entier/int : nombre = 50;
    - flottant/float : nombre décimal = 50.2;
    - boolean/bool : vrai / faux = true;
    - tableau/array : tableau = [1, "nom];
    - objet/object : class car { public $marque} $mycar = new car();  
    - null : var sans valeur

8.	Existe-t-il plusieurs types de tableaux en PHP, si oui lesquels ?
    Tableaux indexés array("1", "2", "3");
    Tableaux associatifs (key => value)
    Tableaux multidimensionnels (tableaux dans tableaux)
    
9.	Quelles sont les différentes structures de contrôles qu’il existe en algorithmie ? Donner un exemple pour chacune d’entre elles
    - Structures conditionnelles : 
        * if ($age < 1) { 
            echo "Jeune mineur";
        } else if ($age < 18) {
            echo "mineur";
        } else {
            echo "Majeur";
        }

        * switch (true){
            case ($age < 18): 
                echo "Mineur";
                break;
            case ($age > 18):
                echo "Majeur";
                break;
            }
    - Boucles :
        * while : Exécute le code tant que la condition est vraie (nb occurence inconnue)
        * do while : Exécute le code au moins une fois, puis tant que la condition est vraie
        * for : Exécute le code selon un nb d'occurence connu
        * foreach : Utiliser pour itérer sur tableaux / collections (array, objets, listes, sets, dicos)

    - Structures de contrôle de flux :
        * break - continue - return
    
    - Structures de contrôle conditionnelles multiples
        * ternaire echo ($age < 1) ? "Jeune mineur" : (($age < 18) ? "Mineur" : "Majeur");

10.	Quelle est la fonction PHP permettant de demander la longueur d’une chaîne de caractères ?
    strlen("Bonjour tout le monde");

11.	Qu’est-ce qu’une session ? Quelle fonction permet de démarrer une session en PHP ? Donner un exemple d’utilisation en PHP
    Permet de garder le user connecté d'une page à une autre. (auth ou info temp (ex: panier))

    session_start() : doit être mentionné en début de script sur la page que l'on souhaite enregistrer
    $_SESSION sera sur les autres pages où l'on souhaite garder en mémoire l'enregistrement

12.	Qu’est-ce qu’un cookie ? Donner un exemple d’utilisation en PHP
    Permet de sauvegarder les informations localement sur le navigateur du user

    Création d'un cookie pour 1j : 
    ex : setcookie("user", "Lily", time() + 86400, "/"); 
    Lecture d'un cookie :
    if (isset($_COOKIE["user"])) {
        echo "Bienvenue, ".$_COOKIE["user]; 
    } else {
            echo "Cookie not find";
    }
    Supprimer un cookie: setcookie() avec date dans le passé


13.	Quelle est la différence entre les instructions « require » et « include » en PHP
    require : Utlisé pour un fichier essentiel (ex : config de bibliothéque)        
    include : Utilisé pour un fichier non essentiel (ex: file interface user)
    require_once et include_once : fichier inclus une seule fois

14.	Comment effectuer une redirection en PHP ?
    ex : permet de diriger automatiquement le user vers une nouvelle page après avoir valider un form 

    header("Location : https://www.site.com/2e_page.php");
    exit(); (permet d'arrêter la lecture du script)

15.	Définir la partie « front-end » et « back-end » d’une application
    Front-end : Partie interactive et visible par le user
    Back-end : Partie cachée qui permet de gérer les interactions avec le serveur et les données

16.	Définir le contrôle de version ? Qu’est-ce que Git ?
    Contrôle de version : Système qui enregistre les modifications apportées à un projet et de suivre l'historique. Permet le travail organisé en équipe et la gestion de conflits.
    Git : Système de contrôle distribué, chaque dév travaille sur un projet en local

17.	Qu’est-ce qu’un CMS ? Citer au moins 2 exemples
    *Content Management System : Permet de concevoir et de gérer des sites web grâce à une interface conviviale et sans besoin de compétences techniques
    Wordpress / Shopify

## Front-end
18.	Définir HTML
    HyperText Markup Language : langage de balisage permettant de structurer une page

19.	Définir CSS
    Cascading Style Sheets : Permet de mettre en page HTML 

20.	Définir Javascript 
    Langage de programmation :
        - front end : permettant de rajouter de l'interactivité et du dynamisme aux pages web
        - back end : permet de gérer le serveur/la sécurité, traiter les données

21.	Définir JSON. Dans quel contexte ce format est-il utilisé ? 
    JavaScript Object Notation (format léger de représentation de données) : Permet de stocker et d'échanger les données entre le FE et le BE

22.	Peut-on interpréter du Javascript côté serveur ? Si oui, comment ?
    Oui, grâce à un environnement d'éxécution comme node.js. Il permet de jongler entre FE et BE, permet de gérer le serveur/la sécurité, traiter les données, de performer pour les appli en temps réel

23.	Qu’est-ce qu’un sélecteur CSS ?
    - sélecteur de type : balises
    - sélecteur de class
    - sélecteur d'id
    - sélecteur d'attribut : a
    - sélecteurs descendants : enfants
    - sélecteurs de pseudo-classes : a:hover
    - sélecteurs de pseudo éléments : p::first-line

24.	Quelle balise HTML permet de créer un lien hypertexte ?
    <a href="https://https://elan-formation.fr/accueil" target="_blank" rel="noopener">Elan</a>

25.	Qu’est-ce qu’une requête AJAX ?
    Asynchronus JavaScript and XML : Effectuée en arrière plan, elle envoie des requêtes afin de mettre à jour sans rechargement complet  

26.	Quel sélecteur CSS permet de sélectionner tous les éléments d’une classe spécifique ? D’un identifiant spécifique ?
    Sélecteur de class symbolisé par un .

27.	Définir le responsive design
    Permet l'adatation d'un site web à toutes les tailles de support visuel

28.	Qu’est-ce que le templating ?
    Utilisation d'un modèle de base que l'on peut personaliser

29.	Qu’est-ce qu’une fonction anonyme en Javascript ?
    - Fonction anonyme : Sans nom, associée à une variable
    - Callback : Utilisée en tant qu'argument dans d'autres fonctions (foreach)
    - Fonction fléchée : Version simplifiée de la fonction anonyme 
    - IIFE (Immediately Invoked Function Expression) : Utilisée de suite
    - Promesse : Utilisée pour des opérations asynchrones

30.	Quelle méthode JavaScript est utilisée pour ajouter un élément à la fin d'un tableau ?
    push() : fruits.push("Banane");

31.	Qu’est-ce qu’un « media query » ?
    Associé au CSS, il permet de rendre le site responsive 

32.	Qu’est-ce qu’un pseudo élément en CSS ?
    Cela permet de donner un style a une partie d'un élément sans rajouter un élément dans le DOM (Document Object Model)

33.	Qu’est-ce que Bootstrap ? Donner d’autres exemples équivalent
    C'est un framework CSS permettant de faire un site rapidement grâce à des templates, styles et plugins tout fait
    Autres : Tailwind CSS

34.	Quand un formulaire HTML est créé, quelles sont les 2 méthodes qui peuvent lui être associées ? Donner la différence entre ces 2 méthodes
    $_GET : Requête d'url simples et visibles dans l'url (application de filtre)
    $_POST : Requpete volumineuse et sensible invisibles dans l'url (envoi de formulaire)

## UX UI
35.	Quelle est la différence entre UX Design et UI Design ?
    UX (User XP) : Rend l'interaction fluide
    UI (User Interface) : Rend la présentation visuelle harmonieuse

36.	Qu’est-ce qu’un wireframe ? 
    Prototype avec structure de base (généralement non interactif) d'un site web 

37.	Qu’est-ce qu’un prototype ? 
    Prototype interactif du site web

38.	Qu’est-ce que la hiérarchie visuelle en UI Design ?
    Elle permet de créer des interfaces intuitives et efficace garantissant le fluidité de la navigation
    (taille/échelle, contrastes, couleur, espacement/alignement, typos, position des éléments, images/icones )

39.	Qu’est-ce que l’accessibilité en UX Design ? 
    Permet de rendre accessible un site internet aux personnes ayant un handicap
    (vision, audition, motricité) -> (texte alt, contrastes de couleur, navigation au clavier, 
    taille/espacement cliquable assez grands, compatibilé avec lecteur d'écran)

40.	Qu’est-ce qu’une grille de mise en page ?
    flexbox/grid : permet l'agencement d'élément de page plus facilement et plus responsive

41.	Qu’est-ce que la notion d’affordance en UX Design ?
    Cela permet au user de comprendre rapidement comment utiliser l'interface 
    (ex : si un élément ressemble à un bouton, le user aura envie de cliquer dessus)

42.	Qu’est-ce qu’un « mobile first design » ?
    Depuis peu, on s'est rendu compte que les sites était prioritairement vu sur smartphone plutôt que sur pc.
    Donc il important de mettre en prod un site en version smartphone puis en version pc  

## Programmation orientée objet (POO)
43.	Donner une définition de la programmation orientée objet 
    C'est un paradigme qui facilite l'organisation et la gestion du code en utilisant des objets qui représentent des entités
    du monde réel permettant une approche modulaire et réutilisable du dév logiciel.
    (classe, objet, encapsulation, héritage, polymorphisme)

44.	Qu’est-ce qu’une classe ? Comment la déclare-t-on ?
    Elle permet d'organiser le code en regroupant des données, donc de créer plusieurs objets à partir d'une classe,
    et a modéliser le monde réel

    ex : class Car {
        public $_brand_; //attribut
        public $_color_;
    }

45.	Qu’est-ce qu’un objet ?
    C'est l'instance d'une classe. 
    C'est elle qui va modéliser le monde réel, stocker les infos et exécuter des actions.
     
    ex : $myCar = new Car(); //Instanciation de la classe

    $myCar->_brand_ = "Toyota"; //assignation de la valeur à l'attribut
    $myCar->_color_ = "rouge";

46.	Définir la notion de propriété / attribut / méthode
    Propriété : Evoque les mécanismes d'accès permettant une meilleure manip des données

    Attribut : Var qui appartient à une classe/objet représentant les carac spécifiques de l'objet

    Méthode : Sa mise en place est similaire à une fonction. On lui donne des fonctionnalités et ensuite on l'appelle

47.	Qu’est-ce que la visibilité d’une propriété ou d’une méthode ? Citer les différents types de visibilité
    Permet d'encapsuler les données et à protéger l'intégrité de l'objet.

    Public : Accessible de partout
    Private : Accessible uniquement à l'intérieur de la classe
    Protected : Accessible à l'intérieur de la classe et des sous classes (child)

48.	Quelle est la méthode spécifique utilisée pour créer un nouvel objet à partir d’une classe ?
    new() ex : $myCar = new Car();

49.	Qu’est-ce que l’encapsulation ?
    Regroupe les propriétés et les méthodes d'un objet tout en restreignant l'accès aus données internes

    //ex : à faire quand j'aurais pratiquer car la façon de faire m'est floue

50.	Que signifie « étendre une classe » ? Quelle est le concept clé mis en œuvre ? Donner un exemple
    Création d'une nouvelle classe (enfant/sous classe) qui hérité des propriétés et des méthodes de son parent
    Concept clé : l'héritage

    //Concept et suivant à revoir
    ex : class ElectricCar extends Car {
    private $_batteryCapacity_;
    }

51.	Définir l’opérateur de résolution de portée
    Permet d'accèder aux propriétés et méthodes statique ainsi qu'aux constantes de classe

52.	Définir une méthode / propriété statique
    Méthode : 
53.	Définir le polymorphisme en POO
54.	Définir une méthode / classe abstraite ?
55.	Définir le chaînage de méthodes
56.	Qu’est-ce que la méthode __toString() ? Existe-t-il d’autres méthodes « magiques »
57.	Qu’est-ce qu’un « autoload » ?
58.	Comment appelle-t-on en français les « getters » et les « setters » ?
59.	Qu’est-ce que la sérialisation en PHP ? 

## Architecture 
60.	Qu’est-ce que l’architecture client / serveur ? Grâce à quel type de requête peut-on interroger le serveur. Définir l’acronyme de ce type de requête. Si on ajoute un « S » à cet acronyme, expliquer la différence
61.	Donner la définition d’un design pattern. Citer au moins 3 exemples de design pattern
62.	Qu’est-ce que l’architecture MVC ?
    Permet de séparer la logique d'une application en 3 blocs

63.	Quel est le rôle de chaque couche du design pattern MVC : Model, View, Controller ?
64.	Quels sont les avantages de l’architecture MVC ?
65.	Existe-t-il des variantes à l’architecture MVC ?
66.	Qu’est-ce qu’une API ? Définir l’architecture REST

## Modélisation - Base de données
67.	Qu’est-ce que la modélisation de données ? Définir la méthode Merise
68.	Quelles sont les 3 étapes principales de la méthode Merise ? 
a.	Analyse, conception et réalisation
b.	Planification, exécution et contrôle
c.	Création, modification et suppression
69.	Qu’est-ce qu’un modèle conceptuel de données (MCD) en Merise ?
70.	Qu’est-ce qu’un modèle logique de données (MLD) en Merise ?
71.	Donner la définition des mots suivants :
a.	Entité
b.	Relation
c.	Cardinalité
d.	Clé primaire / clé étrangère
72.	Que devient une relation de type « Many To Many » dans le modèle logique de données ?
73.	Qu’est-ce qu’une base de données ?
74.	Définir les notions suivantes : 
a.	SQL
b.	MySQL
c.	SGBD (donner 2 exemples de SGBD)
75.	Dans une base de données, les données sont stockées dans des ___. Celles-ci sont constituées de lignes appelées ___ et de colonnes appelées ___
76.	Quelle est la différence entre une base de données relationnelle et non relationnelle ?
77.	Qu’est-ce qu’une jointure dans une base de données ? En existe-t-il plusieurs ? Si oui lesquelles ?
78.	A quoi sert une vue dans une base de données ?
79.	Qu’est-ce que l’intégrité référentielle dans une base de données ?
80.	Quelles sont les fonctions d’agrégation en SQL ?
81.	Qu’est-ce qu’un CRUD dans le contexte d’une base de données ?
82.	Quelles sont les clauses qui permettent de :
a.	Insérer un nouvel enregistrement dans une table
b.	Modifier un enregistrement dans une table
c.	Supprimer un enregistrement dans une table
d.	Supprimer la base de données
e.	Filtrer les résultats d’une requête SQL
f.	Trier les résultats d’une requête SELECT
g.	Regrouper les résultats d'une requête SELECT en fonction d'une colonne spécifique
h.	Concaténer 2 chaînes de caractères 
83.	Comment se connecter à une base de données en PHP ? Quelle est la classe native utilisée ?

## Symfony
84.	Qu’est-ce que Symfony ?
    C'est un framework PHP open-source qui permet de simplifier le code grâce à ses diverses 
    bibliothéque.

85.	Sur quel langage de programmation et design pattern repose Symfony ? 
    Langage de programmation : PHP
    Design Pattern : 
        - MVC (Modèle Vue Contrôleur) : Gestion des données - Affichage des datas et ui grâce aux templates
                                        Traitement des requêtes / interaction avec le modèle / Renvoi de la vue
        - Dependancy Injection : permet de réduire les dépendances directes et améliore la testabilité et
                                flexibilité du code
        - Front controller : 1 seul point d'entrée pour toutes les requête
        - Observer : Utilisation d'events et un système d'écoute pour permettre à des parties du code de réagir à descendants
                     parties du code de réagir à des actions sans être appelées
        Factory : Permet de créer des objets complexes (form - services) pour centraliser leurs instanciation et de simplifier 
                  le code    
        Sigleton : services ou composants instanciés une seule fois pour économiser mémoire et ressources


86.	Quelle est la dernière version en date de Symfony ?
    Version 7.1

87.	Qu’est-ce qu’un bundle ? 
    Pack de fonctionnalités ou de composants regroupés permettant de modulariser et de réutiliser du code dans une autre app.
    (like plugins ou extensions)

88.	Quel est le moteur de template utilisé par défaut dans Symfony ?
    Twig : rapide sécurisé et flexible 

89.	Qu’est-ce qu’un ORM ? Quel est son utilité et comment s’appelle-t-il au sein de Symfony ?
    Object Relational Mapping : 
        Outil qui facilite l'interaction entre une application oreientée objet et une BDD Relationnelle.
        Plutôt qu'une requête SQL, l'ORM manipule les objets directement sous forme d'objets en effectuant la traduction entre 
        objets et les tables de la BDD.

90.	Qu’est-ce que l’injection de dépendances ? Quel est l’outil utilisé dans ce contexte et quel fichier contient l’intégralité des dépendances du projet ?
    C'est un design pattern qui permet de gérer les dépendances entre les objets dans une app. (composer.json)

91.	Que permet le bundle Maker au sein de Symfony ? 
    Il permet de simplifier la création de code et offre une série de commande CLI (interface de ligne de commande) qui automatise la génération de différents
    types de classes et de fichiers, réduisant le besoin de codage manuel pour les tâches courantes

92.	Quel est le langage de requêtage exploité au sein d’un projet Symfony ?
    DQL : Doctrine Query Language 
    Langage orienté objet utilisé pour interagir avec la BDD via Doctrine (ORM de Symphony) et permet de formuler des requêtes de manière similaire à SQL mais 
    en utilisant des entités plutôt que des tables de BDD.

93.	Quel est le composant qui garantit l’authentification et l’autorisation des utilisateurs ?
    Security component : authentification - autorisation - Protection c/ attaques courantes - intégration avec d'autres composants

## Sécurité
94.	Qu’est-ce que l’injection SQL ? Comment s’en prémunir ?
95.	Qu’est-ce que la faille XSS ? Comment s’en prémunir ?
96.	Qu’est-ce que la faille CSRF ? Comment s’en prémunir ?
97.	Définir l’attaque par force brute et l’attaque par dictionnaire
98.	Existe-t-il d’autres failles de sécurité ? Citer celles-ci et expliquer simplement leur comportement
99.	A quoi servent l’authentification et l’autorisation dans un contexte d’application web ?
100. Définir la notion de hachage d’un mot de passe et citer des algorithmes de hachage
101. Qu’est-ce qu’une politique de mots de passe forts ?
102. Qu’est-ce que l’hameçonnage ?
103. Définir la « validation des entrées »

## RGPD
104. Qu’est-ce que le RGPD ?
     Réglement Général sur la Protection des Données 

105. Quel est son objectif principal ?
    De protéger les données des citoyens en encadrant la collecte, le traitement et la sécurisation 
    des données.

106. Quelle est la date d’entrée en vigueur du RGPD ?
    25/05/2018 à l'initiative de la France

107. Quelles sont les sanctions possibles en cas de non-respect du RGPD ?
    Sanctions administratives : amendes pour violation mineures
    Sanctions pénales : jusqu'à des peines de prisons pour les dirigeants d'entreprises

108. En France, quel est l’autorité administrative qui s’occupe de faire appliquer le RGPD ?
    CNIL : Commission Nationale de l'Informatique et des Libertés

109. Quel est le consentement valide selon le RPGD ?
    Il doit être :
        - Libre : consentement donné sans pression ni coercition            
        - Eclairé : L'individu doit être informé clairement
        - Spécifique : Pour un type précis de données
        - Univoque : Acte de l'individu qu'il est consentant (ex : cocher une case)
        - Facile à retirer : L'individu doit pouvoir retirer son consentement

110. Qu’est-ce qu’une politique de confidentialité ?
      Document qui explique comment une organisation collecte, utilise, stocke et protége les données 
      personnelles de ses clients/users.
        
111. Quelle est la durée de conservation maximale des données personnelles selon le RGPD ?
    2 ans

112. Quels sont les droits des utilisateurs selon le RGPD ?
    Droits : Accès - Rectification - Effacement - Limitation du traitement - Portabilité des données - D'opposition - De ne pas faire l'objet d'une décision automatisée (ex: profilage)

113. Qu’est-ce que le principe de minimisation des données selon le RGPD ?
    Les entreprises ne doivent collecter et traiter les données nécessaires et pertinentes pour atteindre
    des objectifs spécifiques (exs : newsletters - fournir un service/produit - gestion de la relation client).


## SEO
114. Qu’est-ce que le SEO ? 
    Search Engine optimization

115. Quel est l’objectif principal du SEO ?
    D'effectuer un classement des sites internet

116. Existe-t-il plusieurs types de référencement ? Lesquels ?
    - Naturel (SEO) : mots clés - ux, contenu - balises
    - Payant (SEAdvertising) mots clés payant - pubs
    - Référencement social (SMO : Social Media Optimization) : création de contenu sur rzo sociaux
    - Référencement local : SEO local 
    - Référencement mocile (MSEO) : vitesse de chargement - réactivité - ergonomie

117. Qu’est-ce que la densité de mots-clés en SEO ?
        Cela désigne le pourcentage d'un mot ou d'une phrase clé par rapport au contenu. Permet d'évaluer la 
    fréquence à laquelle un mot clé apparait dans un texte.

118. Qu’est-ce qu’une balise « alt » ?
        Balise HTML qui permet d'indiquer la description d'une image afin d'être lue par un lecteur d'écran.

119. Qu’est-ce que la balise « meta description » ?
    Balise HTML qui fournit un résumé concis du contenu d'une page web, généralement affiché sous le titre
    de la page dans les résultats des moteurs de recherche.

120. Qu’est-ce que le « nofollow » en SEO ?
    Attribut HTML que l'on peut ajouter à un lien pour indiquer aux moteurs de recherche de ne pas suivre ce lien.
    (prévention c/ contenu payant - spams)

121. Quelle est l'importance du contenu de qualité pour le référencement d'un site web ?
        - Amélioration du classement dans les moteurs de recherches
        - Renforce l'autorité et la crédibilité du site

122. Pourquoi est-il important d'utiliser des balises de titre (h1, h2, h3, etc.) de manière structurée ?
        - Amélioration de la lisibilité
        - Indexation et SEO
        - Amélioration de l'accessibilité

123. Quelle est la recommandation pour les URL d'un site web bien référencé ?
        - Use URL courtes et descriptives
        - Mots clés pertinents
        - Séparer les mots par des tirets/underscores
        - Eviter caractères spéciaux
        - Use une hiérarchir logique
        - Eviter les paramètres inutiles

124. Qu'est-ce que le maillage interne et pourquoi est-il important pour le référencement ?
    Permet de lier les pages au sein d'un même site web.

125. Qu'est-ce que l'optimisation des images pour le référencement ?
    Permet de rendre les éléments visuels plus performants dans les résultats de recherche.
    Alt - nomFichierPertinent - compression des images - dimensions adaptées - formats appropriés

126. Qu'est-ce qu'un plan de site (sitemap) et pourquoi est-il important pour le référencement ?
        C'est un fichier qui liste toutes les pages d'un site web que les moteurs de recherche 
        peuvent explorer (XML ou HTML)

        - Améliorer l'Indexation : même celle difficile d'accès via les liens internes
        - Priorisation des pages : Influence la fréquence de visite
        - Gestion des erreurs : ex : pages cassées ou redirections
        - Amélioration de l'ux : Fournit une liste claires des pages dispo du site au user


## Gestion de projets - DevOps
127. Qu’est-ce que la gestion de projet ?	
    Processus qui consiste à planifier, organiser, exécuter et contrôler des ressources (hum, fin, matos, etc)
    Différentes phases :
        - Initiation : identif besoins et objectifs - faisabilité du projet
        - Planification : Calendrier
        - Exécution : Coordination des parties prenantes
        - Controle et suivi : Gestion des changements et des imprévus + ajustements
        - Clôture : Evaluation des résultats

128. Qu’est-ce qu’une méthode Agile de gestion de projet ? 
    La méthode Agile permet d'améliorer la flexibilité, la collaboration et la réactivité dans la gestion de projet

129. Expliquer la méthode MoSCoW en quelques lignes et citer ses avantages
    Permet de gérer les priorités et les attentes dans un projet en se concentrant sur l'essentiel.
        - Must Have (doit avoir) : Exigences critiques et essentielles qui doivent être satisfaites
        - Should have (devrait avoir) : Exigences importantes qui ajoutent de la valeur au projet
        - Could have (pourrait avoir) : Exigences souhaitables mais non essentielles
        - Won't have this time (n'aura pas cette fois-ci) : Exigences non prises en compte dans le projet actuel
        
130. A quoi sert la méthodologie MVP ? Citer les caractéristiques clés
131. Qu’est-ce que la planification itérative ?
132. Citer 3 méthodes Agiles dans le cadre d’un projet informatique
133. Qu’est-ce qu’une réunion de revue de projet ?
134. Qu’est-ce qu’un livrable dans un projet ? 
135. Quels sont les 3 piliers SCRUM ? Définir chacun d’entre eux
136. Qu’est-ce que le DevOps et quel est son objectif principal ?
137. Qu’est-ce que l’intégration continue ? 
138. Qu’est-ce que Docker ? Et en quoi est-il utile dans le cadre du DevOps ?
139. Qu’est-ce qu’un test unitaire ? 
140. Quelle est l'unité de code testée lors d'un test unitaire ?
141. Quelles sont les caractéristiques d'un bon test unitaire ?
142. Qu'est-ce qu'une assertion dans un test unitaire ?
 
## English
1)	What does JavaScript enable you to do on a website ?
a.	Add interactive behavior and dynamic content
b.	Define the layout and design of web pages
c.	Handle server-side operations
2)	Which programming language is primarily used for server-side web development ?
a.	PHP
b.	JavaScript
c.	HTML
3)	What is the purpose of a web browser ?
a.	To render and display web pages
b.	To execute serve-side code
c.	To manage databases
4)	What is the difference between GET and POST methods in HTTP ?
a.	GET retrieves data from a server, while POST submits data to a server
b.	GET submits data to a server, while POST retrieves data from a server
c.	GET and POST methods are interchangeable
5)	What is the purpose of version control systems (e.g., Git) in web development ?
a.	To track changes and manage collaborative development
b.	To optimize website loading speed
c.	To handle server-side scripting
6)	What is the purpose of a framework in web development ?
a.	To provide a structured environment for building web applications
b.	To handle network protocols and data transfer
c.	To create visual designs and layouts for websites
7)	What does NoSQL stand for ?
a.	Not Only SQL
b.	Non-Structured Query Language
c.	New Object-Oriented Language
8)	Which of the following is a characteristic of NoSQL databases ?
a.	Strict schema enforcement
b.	Support for complex transactions
c.	Scalability and flexible data models