# Instalation/Configuration de WinRM
---
## 1️⃣ Configuration de WinRM => Client
---
* ###  `Activer WinRM` 
#### Services => Windows Remote Management (WS-Management) => clic droit Properties
![image](https://github.com/user-attachments/assets/c6dd562b-b1b5-42a5-9b92-66890c0edab3)
#### Puis Automatic (Delayed Start)
![image](https://github.com/user-attachments/assets/890c875e-f02c-42d6-95c8-2d0b6e99f0a1)
---
* ### `Firewall`
#### Dans les régle rentrante => New Rules ⚠️Attention deux régles sont à éditer à la suite!! 
![image](https://github.com/user-attachments/assets/d10bddad-6dd2-49b7-a52b-84ba5f389711)
#### Cocher Predefined => Windows Remote Management et par la suite Remote Management(compatibility
![image](https://github.com/user-attachments/assets/58edd5e1-7735-46f4-a2cc-6db7c8ffd39f)
#### Puis Profile => Domain, Pivate
![image](https://github.com/user-attachments/assets/76f7488e-ccff-435e-ade2-fa8adb10d025)
#### Allow Connection
#### Clic droit sur Windows Remote Management (HTTP-In) => Properties
![image](https://github.com/user-attachments/assets/7be50976-2c66-47f2-97e9-28dd08801eba)
#### Advanced => Cocher Domain
![image](https://github.com/user-attachments/assets/d33ab730-74d3-4fbe-bc96-8a92957a63a3)
---
* ### `Computer Manager`
#### System Tools => Local Users and Group => clic droit sur l'utilisateur concerné => Properties
![image](https://github.com/user-attachments/assets/e9d8111b-9854-47a5-84f1-121840cd36a3)
#### 🔵 Member of => 🔴 Add..
![image](https://github.com/user-attachments/assets/4a86c6a9-a73a-49e2-9e80-d8b03a02edc0)
#### Advanced..
![image](https://github.com/user-attachments/assets/ea99d218-7102-4a01-ba79-7afdd0948ec4)
#### Find Now
![image](https://github.com/user-attachments/assets/31a45453-9104-4126-91d7-a05f1601908e)
#### Remote Management Users
![image](https://github.com/user-attachments/assets/3651b310-94c0-4630-a33c-7638a5fc51f3)
---
* ### `PS en Admin`
#### la commande       
      winrm quickconfig
      Enable-PSRemoting
#### Configurer l'hôtes de confiance
      Set-Item WSMan:\localhost\Client\TrustedHosts SRVWIN-ADDS-GUI.Pharmgreen.com
      winrm get winrm/config/client
#### On voit que le client de confiance est bien présent :
![image](https://github.com/user-attachments/assets/41b2a654-bbc6-4223-9d19-179310bf83ac)


















