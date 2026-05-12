# Wacdo - Application RH interne (Symfony)

Application metier developpee dans le cadre du **Bloc 3 RNCP 37805**.  
Le projet permet a un administrateur RH de gerer :
- les restaurants ;
- les collaborateurs ;
- les fonctions (postes) ;
- les affectations (actives et historiques).

## Etat actuel du projet

- Squelette Symfony cree ;
- Structure de base du projet en place ;
- Prochaines etapes : configuration BDD, securite, puis modules metier.

## Prerequis

- PHP 8.2+ ;
- Composer 2+ ;
- Symfony CLI ;
- Base de donnees MySQL ;
- Git.

## Installation

1. Cloner le depot :

```bash
git clone <url-du-depot>
cd wacdo
```

2. Installer les dependances PHP :

```bash
composer install
```

3. Configurer l'environnement local :

- Creer/modifier le fichier `.env.local`
- Definir `DATABASE_URL` avec tes parametres MySQL

Exemple :

```env
DATABASE_URL="mysql://root:@127.0.0.1:3306/wacdo?serverVersion=8.0&charset=utf8mb4"
```

4. Creer la base de donnees :

```bash
php bin/console doctrine:database:create
```

5. Lancer les migrations (des qu'elles existent) :

```bash
php bin/console doctrine:migrations:migrate
```

## Lancement en local

Avec Symfony CLI :

```bash
symfony server:start
```

Ou avec le serveur PHP :

```bash
php -S 127.0.0.1:8000 -t public
```

Application accessible ensuite sur :
- [http://127.0.0.1:8000](http://127.0.0.1:8000)

## Fonctionnalites ciblees (cahier des charges)

- Authentification administrateur (`/login`, `/logout`) ;
- Dashboard RH post-connexion ;
- CRUD Restaurants avec filtres ;
- CRUD Collaborateurs avec filtres ;
- CRUD Fonctions ;
- CRUD Affectations avec distinction :
  - `date_fin = null` -> active ;
  - `date_fin renseignee` -> historique ;
- Controle d'acces strict aux routes d'administration ;
- Validation serveur + CSRF + hashage des mots de passe.

## Structure technique

- Framework : Symfony ;
- Architecture : MVC ;
- ORM : Doctrine ;
- Vues : Twig ;
- Formulaires : Symfony Form + Validator ;
- Securite : Symfony Security (session).

## Tests (a completer)

Scenarios manuels minimum prevus :
- acces protege sans connexion ;
- login valide / invalide ;
- creation entites metier ;
- cloture d'affectation et passage en historique ;
- verification filtres principaux.

Tests automatises possibles via `WebTestCase`.

## Deploiement (a completer)

Le README sera complete avec :
- URL finale de l'application ;
- procedure de deploiement ;
- compte administrateur de demonstration ;
- jeux de donnees de test.

## Auteur

Projet realise pour la certification RNCP 37805 - Bloc 3.
