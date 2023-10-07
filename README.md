# homelab
A simple HomeLab Server


# LXDE NO SUSPEND OR HIBERNATE
systemctl status acpid
systemctl status upower
sudo systemctl mask sleep.target suspend.target hibernate.target hybrid-sleep.target
sudo systemctl set-property sleep.target suspend.target hibernate.target hybrid-sleep.target RebootUSec=infinity ShutdownUSec=1000000000

# ENABLE SSH

Una vez instalado, el servicio SSH debería iniciarse automáticamente. Puedes verificar si está en ejecución con el siguiente comando:

sudo systemctl status ssh
Si no está en ejecución, puedes iniciar el servicio con:

sudo systemctl start ssh
Para asegurarte de que el servicio se inicie automáticamente en el arranque, utiliza:

sudo systemctl enable ssh
Configura el Cortafuegos (Firewall):

Si tienes un cortafuegos habilitado, asegúrate de permitir conexiones a través del puerto 22 (el puerto predeterminado para SSH). Puedes hacerlo ejecutando el siguiente comando:

sudo ufw allow 22
Si no tienes UFW (Uncomplicated Firewall) instalado, puedes instalarlo y configurarlo con los siguientes comandos:

sudo apt-get install ufw
sudo ufw allow 22
sudo ufw enable


# STATIC IP
Cambiar la Configuración de Red de Forma Manual:

Si prefieres configurar la dirección IP de forma estática, puedes editar el archivo de configuración de red manualmente. Abre una terminal y ejecuta el siguiente comando para editar el archivo de configuración:

sudo nano /etc/network/interfaces
Luego, cambia la configuración para utilizar una dirección IP estática. Por ejemplo:

auto eth0
iface eth0 inet static
address 192.168.1.100
netmask 255.255.255.0
gateway 192.168.1.1
dns-nameservers 8.8.8.8 8.8.4.4
Guarda los cambios y reinicia la interfaz de red con:

sudo systemctl restart networking
