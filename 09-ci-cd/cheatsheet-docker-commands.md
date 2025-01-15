# Docker Cheatsheet

## Images Docker

| Commande | Description | Exemple |
|----------|-------------|---------|
| `docker images` | Liste toutes les images Docker | `docker images` |
| `docker pull <image>` | Télécharge une image depuis Docker Hub | `docker pull nginx:latest` |
| `docker rmi <image>` | Supprime une image | `docker rmi nginx` |
| `docker build -t <nom>:<tag>` | Construit une image à partir d'un Dockerfile | `docker build -t mon-app:1.0 .` |
| `docker tag <image> <nouveau_nom>:<tag>` | Crée un nouveau tag pour une image | `docker tag mon-app:1.0 user/mon-app:latest` |
| `docker push <image>` | Pousse une image vers un registre | `docker push user/mon-app:latest` |
