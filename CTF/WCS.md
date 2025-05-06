# 🏴‍☠️`CTF WCS`🏴‍☠️ 

## 1️⃣ Intro

### Bienvenu dans ce challenge cybersécurité de fin de session TSSR.
### Tu peux utiliser tous les outils, techniques, sites web, logiciels, que tu souhaites pour arriver
### à tes fins.
### Les fichiers ou documents fournis peuvent t'aider, ou pas...
### Si tu es bloqué, ton formateur pourra - peut-être - t'aider à avancer !
### Soit inventif et perspicace !
### BONNE CHANCE !


<details>
<summary>
<h2>
:arrow_forward: 2. INIT  
</h2>
</summary>


# ➡️ Ouvrir le Zip

### 1️⃣ Prise en main de [JtR](https://github.com/NALSED/Future-R-vision/blob/main/LINUX/app/password/john_the_ripper2.md)

### 2️⃣ Utilisation de [crunch](https://ns3edu.com/blog/a-detailed-guide-on-crunch-tool/) [crunch2](https://itintegrity.wordpress.com/2012/08/18/crunch-un-generateur-de-wordlist-simple-et-efficace/) pour généger une wordlist.

### Vérifier que crunch est installé et version
      crunch -h

### Editer le fichier de charset dans `/usr/share/crunch/charset.lst`

![image](https://github.com/user-attachments/assets/69eaf5fd-95d6-4355-b929-ea250f4ad418)

### On peux par la suite réutiliser ce charset dans la commandes crunch:

    crunch 8 8 -f /usr/share/crunch/charset.lst tssr -t Az@@@@@7 -o wordlist.lst

### `crunch` appel l'utilisation de crunch

### `8 8` Min et Max pour le MDP

### `-f /usr/share/crunch/charset.lst tssr` Appel le charset créer précédement

### `-t Az@@@@@7` spécifie que le MDP doit commencer par Az finir par 7 et les @ autres caractéres

### `-o wordlist.lst` redirige la sortie vers le fichier demandé


### 3️⃣ Utiliser le fichier wordlist.lst créer avec JtR / 

      zip2john chalengeTSSR.zip > haszip

### ` zip2john` appel l'extraction du hash d'un fichier zip

### `chalengeTSSR.zip ` extrait le hash de ce fichier

### `> haszip` dans ce fichier
      
     sudo john --wordlist=/home/practoxx/Documents/wordlist.lst /home/practoxx/haszip

### `john` appel john à exécuter >>>

### `--wordlist=/home/practoxx/Documents/wordlist.lst` chemin vers la liste créer avec crunch

### `/home/practoxx/haszip` sur le fichier contenant le hash précédemement extrait. 

### Et voila le MDP

![image](https://github.com/user-attachments/assets/3c5f1eba-cf97-4548-b0a0-716e89ee77a1)

</details>



<details>
<summary>
<h2>
:arrow_forward: 3. FILES ?  
</h2>
</summary>

## 1️⃣ `Accéder à la VM`

### Au démarage spammer e
### On arrive sur cette page
![image](https://github.com/user-attachments/assets/5b4dcb50-0cec-4332-9dd3-48ec8b6c6f41)

### A laide des fléches descendre jusquà la ligne commençant "linux"
![image](https://github.com/user-attachments/assets/f17c24bf-e563-4784-b83a-93058ca2a100)

### Derrière le mot quiet
![image](https://github.com/user-attachments/assets/906445e9-68aa-47f6-9033-09d0c9df2138)

### Ecrire rw init=/bin/bash ⚠️ Clavier en qwerty ⚠️ Puis sauvegarder.

### Résultat attendu
![image](https://github.com/user-attachments/assets/39cf6d06-daf0-48ff-9a18-381f9b697da3)

### changer le mot de passe de root
      passwd

![image](https://github.com/user-attachments/assets/7e81867e-ea42-44eb-8f10-8e181dbfc66e)

### lister les utilisateur 
      getent passwd {1000..1003} # liste les utilisateur avec UUID entre 1000 et 1003

![image](https://github.com/user-attachments/assets/8ab3159d-8c20-4bd8-a67f-583a55f7d99a)

### Changer les MDP des deux utilisateurs
      passwd wildssh
      passwd ftponly

### Quitter ce mode avec la commande
      exec /sbin/init

### On peux accéder à la machine via root

## 2️⃣ `trouver les fichiers`

      cd /home/ftponly/ftp/files
      
![image](https://github.com/user-attachments/assets/3741657c-7994-42be-b1e6-a2591bcb1039)

### ⚠️ Message erreur après => apt install unzip : en attente de l'entête
### Probléme avec le fichier => etc/apt/sources.list
### Ajouter la première ligne

![image](https://github.com/user-attachments/assets/06a17126-8a39-46b4-9e89-ffd6b50e7c89)

### Trouvé ici 

            ## Debian Squeeze sources.list

            ## Debian.org FR mirror
            deb http://ftp.fr.debian.org/debian/ squeeze main contrib non-free
            deb-src http://ftp.fr.debian.org/debian/ squeeze main contrib non-free

            ## Debian security updates
            deb http://security.debian.org/ squeeze/updates main contrib non-free
            deb-src http://security.debian.org/ squeeze/updates main contrib non-free


### Installer unzip
     apt install unzip

### On passe à la partie 4 MAIN

</details>











<details>
<summary>
<h2>
:arrow_forward: 4. MAIN  
</h2>
</summary>

>Challenge 1 : trouver url et mot de passe
>Mot de passe du fichier :
>Mot de passe classique de la formation concaténé avec la somme des 2 ports
>utilisée dans la première partie. Si tu as utilisé une méthode sans utilisation de
>port spécifique, demande à ton formateur le mot de passe...


### 1️⃣ Trouver le MPD :

### Somme des deux ports ftp + ssh (pour les deux user ftponty et wild ssh)
### ftp 21 ou 20 et ssh 22 => 43 ou 42 avec le mot de passe classique de la formation Azerty1*43 ou 42

### Copier le fichier du debian challenge => kali perso
      sudo ufw allow 22 # autorise le port 22 ufw (kali)
      sudo service ssh start # démare le ssh
      scp challenge1.zip practoxx@192.168.0.131:/home/practoxx/Documents
      
### Déziper le fichier avec le MDP `Azerty1*43` 

### 2️⃣ Analyser le PDF
### Le PDF nous racconte l'hisoire des argonautes et à la fin une URL nous est donné :
https://quest_editor_uploads.storage.googleapis.com/challenge.pcap

### Une fois cette url entrée dans le navigateur un fichier wireshark est téléchargé
### Quand on regarde les captures http une autre url nous est donnée

![image](https://github.com/user-attachments/assets/44035f1c-ab7f-40a6-b191-4ab37d608f95)
### En entrant cette adresse http://cyber-course.wildcodeschool.com/

![image](https://github.com/user-attachments/assets/ecf6be0b-fc13-4723-ba1c-ede8da81876d)

### l'entrée de la grotte


















>Challenge 2 : trouver le nombre
>Mot de passe du fichier :
>11 premiers caractères du nom du site (après le https://) trouvé au challenge 1
>Et les 6 derniers caractères du mot de passe trouvé au challenge 1

>Challenge 3 : trouver l'id
>Mot de passe du fichier :
>20 premiers caractères du sha512sum du numéro de coffre trouvé au
>challenge 2

>Challenge 4 : trouver le mot de passe
>Mot de passe du fichier :
>10 premiers chiffres du code du bouton (trouvé au challenge 3) mis au cube

>Challenge 5 : trouver le mot de passe
>Mot de passe du fichier :
>Date de naissance (en français) sur 6 chiffres concatenée avec le nom de
>famille


</details>











