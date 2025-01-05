# Utiliser une image Node.js comme base
FROM node:16

# Définir le répertoire de travail dans le conteneur
WORKDIR /usr/src/app

# Copier les fichiers package.json et package-lock.json
COPY package*.json ./

# Installer les dépendances
RUN npm install

# Copier le reste des fichiers du projet
COPY . .

# Exposer le port utilisé par l'application (8000)
EXPOSE 8000

# Commande pour démarrer l'application
CMD ["node", "server.js"]
