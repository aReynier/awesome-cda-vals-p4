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

## Conteneurs Docker

### Cycle de Vie
| Commande | Description | Exemple |
|----------|-------------|---------|
| `docker run <image>` | Crée et démarre un conteneur | `docker run -d -p 80:80 nginx` |
| `docker start <conteneur>` | Démarre un conteneur arrêté | `docker start mon-nginx` |
| `docker stop <conteneur>` | Arrête un conteneur | `docker stop mon-nginx` |
| `docker restart <conteneur>` | Redémarre un conteneur | `docker restart mon-nginx` |
| `docker rm <conteneur>` | Supprime un conteneur | `docker rm mon-nginx` |
| `docker system prune`| Nettoie les conteneurs inutilisés | `docker system prune`|

### Gestion et Surveillance
| Commande | Description | Exemple |
|----------|-------------|---------|
| `docker ps` | Liste les conteneurs actifs | `docker ps` |
| `docker ps -a` | Liste tous les conteneurs | `docker ps -a` |
| `docker logs <conteneur>` | Affiche les logs | `docker logs mon-nginx` |
| `docker inspect <conteneur>` | Affiche les détails | `docker inspect mon-nginx` |
| `docker stats <conteneur>` | Affiche les statistiques | `docker stats mon-nginx` |
| `docker exec -it <conteneur> <cmd>` | Exécute une commande | `docker exec -it mon-nginx bash` |

## Volumes Docker

| Commande | Description | Exemple |
|----------|-------------|---------|
| `docker volume create <nom>` | Crée un volume | `docker volume create mes-donnees` |
| `docker volume ls` | Liste les volumes | `docker volume ls` |
| `docker volume inspect <volume>` | Inspecte un volume | `docker volume inspect mes-donnees` |
| `docker volume rm <volume>` | Supprime un volume | `docker volume rm mes-donnees` |
| `docker run -v <volume>:<chemin>` | Monte un volume | `docker run -v mes-donnees:/data nginx` |
| `docker run -v <hôte>:<conteneur>` | Monte un dossier (bind) | `docker run -v $(pwd):/app node` |
