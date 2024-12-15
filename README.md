# sambaEc2Aws
Paso a paso de como desplegar SAMBA para compartir archivos
- **Primer paso** crear una instancia Ec2
<img src="https://i.ibb.co/zGBvV2H/Screenshot-1.png" alt="Descripción de la imagen">
<img src="https://i.ibb.co/W0sK0TK/image.png" alt="Descripción de la imagen">
<img src="https://i.ibb.co/ygYG1Fn/image.png">
<img src="https://i.ibb.co/Bw9zt4W/image.png">
<img src="https://i.ibb.co/FbSQ4jg/image.png">
<img src="https://i.ibb.co/f4kxSPW/image.png">
<img src="https://i.ibb.co/JH6jx9r/image.png">
<img src="https://i.ibb.co/B3k2Y03/image.png">
- luego espera que la comprobacion de la instancia sea 2/2 
<img src="https://i.ibb.co/c3fjxds/image.png">

- **Segundo Paso** Asigna una IP Elastica
  
<img src="https://i.ibb.co/qLS14Yg/image.png">
<img src="https://i.ibb.co/SXt3KFH/image.png">
<img src="https://i.ibb.co/xmKHB5s/image.png">
<img src="https://i.ibb.co/sVN5MQ4/image.png">
<img src="https://i.ibb.co/dP0vVRx/image.png">

**Tercer Paso** Editar las reglas de entrada

<img src="https://i.ibb.co/pfm7g2V/image.png">
<img src="https://i.ibb.co/HrTS5QV/image.png">
<img src="https://i.ibb.co/X8cG56d/image.png">

# 👩‍💻 Instalacion y configuracion de SAMBA
- comando para actualizar y instala paquetes.
```
 sudo apt update
```
```
sudo apt  upgrade
```
- instalacion de samba
```
sudo apt install samba samba-client samba-common
```
- creamos la carpeta y verificamos los permisos
```
mkdir compartido
```
```
ls -l
```
- damos permisos a la carpeta
```
chmod 777 compartido/
```
- realizamos una copia de seguridad del archivo *smb.conf*
```
cd /etc/
```
```
cd samba/
```
```
sudo cp smb.conf smb.conf.backup
```
- editamos y configuramos el archivo *smb.conf*
```
sudo nano /etc/samba/smb.conf
```
```
[Compartido]
  path =  /home/admin/compartido/
  browsable = yes
  writable = yes
  guest ok = yes
  read only = no
  forcer user = nobody
```
- reiniciar samba
```
sudo systemctl restart nmbd
```
```
sudo systemctl status nmbd
```

- comprobar el acceso
```
\\<ip-elastica>
```
- para ver la ip
```
curl http://icanhazip.com
```
