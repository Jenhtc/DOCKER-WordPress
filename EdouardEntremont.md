Instalaton et utilisation de Docker
Ce tuto se base sur une version simple de Debian avec cpu intel 64 bits.
Dans un 1er temps 2/3 sites à garder sous la main :

    Docker Hub (Registre officiel)
    Docker Doc (Site officiel doc etc)
    Très bon tuto (en 3 parties pleins de détails pour les plus fous)

Instalation de Docker
Dans le terminal :
(Mise à jour/Ajout de la source Docker/Installation)

    sudo apt-get update && sudo apt-get upgrade
    sudo apt-get install apt-transport-https ca-certificates curl software-properties-common
    curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
    sudo apt-key fingerprint 0EBFCD88
    Pour Debian
        sudo add-apt-repository \ "deb [arch=amd64] https://download.docker.com/linux/debian \ $(lsb_release -cs) \ stable"
    Pour Ubuntu
        sudo add-apt-repository \ "deb [arch=amd64] https://download.docker.com/linux/ubuntu \ $(lsb_release -cs) \ stable"
    sudo apt-get update
    sudo apt-get install docker-ce

Pour voir ci cela marche comme il faut :

    sudo docker run hello-world

Si tout va bien vous aurez un message avec "Hello from Docker!" puis un texte explicatif.

Utilisation de Docker
Toujours dans le terminal, voici des commandes utiles (il est possible de devoir mettre un sudo avant la commande).

    Pour avoir la liste des commandes :
        docker
    Pour voir la liste des images :
        docker image ls
    Pour voir la liste des tous les containers :
        docker container ls --all
    Pour chercher une image sur hub.docker.com :
        docker search <nom d'un logiciel>
    Pour charger une image :
        docker pull <nom de l'image>
    Pour créer un container avec l'image :
        docker run --name <nom du container> <nom de l'image>
    Pour stoper un container :
        docker stop <nom du container>
    Pour lancer un container :
        docker start <nom du container>
    Pour se rendre dans le terminal du container :
        docker attach <nom du container>
    Pour en sortir sans stoper le porcess :
        CRTL + P puis CTRL + Q (CTRL + C stop le process)

