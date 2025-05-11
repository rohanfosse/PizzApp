# Projet : **Pizz’App** – Suivi de commandes en ligne pour une pizzeria

## Contexte

Vous développez une application web pour une pizzeria artisanale. L’objectif est de permettre aux clients de :

* s’inscrire,
* commander une pizza parmi une liste fixe,
* consulter le statut de leurs commandes.

Le gérant de la pizzeria, via une interface dédiée, pourra :

* consulter les commandes en cours,
* modifier leur statut (préparation, prête, livrée).

---

## Objectifs pédagogiques

Ce projet a pour but de vous faire pratiquer :

* la conception d’une API REST sécurisée avec Node.js, Express et MongoDB,
* l’authentification par JWT avec gestion des rôles,
* la création d’une interface utilisateur moderne, responsive et mobile-first avec React et Next.js,
* la gestion des sessions et redirections côté client,
* la communication front-end / back-end via Axios,
* la conteneurisation complète de l’application avec Docker.

---

## Fonctionnalités attendues

### Côté client

* Inscription et connexion sécurisées
* Affichage des pizzas proposées
* Création d’une commande
* Suivi de l’état de ses commandes

### Côté pizzeria (administrateur)

* Connexion à une interface dédiée
* Visualisation de toutes les commandes
* Mise à jour du statut des commandes

---

## Contraintes techniques

### Back-end (API REST sécurisée)

Technologies à utiliser :

* Node.js avec Express.js
* MongoDB via Mongoose
* Authentification avec JSON Web Tokens (JWT)
* Middleware de protection des routes et gestion des rôles
* Gestion centralisée des erreurs
* Activation du CORS
* Dockerisation du serveur via Dockerfile et docker-compose

### Front-end (interface responsive)

Technologies à utiliser :

* React.js avec Next.js
* Tailwind CSS pour la mise en forme responsive
* Axios pour les appels à l’API
* Stockage et gestion du JWT (localStorage ou cookies)
* Routage avec Next.js (et éventuellement React Router pour certaines pages client)
* Conception mobile-first
* Redirection automatique selon l’état de session et le rôle
* Affichage clair des erreurs côté interface

---

## Structure de données minimale

* `User` : email, mot de passe (hashé), rôle (`client` ou `admin`)
* `Pizza` : nom, description, prix
* `Order` : utilisateur, pizza commandée, statut (`en attente`, `préparation`, `prête`, `livrée`), date

---

## Organisation du projet

```
pizzapp/
├── backend/
│   ├── models/ (User.js, Pizza.js, Order.js)
│   ├── routes/ (auth.js, orders.js)
│   ├── middleware/ (auth.js, errorHandler.js)
│   └── server.js
├── frontend/
│   ├── pages/ (index.js, login.js, register.js, dashboard.js, admin.js)
│   ├── components/ (PizzaList.js, OrderStatus.js, Navbar.js, etc.)
│   └── styles/ (configurations Tailwind)
├── docker-compose.yml
└── README.md
```

---

## Étapes de réalisation conseillées

### Étape 1 – Initialisation du projet

* Créez les dossiers `backend/` et `frontend/`.
* Installez les dépendances de base pour chaque partie (`express`, `mongoose`, `jsonwebtoken`, `next`, `react`, `tailwindcss`, etc.).
* Configurez `docker-compose.yml` pour faire tourner MongoDB, l’API et le front ensemble.

### Étape 2 – Mise en place du back-end

* Configurez Express et connectez MongoDB.
* Créez les modèles `User`, `Pizza`, `Order` avec Mongoose.
* Développez les routes d’authentification (`/api/auth/register`, `/api/auth/login`) avec gestion des tokens JWT.
* Protégez les routes privées avec un middleware d’authentification.
* Implémentez les routes pour :

  * récupérer la liste des pizzas,
  * créer une commande,
  * récupérer les commandes de l’utilisateur connecté,
  * pour l’admin : lister toutes les commandes et mettre à jour leur statut.
* Gérez les erreurs de manière centralisée (middleware `errorHandler`).

### Étape 3 – Construction du front-end

* Initialisez un projet Next.js avec Tailwind CSS.
* Créez les pages suivantes :

  * `register.js` et `login.js` pour l’authentification,
  * `dashboard.js` pour les clients (affichage des pizzas, création et suivi de commandes),
  * `admin.js` pour les administrateurs (liste et gestion des commandes).
* Créez les composants nécessaires : `PizzaList`, `OrderStatus`, `Navbar`, etc.
* Connectez le front à l’API avec Axios pour chaque fonctionnalité.

### Étape 4 – Authentification et session

* Stockez le JWT côté client (localStorage ou cookie).
* Ajoutez des protections sur les pages :

  * redirection vers la page de connexion si l’utilisateur n’est pas authentifié,
  * redirection vers le tableau de bord approprié selon le rôle.
* Gérez la déconnexion et la vérification de l’expiration du token.

### Étape 5 – Design et responsivité

* Utilisez Tailwind pour construire une interface simple, claire et responsive.
* Adoptez une approche mobile-first : testez sur mobile en priorité.
* Affichez des messages d’erreurs explicites côté interface en cas de problème (erreur API, formulaire invalide, etc.).

### Étape 6 – Conteneurisation

* Créez un `Dockerfile` pour le backend.
* Assurez-vous que `docker-compose.yml` permet de lancer MongoDB, le serveur Node, et le front-end Next.js avec une seule commande.
* Documentez dans un `README.md` comment lancer le projet.

Bon courage ! :)
