                                                PROJET CELEBETRIP
                                               Login/Logout component

                                                  PROJET OPEN SOURCE
________________________________________________________________________________________________________________

Component 1 : https://github.com/Sandrine75/CelebetripOSS

Component 2 : https://github.com/Sandrine75/CelebetripLogComponentOSS

Formulaire base de données : https://celebetrip.herokuapp.com/
________________________________________________________________________________________________________________


Je suis interressée par des poolrequest :

Component 1 :


     1-  mettre le projet sous Heroku >> Cela a échoué jusqu'à présent >> revoir le code
     
     2-  anomalie dans le code : l'animation du texte déroulant fait sauter le site au bout de quelques instants. Trouver le bug.

     3-  fusionner le component 1 et 2 (component 1 = CelebetripOSS)
     
Component 2 :

     1-  les liens mlab (base de donnée) ne fonctionnenet plus. 
     >> voir contacts mail avec Mlab *
     La plateforme fonctionne mais le transfert vers la base de donnée ne se fait pas.

     2-  anomalie dans le code :  Au niveau du menu (bootstrap) les onglets des menus sont collés. A voir dans le code
     
     3-  création d'un dashboard en cours

<img src="/images/SandrineGautier.png" alt="Sandrine Gautier"/>

_____________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________
problème de connection vers la base de donnée. Les informtions ne passent pas<br>
--------------
BUG MLAB <br>
--------------
Contact Mlab<br>
--------------

Hello again,

We are seeing successful connections to your "loginlogout" database, so this doesn't appear to be connectivity issue:

2018-06-11T08:01:49.209-0700 I NETWORK  [thread1] connection accepted from 90.79.218.24:57925 #352097 (43 connections now open)
2018-06-11T08:01:49.217-0700 I NETWORK  [conn352097] received client metadata from 90.79.218.24:57925 conn352097: { driver: { name: "nodejs", version: "2.2.34" }, os: { type: "Windows_NT", name: "win32", architecture: "x64", version: "10.0.17134" }, platform: "Node.
js v8.11.2, LE, mongodb-core: 2.1.18" }
2018-06-11T08:01:49.315-0700 I ACCESS   [conn352097] Successfully authenticated as principal loginlogout on loginlogout
You'll likely need to debug the code path that inserts new documents to determine why documents are not being inserted.

--------------
SUITE BUG MLAB<br>
--------------------------------------------------
Le message d'erreur dans la console est persistant :<br>
--------------------------------------------------

(node:5524) UnhandledPromiseRejectionWarning: Unhandled promise rejection (rejection id: 1): MongoError: Authentication failed.
(node:5524) [DEP0018] DeprecationWarning: Unhandled promise rejections are deprecated. In the future, promise rejections that are not handled will terminate the Node.js process with a non-zero exit code.


-----------------------------------
Nouveau contact aide Mlab. Réponse :<br>
-----------------------------------

We're seeing the following error in the ds239137/loginlogout deployment's database log (timestamps are in Pacific Time):

2018-06-14T02:55:57.072-0700 I ACCESS   [conn356954] SCRAM-SHA-1 authentication failed for login on loginlogout from client 90.79.218.24:53710 ; UserNotFound: Could not find user login@loginlogout
This indicates that either the shell and/or driver you are connecting with is not compatible with SCRAM-SHA-1, the authentication mechanism for MongoDB 3.0 and above. If you haven't already, could you look at the following troubleshooting documentation?
http://docs.mlab.com/connecting/#version-compatibility

>> Nota : je n'ai pas trouvé

-----------------------------------
Nouveau message Mlab. Réponse :<br>
-----------------------------------

Hi Sandrine,

We're seeing the following error messages in the server logs:

2018-06-14T08:40:30.376-0700 I NETWORK  [thread1] connection accepted from 90.79.218.24:57976 #357492 (46 connections now open)
2018-06-14T08:40:30.405-0700 I NETWORK  [conn357492] received client metadata from 90.79.218.24:57976 conn357492: { driver: { name: "nodejs", version: "2.2.34" }, os: { type: "Windows_NT", name: "win32", architecture: "x64", version: "10.0.17134" }, platform: "Node.js v8.9.1, LE, mongodb-core: 2.1.18" }
2018-06-14T08:40:30.452-0700 I ACCESS   [conn357492] SCRAM-SHA-1 authentication failed for login on loginlogout from client 90.79.218.24:57976 ; UserNotFound: Could not find user login@loginlogout
There is no database user named "login" for the "loginlogout" database:

https://mlab.com/databases/loginlogout#users

Hope that helps! Please let us know if we can be of any further assistance.

Kind regards,
Sean@mLab
________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________
-------------
BUG HEROKU <br>
-------------

Manip Heroku :<br>
$ cd my-project/<br>
$ git init<br>
$ heroku git:remote -a loginlogoutcelebetrip<br>
$ git add .<br>
$ git commit -am "make it better"<br>
$ git push heroku master<br><br>

Message dans la console :<br>

To https://git.heroku.com/loginlogoutcelebetrip.git
 ! [remote rejected] master -> master (pre-receive hook declined)
error: failed to push some refs to 'https://git.heroku.com/loginlogoutcelebetrip.git'
