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

z![image](https://github.com/user-attachments/assets/97e8dd2e-37ab-472d-ae40-1d09948b3035)


### On peux par la suite réutiliser ce charset dans la commandes crunch:

    crunch 8 8 -f /usr/share/crunch/charset.lst tssr -t Az@@@@@7 -o wordlist.txt

### `crunch` appel l'utilisation de crunch

### `8 8` Min et Max pour le MDP

### `-f /usr/share/crunch/charset.lst tssr` Appel le charset créer précédement

### `-t Az@@@@@7` spécifie que le MDP doit commencer par Az finir par 7 et les @ autres caractéres

### `-o wordlist.txt` redirige la sortie vers le fichier demandé


### 3️⃣ Utiliser le fichier wordlist.lst créer avec JtR / 

      zip2john chalengeTSSR.zip > haszip

### ` zip2john` appel l'extraction du hash d'un fichier zip

### `chalengeTSSR.zip ` extrait le hash de ce fichier

### `> haszip` dans ce fichier
      
      john --wordlist=/home/practoxx/Documents/wordlist.txt /home/practoxx/haszip

### `john` appel john à exécuter >>>

### `--wordlist=/home/practoxx/Documents/wordlist.txt` chemin vers la liste créer avec crunch

### `/home/practoxx/haszip` sur le fichier contenant le hash précédemement extrait. 

## Voici le MDP

![image](https://github.com/user-attachments/assets/6ac867cc-05ee-4a21-a2c3-c51337ff5855)

















</details>



<details>
<summary>
<h2>
:arrow_forward: 3. FILES ?  
</h2>
</summary>
blabla
</details>




<details>
<summary>
<h2>
:arrow_forward: 4. MAIN  
</h2>
</summary>
blabla
</details>











