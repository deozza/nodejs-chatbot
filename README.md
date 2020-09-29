# Nodejs-chatbot

Une application de démo pour le premier cours de nodejs.

## Sommaire

- [Nodejs-chatbot](#nodejs-chatbot)
  * [Sommaire](#sommaire)
  * [Prérequis](#pr-requis)
    + [Sur Unix](#sur-unix)
      - [MacOS](#macos)
      - [Ubuntu/Debian](#ubuntu-debian)
      - [Arch](#arch)
    + [Sur Windows](#sur-windows)
    + [Avec Docker](#avec-docker)
  * [Routes](#routes)

## Prérequis

Il faudra avoir d'installé sur sa machine : 
 * nodejs et npm pour interpréter l'application
 * un terminal bash pour lancer l'application
 * un client HTTP (comme Postman) pour utiliser l'application

### Sur Unix 

#### MacOS

*Installer nodejs*


 * [installer nodejs](https://nodejs.org/dist/v12.18.4/node-v12.18.4.pkg)

*Terminal*

 * utiliser le terminal intégré à MacOS
  * utiliser le finder

*Client HTTP*

 * [installer postman](https://dl.pstmn.io/download/latest/osx)

#### Ubuntu/Debian

*Installer nodejs*

```bash
sudo apt-get install nodejs npm
```

*Terminal*

 * utiliser le terminal gnome intégré

`ctrl+alt+t`

*Client HTTP*

```bash
sudo snap install postman
```

#### Arch

*Installer nodejs*

```bash
sudo pacman nodejs -S
```

*Terminal*

 * utiliser le terminal intégré

`ctrl+alt+t`

*Client HTTP*

```bash
sudo pacman postman -S
```

### Sur Windows

*Installer nodejs*

 * [installer postman](https://nodejs.org/dist/v12.18.4/node-v12.18.4-x86.msi)

*Terminal*

 * [installer CMDER](https://github.com/cmderdev/cmder/releases/download/v1.3.16/cmder_mini.zip)

*Client HTTP*

 * [installer Postman](https://dl.pstmn.io/download/latest/win64)

### Avec Docker

*Lancer l'application dans un container*

```bash
# allumer le container
docker-compose up -d --build

# allumer l'application
docker-compose exec nodejs_chatbot_cours node index.js 
```

## Routes

L'application est disponible à l'adresse `127.0.0.1:3000` .

`GET` /

*Description*

Renvoi un message d'accueil quand on arrive sur le serveur.

*Exemple de retour*

`'Bonjour !'`

`GET` /hello?{nom}

*Description*

Renvoi un message d'accueil personnalisé en fonction du nom entré en paramètre.

*Paramètres URL*

| Paramètre | Obligatoire | Type     | Exemple |
|-----------|-------------|----------|---------|
| nom       | `oui`       | `string` | toto    |

*Exemple de requête*

`127.0.0.1:3000/hello?name=toto`

*Exemple de retour*

`'Bonjour, toto !'`

`POST` /chat

*Description*

Renvoi un message personnalisé en fonction du contenu de la requête json.

*Paramètres*

| Paramètre | Obligatoire | Type     | Valeurs attendues |
|-----------|-------------|----------|-------------------|
| msg       | `oui`       | `string` | `météo` / `ville` |

*Exemple de requête*

```curl
curl --location --request POST '127.0.0.1:3000/chat' \
--header 'Content-Type: application/json' \
--data-raw '{
    "msg": "ville"
}'
```

*Exemple de retour*

```
 "Nous sommes à Paris"
```
