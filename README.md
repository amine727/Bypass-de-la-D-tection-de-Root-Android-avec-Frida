Lab 11 – Bypass Root Detection (Uncrackable Level 2)
🎯 Objectif
L'objectif de ce lab est de contourner les mécanismes de protection d'une application Android vulnérable, notamment :
Détection du root
Vérifications de sécurité côté Java
Fermeture automatique de l'application
Le but final est de maintenir l'application ouverte malgré ces protections.
---
🛠️ Environnement
Android Emulator (rooté)
ADB
Frida (v17.9.1)
Application : `owasp.mstg.uncrackable2`
---
🚀 Étapes de réalisation
1️⃣ Lancement de Frida Server
```bash
adb push frida-server /data/local/tmp/
adb shell
su
chmod 755 /data/local/tmp/frida-server
/data/local/tmp/frida-server &
```
<img width="1801" height="241" alt="12" src="https://github.com/user-attachments/assets/041b93c4-4d14-423f-b156-cdbaac198c2a" />

---
2️⃣ Vérification des processus
```bash
frida-ps -Uai
```
<img width="1264" height="507" alt="10" src="https://github.com/user-attachments/assets/9badcf27-3be2-4908-b150-08e7241d53ed" />

✔ Vérifier que l'application apparaît : `owasp.mstg.uncrackable2`
---
3️⃣ Lancement avec Frida
```bash
frida -U -f owasp.mstg.uncrackable2 -l bypass_root.js
```
![Lancement du script Frida](https://github.com/user-attachments/assets/b425b145-8dbe-43ee-80d9-f5e933fdf22a)
---
🧠 Conclusion
Ce lab montre qu'il est possible de contourner efficacement les mécanismes de sécurité d'une application Android en utilisant Frida.
Le bypass dynamique permet de :
Manipuler le comportement de l'application en temps réel
Désactiver les protections sans modifier le code source
Analyser les applications sécurisées
