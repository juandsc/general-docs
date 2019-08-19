# Instalación

Información tomada de [Docker-Install](https://docs.docker.com/install/linux/docker-ce/debian/)

En la documentación oficial se soportan la plataformas CentOS, Debian, Fedora y Ubuntu. Si se tiene instalado una distribución deribada de alguna de estas se debe seguir las instrucciones correspondientes. En este caso se realiza sobre MX Linux.

1. Actualizar repositorios:

        sudo apt update

2. Instalar los paquetes necesarios para permitir que `apt` use repositorios a traves de HTTPS:

        sudo apt install apt-transport-https ca-certificates curl gnupg2 software-properties-common

3. Añadir la llave oficial:

        curl -fsSL https://download.docker.com/linux/debian/gpg | sudo apt-key add -

4. Verificar que el fingerprinting de la llave sea la siguiente:

        9DC8 5822 9FC7 DD38 854A E2D8 8D81 803C 0EBF CD88

    con el siguiente comando:

        sudo apt-key fingerprint 0EBFCD88

5. Verificar la distribución base del sistema operativo actual:

        hostnamectl

    aparecera algo como esto:

            Static hostname: pitmmam-laptop
                  Icon name: computer-laptop
                    Chassis: laptop
                    Boot ID: ea65a0f2bad8424bb2bc4549661e89e7
           Operating System: Debian GNU/Linux 9 (stretch)
                     Kernel: Linux 4.19.0-5-amd64

    en este caso se identifica que es Debian stretch.

6. Configurar el repositorio estable. En MX Linux no existe el archivo `/etc/apt/sources.list`, por eso este paso se diferencia de la documentación oficial:

        echo 'deb [arch=amd64] https://download.docker.com/linux/debian stretch stable' | sudo tee --append /etc/apt/sources.list.d/docker.list

7. Actualizar los repositorios

        sudo apt update

8. Instalar Docker:

        sudo apt install docker-ce docker-ce-cli containerd.io

9. Añadir el usuario de trabajo al grupo de docker para que no pida permisos en cada ejecucion de algun comando:

        sudo usermod -aG docker $(whoami)

   Se debe reiniciar sesión para que tenga efecto.

10. Instalar Docker Compose. Descargar y guardar la versión estable:

        sudo curl -L "https://github.com/docker/compose/releases/download/1.24.1/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose

11. Añadir los permisos al binario:

        sudo chmod +x /usr/local/bin/docker-compose

12. Testear la versión instalada:

        docker-compose --version
