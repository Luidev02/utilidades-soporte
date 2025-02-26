### Comandos Básicos para Ubuntu Server 22.04

#### 1. **Gestión de Paquetes**
```sh
sudo apt update && sudo apt upgrade -y  # Actualizar paquetes
sudo apt install <paquete>              # Instalar un paquete
sudo apt remove <paquete>               # Eliminar un paquete
sudo apt autoremove                     # Eliminar paquetes innecesarios
sudo apt clean                          # Limpiar caché de paquetes
```

#### 2. **Gestión de Usuarios y Permisos**
```sh
sudo adduser <usuario>                  # Crear un nuevo usuario
sudo passwd <usuario>                    # Cambiar contraseña de un usuario
sudo deluser <usuario>                   # Eliminar un usuario
sudo usermod -aG sudo <usuario>          # Agregar usuario al grupo sudo
sudo chmod 777 <archivo/carpeta>         # Cambiar permisos (777: todos los permisos)
sudo chown <usuario>:<grupo> <archivo>   # Cambiar propietario de un archivo o carpeta
```

#### 3. **Gestión de Servicios**
```sh
sudo systemctl start <servicio>          # Iniciar un servicio
sudo systemctl stop <servicio>           # Detener un servicio
sudo systemctl restart <servicio>        # Reiniciar un servicio
sudo systemctl status <servicio>         # Ver estado de un servicio
sudo systemctl enable <servicio>         # Habilitar inicio automático
sudo systemctl disable <servicio>        # Deshabilitar inicio automático
```

#### 4. **Gestión de Red**
```sh
ip a                                    # Ver direcciones IP
ip r                                    # Ver rutas de red
sudo systemctl restart networking       # Reiniciar servicio de red
ping <dominio o IP>                     # Comprobar conectividad
```

#### 5. **Gestión de Firewall (ufw)**
```sh
sudo lsof -i -P -n                      # Saber los puertos activos
sudo ufw status                         # Ver estado del firewall
sudo ufw enable                         # Activar firewall
sudo ufw disable                        # Desactivar firewall
sudo ufw allow <puerto>/<protocolo>     # Permitir tráfico en un puerto (Ej: sudo ufw allow 80/tcp)
sudo ufw deny <puerto>/<protocolo>      # Bloquear tráfico en un puerto
sudo ufw reload                         # Aplicar cambios en el firewall
```

#### 6. **Gestión de Procesos**
```sh
top                                      # Monitorizar procesos en tiempo real
htop                                     # Alternativa más visual (requiere instalación: sudo apt install htop)
ps aux | grep <proceso>                  # Buscar un proceso específico
kill <PID>                               # Terminar un proceso por su ID
kill -9 <PID>                            # Forzar la terminación de un proceso
```

#### 7. **Gestión del Sistema**
```sh
sudo reboot                              # Reiniciar el sistema
sudo shutdown -h now                     # Apagar el sistema inmediatamente
sudo shutdown -r now                     # Reiniciar el sistema inmediatamente
sudo hostnamectl set-hostname <nombre>   # Cambiar el hostname del sistema
free -h                                  # Ver uso de memoria RAM
df -h                                    # Ver uso del disco
du -sh <directorio>                      # Ver tamaño de un directorio específico
```

#### 8. **Gestión de Archivos y Directorios**
```sh
ls -lah                                  # Listar archivos con detalles
cd <directorio>                          # Navegar entre directorios
mkdir <directorio>                       # Crear un directorio
rm -r <directorio/archivo>               # Eliminar archivos o carpetas
cp -r <origen> <destino>                 # Copiar archivos o carpetas
mv <origen> <destino>                    # Mover o renombrar archivos y carpetas
tar -czvf archivo.tar.gz <directorio>    # Comprimir un directorio en formato .tar.gz
tar -xzvf archivo.tar.gz                 # Extraer un archivo .tar.gz
```

#### 9. **Gestión de Docker (Si está instalado)**
```sh
sudo systemctl start docker              # Iniciar Docker
sudo systemctl enable docker             # Habilitar inicio automático de Docker
docker ps -a                             # Ver contenedores
sudo docker stop <contenedor>            # Detener un contenedor
sudo docker start <contenedor>           # Iniciar un contenedor
sudo docker restart <contenedor>         # Reiniciar un contenedor
sudo docker rm <contenedor>              # Eliminar un contenedor
sudo docker rmi <imagen>                 # Eliminar una imagen de Docker
```

#### 10. **Gestión de SSH**
```sh
sudo systemctl restart ssh               # Reiniciar servicio SSH
sudo systemctl status ssh                # Ver estado del servicio SSH
sudo nano /etc/ssh/sshd_config           # Editar configuración de SSH
ssh <usuario>@<IP>                       # Conectarse a un servidor remoto por SSH
scp <archivo> <usuario>@<IP>:<destino>   # Copiar archivos por SSH
```

#### 11. **Gestión de Procesos**
```sh
top                                      # Monitorizar procesos en tiempo real
htop                                     # Alternativa más visual (requiere instalación: sudo apt install htop)
ps aux | grep <proceso>                  # Buscar un proceso específico
kill <PID>                               # Terminar un proceso por su ID
kill -9 <PID>                            # Forzar la terminación de un proceso
```
---

