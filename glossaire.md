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
    VS code et Laragon / XAMP

2.	Qu’est-ce qu’un algorithme ?  
    C'est une suite d'instructions organisées (séquentiel (exécution d'instructions) et procédurale (exécution de fonctions))

3.	Qu’est-ce qu’une variable ? Par quel symbole est préfixée une variable en PHP ?
    Emplacement mémoire permettant de stocker une valeur symbolisé par le dollar $.

4.	Qu’est-ce que la portée d’une variable ?
    La portée d'une variable correspond à son champ d'action (superglobale / globale / locale)

5.	Qu’est-ce qu’une constante ? Quelle est la différence avec une variable ?
    Une constante a une valeur qui n'a pas vocation a changé contrairement à la variable qui varie.

6.	Qu’est-ce qu’une superglobale, combien en existent-ils et donner un exemple d’utilisation 

    La portée de la superglobale est externe à son script car elles sont crées automatiquement par le serveur

    $_GET : Contient les données envoyés en paramètre d'url (ex : récupérer l'id d'un article dans l'url pour l'afficher)
    $_POST : Contient les données envoyées par le biais d'un formulaire
    $_SESSION : Permet de stocker et de récupérer les données de sessions du user (ex: garder le user connecté d'une page à l'autre)
    $_COOKIE : Contient les cookies (locaux) envoyés par le navigateur du user (ex: se souvenir de sa langue préféré)
    $_ENV et $_SERVER : Fournit les infos sur le serveur et l'environnement d'exécution (ex : connaitre l'adresse ip du user)
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

    ex : class ElectricCar extends Car {
    private $_batteryCapacity_;
    }

51.	Définir l’opérateur de résolution de portée ::
    Permet d'accèder aux propriétés et méthodes statiques ainsi qu'aux constantes de classe.
    ex dans le cadre d'un héritage

52.	Définir une méthode / propriété statique
    Méthode appartenant a une classe qui peut être appelée sans créer d'objet de la classe.
    Souvent appelée avec l'opérateur de résolution de portée.

53.	Définir le polymorphisme en POO
    Avantages : Flexibilité - Extensibilité - réutilisable

    Permet a des objets de différentes classes d'être traités de manière uniforme.
        - Par héritage/dyn : Méthode redéfinie dans la classe enfant. 
          (avec extends on modifie la méthode)
        - Par interface/inclusion : Lorsque plusieurs classes implémentent une même interface et fournissent leur 
          propre version des méthodes définies. 
        - Avec classes abstraites : oblige les classes dérivées d'avoir leur propre implémentation.

54.	Définir une méthode / classe abstraite ?
    Elle permet de fournir une implémentation partielle d'un comportement commun que les classes dérivées peuvent 
    compléter ou modifier.

55.	Définir le chaînage de méthodes
    Permet d'appeler plusieurs méthodes sur un simple objet grâce au retour de return $this (objet courant).

56.	Qu’est-ce que la méthode __toString() ? Existe-t-il d’autres méthodes « magiques »
    Elle permet de défénir une représentation string de l'objet.

57.	Qu’est-ce qu’un « autoload » ?
    Permet de charger les classes ou interfaces nécessaires sans avoir besoin d'use require ou include
    spl_autoload_register(function ($className) {
    include 'classes/' . $className . '.php';
});

58.	Comment appelle-t-on en français les « getters » et les « setters » ?
    Accesseur : Méthode qui permet d'accèder à la valeur d'un attribut pv ou protégé d'une classe
    Mutateur : Méthode qui permet de modifier ou muter la valeur d'un attribut pv ou protégé d'une classe

59.	Qu’est-ce que la sérialisation en PHP ? 
    Processus qui permet de convertir une variable (objet, tabl, etc) en une string afin de 
    stocker : dans un file, bdd
    transmettre : sur un rzo, (ex api ou session)
    rétablir : plus tard la variable dans son état d'origine (désérialisation)

    $serializedData = serialize($data);

## Architecture 
60.	Qu’est-ce que l’architecture client / serveur ? 
    Modèle de communication dans lequel les rôles sont répartis entre un client qui demande des services/ressources
    et un serveur qui les fournit. client env requête au serveur qui répond en fonction des données ou traitements qu'il Gère

    Grâce à quel type de requête peut-on interroger le serveur ? Définir l’acronyme de ce type de requête. Si on ajoute un « S » à cet acronyme, expliquer la différence
    Requête HTTP (Hypertext Transfert Protocol)
    Avec S : Sécurisée (fortement recommandée pour SEO, obl pour certains sites)

61.	Donner la définition d’un design pattern. Citer au moins 3 exemples de design pattern
    Solution réutilisable à un problème courant dans le développement logiciel afin de résoudre plus facilement 
    un problème.
    Avantages : 
        - respect des méthodes de conception
        - dév + rapidement en suivant des modèles
        - permet au code d'être relu plus facilement par autrui
    ex : 
    - composite : mep hiérarchie d'objet (architecture complexe: manip arbre, branches ou feuille)
    - factory : creation familles d'objets sans préciser la classe return instance parmi plsuieurs possibles selon paramètres
    - observer : relation 1 à +sieurs objets (enregistrement d'une activité > observation log, connexion etc)
    
62.	Qu’est-ce que l’architecture MVC ?
    Permet de séparer la logique d'une application en 3 blocs (logique métier, présentation, traitements)

63.	Quel est le rôle de chaque couche du design pattern MVC : Model, View, Controller ?
    Model : Gère les données, la logique métier et l'accès à la BDD
    View : Présente les données au user sans contenir de logique métier
    Controller : Interprète les actions du user et update le modèle et la vue en conséquence

64.	Quels sont les avantages de l’architecture MVC ?
    Séparation des préoccupations : Facilité de la gestion et la maintenance du code. Chaque couche est resp d'une fonction.
    Facilité de test : Permet de tester la logique métier sans dépendre de l'ui
    Réutilisation du code
    Facilité de collab
    Scalabilité et flexibilité

65.	Existe-t-il des variantes à l’architecture MVC ?
    MVVM (Model-View-ViewModel) : Use dans appli dyn
    MVP (Model-View-Presenter) : Gére la logique de présentation
    MVU (Model-Update-View) : Flux unidirectionnel, état géré par Update.

66.	Qu’est-ce qu’une API ? Définir l’architecture REST
    Application Programming Interface : Ensemble de protocoles et d'outils qui permet à différentes appli
    de communiquer entre elles 
    Representational State Transfert : Style de conception d'api qui utilise les méthodes http pour manipuler
    les ressources identifiées par des url (CRUD > Post, Get, Put, Delete)

    Avantages : simple, standardisé, évolutif, rapide, haute performance, support de mise en cache

## Modélisation - Base de données
67.	Qu’est-ce que la modélisation de données ? Définir la méthode Merise
    La modélisation de données est une façon d’organiser et de représenter les informations 
    pour mieux les comprendre et répondre aux besoins métier.

    Merise : méthode de conception de systèmes d'information qui organise les données et les processus grâce 
    à des modèles pour assurer une bonne compréhension et une gestion efficace (ex MCD - MLD)

68.	Quelles sont les 3 étapes principales de la méthode Merise ? 
**a.Analyse, conception et réalisation**
        Analyse : étude des besoins + modélisation
        Conception : MCD -> MLD 
        Réalisation : Implémenter le modèle physique dans un environnement techniques

b.	Planification, exécution et contrôle
c.	Création, modification et suppression

69.	Qu’est-ce qu’un modèle conceptuel de données (MCD) en Merise ?
    Représention graphique des données d'un système d'information (entités - attributs - relations)

70.	Qu’est-ce qu’un modèle logique de données (MLD) en Merise ?
    Traduction du MCD en organisant les éléments sous forme de tables, colonnes (attributs), clés
    primaires et étrangères.

71.	Donner la définition des mots suivants :
a.	Entité : représente un objet qui a une existence propre possédant des attributs
b.	Relation : Associations entre plusieurs entités
c.	Cardinalité : Nb d'occurences possibles entre 2 entités en relation
d.	Clé primaire / clé étrangère : identifiant de l'entité / identifiant d'une entité étrangère

72.	Que devient une relation de type « Many To Many » dans le modèle logique de données ?
    Elle devient une table d'Associations.

73.	Qu’est-ce qu’une base de données ?
    Ensemble de données stockées.

74.	Définir les notions suivantes : 
a.	SQL (Structured Query Language) : langage de programmation pour manipuler les données de la BDD
b.	MySQL : c'est un SGBD open sourcé basé sur sql
c.	SGBD (system de Gestion de BDD) : logiciel permettant de crud une bdd
         (ex : MongoDB, Oracle, MariaDB PostGre)

75.	Dans une base de données, les données sont stockées dans des **tables**. 
    Celles-ci sont constituées de lignes appelées **enregistrement** et de colonnes appelées **attributs**.

76.	Quelle est la différence entre une base de données relationnelle et non relationnelle ?
    BDD relationnelle : Elle organise les données en tables interconnectées par des relations utilisantle langage SQL 
    pour manipuler les données structurées utilisant SQL.

    BDD non relationnelle : Elle stocke les données de manière flexible, souvent sous forme de documents,
    paires clé-valeur sans imposer de structure rigide et ne nécessite pas SQL.


77.	Qu’est-ce qu’une jointure dans une base de données ? En existe-t-il plusieurs ? Si oui lesquelles ?
    INNER JOIN : données communes a 2 tables
    LEFT JOIN : enregistrements de la table de gauche et correspondances de la table de droite
    RIGHT JOIN : enregistrements de la table de droite et correspondances de la table de gauche
    FULL JOIN : enregistrements des 2 tables avec valeur nulles pour absence de correspondances
    CROSS JOIN : combine chaque enregistrment de la 1ere table avec tous les enr de la 2e_page
    SELF JOIN : table jointe à elle-même

78.	A quoi sert une vue dans une base de données ?
    Permet de simplifier l'accès aux données, restreindre leur visibilité et personnaliser leur présentation.
    (avec CREATE VIEW)

79.	Qu’est-ce que l’intégrité référentielle dans une base de données ?
    Permet de garantir la liaison clé étrangère <-> clé primaire

80.	Quelles sont les fonctions d’agrégation en SQL ?
    SUM() - COUNT() - AVG() - MIN() - MAX() : a utiliser avec GROUP BY

81.	Qu’est-ce qu’un CRUD dans le contexte d’une base de données ?
    Create - Read - Update - Delete 

82.	Quelles sont les clauses qui permettent de :
a.	Insérer un nouvel enregistrement dans une table : **INSERT INTO**
b.	Modifier un enregistrement dans une table : **UPDATE**
c.	Supprimer un enregistrement dans une table : **DELETE**
d.	Supprimer la base de données : **DROP DATABASE**
e.	Filtrer les résultats d’une requête SQL : **WHERE**
f.	Trier les résultats d’une requête SELECT : **ORDER BY**
g.	Regrouper les résultats d'une requête SELECT en fonction d'une colonne spécifique : **GROUP BY**
h.	Concaténer 2 chaînes de caractères ; **|| '' ||**

83.	Comment se connecter à une base de données en PHP ? Quelle est la classe native utilisée ?
    /*Connexion a la BDD*/
        try 
        {
            $bdd = new PDO('mysql:host=localhost;dbname=recettelily;charset=utf8', 
            'root', 
            '',
            [PDO::ATTR_ERRMODE => PDO::ERRMODE_EXCEPTION], /*Permet d'afficher erreurs clairement*/
        );
            
        }
        catch (Exception $e)
        {
            die('Erreur : ' . $e->getMessage());
        }

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
    Code SQL malveillant afin de manip la BDD (usurpation d'identité) 
    ex : insertion de " ou ', opérateur OR

    Prévention : bonne gestion des privilèges, requêtes préparées (requêtes paramétrées)


95.	Qu’est-ce que la faille XSS ? Comment s’en prémunir ?
    XSS : Cross Site Scripting : Injection de code malveillant au sein d'un formulaire.

    Mise en place de filtres : 
        FILTER_SANITIZE_FULL_SPECIAL_CHARS -> supprime les strings
        FILTER_VALIDATE_FLOAT -> valide si float
        FILTER_FLAG_ALLOW_FRACTION -> permet "." ou "," au float
        FILTER_VALIDATE_INT : valide si int != 0

96.	Qu’est-ce que la faille CSRF ? Comment s’en prémunir ?
    CSRF : Cross Site Request Forgery : Use user pour effectuer une action sans qu'il en ait conscience
    ex : Réception de mail envoyant le user admin sur un site frauduleux (ingénierie sociale)

    Prévention : Génération d'un token unique côté serveur permettant de lier l'utilisateur au formualaire

97.	Définir l’attaque par force brute et l’attaque par dictionnaire

    Attaque par force brute : Tester chaque combinaison possible d'un mot de passe
    Attaque par dico : Hacker va essayer automiquement des mots issus du dictionnaire

    Prévention : Hashage du mot de passe par le biais du regex (expression régulière)

98.	Existe-t-il d’autres failles de sécurité ? Citer celles-ci et expliquer simplement leur comportement

Attaque Man in the Middle : interception de datas sensibles 
    - ARP poisoning : interception sur LAN 
                    Prévention : tables ARP statiques pour config adresses IP et MAC - Implémenter sytèmes d'intrusion - chiffrer les datas

    - DNS Spoofing : redirection vers sites malveillants
                    Prévention : implémentation signatures cryptographiques - Mep d'outils de détection et d'analyse rzo

    - DHCP spoofing : détournement du processus de distrib IP
                    Prévention : protection DHCP sur les switches - Segmenter le rzo avec vlan - config parefeu et ACLs (Access Control Lists)

99.	A quoi servent l’authentification et l’autorisation dans un contexte d’application web ?
    Cela permet de gérer les accès utilisateurs.

100. Définir la notion de hachage d’un mot de passe et citer des algorithmes de hachage
     Le hachage de mot de passe consiste à camoufler un mot de passe grâce a un algorithme.

     Algorithme SHA-256 va produire un « hash » (code ) de 256 bits précis
     Algorithme SHA-3 utilise des mécanisme de brouillage très avancés (2015)

101. Qu’est-ce qu’une politique de mots de passe forts ?
    Permet de rendre un mot de passe quasiment inviolable.

102. Qu’est-ce que l’hameçonnage ?
     C'est le fait d'être démarché par téléphone, sms ou mail se faisant passer bien souvent pour un organisme public (banque, impôts, caf, etc) afin de récupérer des informations sensibles
     en utilisant des techniques d'ingenierie sociale.

103. Définir la « validation des entrées »
     Le développeur doit anticiper tous les comportements d'un utilisateur afin que ce dernier utilise l'application correctement. 
     ex : n'autoriser que des string dans un nom

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
    Minimum Viable Project : Version minimum d'un projet contenant les fonctionnalités de base

    Petit - rapide - peu cher 

131. Qu’est-ce que la planification itérative ?
     Consiste à diviser un projet en cycles courts, appelés itérations, permettant des ajustements continus 
     et des améliorations basées sur les retours des utilisateurs à chaque étape.

132. Citer 3 méthodes Agiles dans le cadre d’un projet informatique
    SCRUM : sprints de travail
    KANBAN : méthode visuelle de la gestion du travail
    Extreme Programming (XP) : mise en place du développement itératif (version fonctionnelle à chaque cycle),
                             pair programming (2 dev : 1 dev - 1 pilote) et tests fréquents


133. Qu’est-ce qu’une réunion de revue de projet ?
    Réunion sur l'avancement du projet.

134. Qu’est-ce qu’un livrable dans un projet ? 
    Résultat de fin.

135. Quels sont les 3 piliers SCRUM ? Définir chacun d’entre eux
    transparence : tout les processus sont visibles.
    Inspection : Examen des progrès pour identifier les écarts ou problèmes potentiels.
    Adaptation : Ajustement des processus.

136. Qu’est-ce que le DevOps et quel est son objectif principal ?
     Approche collaborative qui combine les équipes de développement (Dev) et des opérations (Ops) pour automatiser 
     et optimiser le cycle de vie des logiciels.

     Son objectif principal est d'améliorer la qualité, la rapidité et la fiabilité des livraisons de
     logiciels en favorisant la communication, l'intégration continue, et le déploiement automatisé.

137. Qu’est-ce que l’intégration continue ? 
    Enregistrement de l'avancée du travail dans un dépôt partagé.

138. Qu’est-ce que Docker ? Et en quoi est-il utile dans le cadre du DevOps ?
    plateforme permettant de créer et exécuter des conteneurs qui garantissent la portabilité, la cohérence et 
    l'efficacité des applications à travers différents environnements.

139. Qu’est-ce qu’un test unitaire ? 
    Permet de tester de manière isolée un bout de code.

140. Quelle est l'unité de code testée lors d'un test unitaire ?
    fonction - méthode ou composant individuel

141. Quelles sont les caractéristiques d'un bon test unitaire ?
    Indépendant : autonome
    Rapide
    Prédictible : résultat constant
    Clair et précis
    Isolée : abs d'interactions avec bdd ou syst ext
    Automatisé

142. Qu'est-ce qu'une assertion dans un test unitaire ?
    Comparaison du résultat produit par une unité de code avec le résultat attendu.
    Si çca correspond l'assertion a réussi.
 
## English
1)	What does JavaScript enable you to do on a website ?
**a.	Add interactive behavior and dynamic content**
b.	Define the layout and design of web pages
c.	Handle server-side operations
2)	Which programming language is primarily used for server-side web development ?
**a.	PHP**
b.	JavaScript
c.	HTML
3)	What is the purpose of a web browser ?
**a.	To render and display web pages**
b.	To execute serve-side code
c.	To manage databases
4)	What is the difference between GET and POST methods in HTTP ?
**a.	GET retrieves data from a server, while POST submits data to a server**
b.	GET submits data to a server, while POST retrieves data from a server
c.	GET and POST methods are interchangeable
5)	What is the purpose of version control systems (e.g., Git) in web development ?
**a.	To track changes and manage collaborative development**
b.	To optimize website loading speed
c.	To handle server-side scripting
6)	What is the purpose of a framework in web development ?
**a.	To provide a structured environment for building web applications**
b.	To handle network protocols and data transfer
c.	To create visual designs and layouts for websites
7)	What does NoSQL stand for ?
a.	Not Only SQL
**b.	Non-Structured Query Language**
c.	New Object-Oriented Language
8)	Which of the following is a characteristic of NoSQL databases ?
a.	Strict schema enforcement
b.	Support for complex transactions
c.	Scalability and flexible data models