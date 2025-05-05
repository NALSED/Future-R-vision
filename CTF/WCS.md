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

### Trouvvé ici 

## Debian Squeeze sources.list

## Debian.org FR mirror
deb http://ftp.fr.debian.org/debian/ squeeze main contrib non-free
deb-src http://ftp.fr.debian.org/debian/ squeeze main contrib non-free

## Debian security updates
deb http://security.debian.org/ squeeze/updates main contrib non-free
deb-src http://security.debian.org/ squeeze/updates main contrib non-free































</details>




<details>
<summary>
<h2>
:arrow_forward: 4. MAIN  
</h2>
</summary>
blabla
</details>











