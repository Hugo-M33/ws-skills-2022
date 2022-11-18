# Docker

> ❌ A travailler

> ✔️ Auto validation par l'étudiant

## 🎓 J'ai compris et je peux expliquer

- la création d'une image docker ✔️
- l'éxécution d'un container ✔️
- l'orchestration de containers avec docker-compose ✔️


## 💻 J'utilise

### Un exemple personnel commenté ✔️

```yaml
version: '3.9'

services:
  database:
    image: postgres:15-alpine
    container_name: wildrent-database
    ports:
      - "5432:5432"
    environment:
      - POSTGRES_PASSWORD=root
      - POSTGRES_USER=wildrent
      - POSTGRES_DB=wildrent
    volumes:
      # creation d'un volume pour persister la donnée 
      # apres restart du container
      - ./postgres-data:/var/lib/postgresql/data

  frontend:
    working_dir: /app
    build:
      target: wildrent_frontend
      context: frontend
      dockerfile: Dockerfile
    environment:
      - EXEC_ENV=development
    volumes:
      # mapping pour synchro des fichiers entre le container et le host
      - ./frontend:/app
    ports:
      - "3000:3000"
    restart: always
    depends_on:
      # Utilisation de dépendance pour éviter les erreurs de connection
      - backend

  backend:
    working_dir: /app
    build:
      target: wildrent_backend
      context: backend
      dockerfile: Dockerfile
    environment:
      - EXEC_ENV=production
    volumes:
      - ./backend:/app
      - /app/node_modules
    ports:
      - "4000:4000"
    restart: always
    depends_on:
      - database
```

### Utilisation dans un projet ❌ / ✔️

[lien github](...)

Description :

### Utilisation en production si applicable❌ / ✔️

[lien du projet](...)

Description :

### Utilisation en environement professionnel ❌ / ✔️

Description :

## 🌐 J'utilise des ressources

### Titre

- lien
- description

## 🚧 Je franchis les obstacles

### Point de blocage ❌ / ✔️

Description:

Plan d'action : (à valider par le formateur)

- action 1 ❌ / ✔️
- action 2 ❌ / ✔️
- ...

Résolution :

## 📽️ J'en fais la démonstration

- J'ai ecrit un [tutoriel](...) ❌ / ✔️
- J'ai fait une [présentation](...) ❌ / ✔️
