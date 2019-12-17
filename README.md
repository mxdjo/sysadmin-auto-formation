### Guide d'auto-formation pour administrateur systeme Linux ##
1) Créer une VM qui fournit les services dhcp (dhcp) et dns(bind ou autre).Configurer le demon dhcp pour utiliser un autre serveur comme pxeboot.
Assurez vous que chaque zone a une zone reverse associée. 
Utilisez quelque chose comme "internal.virtnet" (pas ".local")
comme zone interne DNS.

2) Configurer OpenSSH sur le serveur 

3) Utilisez cobbler pour déployer deux autres serveurs
qui feront office de serveurs master/master LDAP.
Interdisez le anonymouns bind et n'utilisez pas LDAP encrypté

4) Installer fail2ban pour bloquer les attaques SSH,les attaques par brute-force

5) Reconfigurer les 3 serveurs pour l'utilisation de l'authentification LDAP.

6) Créer 2 nouvelles VMs encore avec cobbler et ils devront héberger Postgresql.
L'un (postgresql) est installé manuellement et l'autre avec un playbook ansible

7) Créer un cluster PostgreSQL (HaProxy/Keepalived) et tester la réplication 

8) Configurer un Puppet Master.
 Utiliser ansible pour le deployment

9) Deployer une autre VM. Installer bacula sur lui,en utilisant le postgresql cluster pour stocker la base de données.Stocker le contenu des autres machines sur le serveur


10) Installer deux serveurs httpd (Apache2) . Laissez les configurations par défaut


11) Utiliser un autre serveur pour faire office de iptables-based NAT/round-robin loadbalancing entre les deux serveurs http

12) Revenir à fail2ban pour bloquer les attaques HTTP

13) Sur une VM, installer postfix.  Configurer votre compte gmail pour envoyer des mails de votre réseau interne.

14) Deployer une autre VM. Sur cette VM installer ELK

15) Deployer une autre VM. Sur cette VM, configurer un demon syslog qui écoute les input des autres serveurs. Reconfigurer les autres serveurs pour envoyer leurs logs à syslog et utiliser Kibana pour analyser ses logs.


16) Maintenant créeons des Manifests Puppet Manifests pour s'assurer que toutes les machines sont authentifiés au serveur LDAP et sauvegardés avec bacula server.
