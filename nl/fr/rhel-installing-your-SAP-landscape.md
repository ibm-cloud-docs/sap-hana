---

copyright:
years: 2017, 2019
lastupdated: "2019-03-01"

keywords: SAP NetWeaver, ABAP, ASCS Instance, Database Instance, ABAP SAP Central Services, SWPM, application server, database server

subcollection: sap-netweaver-rhel-qrg

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# Installation de votre paysage SAP
{: #install_landscape}

## Installation des packages RPM (prérequis)
{: #RPM}

Une installation SAP requiert un certain nombre de conditions pour les packages qui sont installés sur le système d'exploitation et pour les démons du système d'exploitation qui sont exécutés. Consultez les derniers [guides d'installation ![Icône de lien externe](../icons/launch-glyph.svg "Icône de lien externe")](https://support.sap.com/software/installations.html) (requiert un [ID utilisateur SAP](/docs/infrastructure/sap-netweaver?topic=sap-netweaver-getting-started#getting-started)) et les [ notes de prise en charge ![Icône de lien externe](../icons/launch-glyph.svg "Icône de lien externe")](https://support.sap.com/notes){: new_window} (requiert un ID utilisateur SAP) de SAP pour obtenir une liste actualisée de ces conditions requises. Deux packages supplémentaires doivent être installés :
* compat-sap-c++ : permet généralement la compatibilité de l'environnement d'exécution C++ avec les compilateurs utilisés par SAP. Red Hat Enterprise Linux for SAP Business Application 7.X étant sélectionné comme système d'exploitation à la fois pour le serveur d'applications de 32 Go et le serveur de base de données de 192 Go, vous utiliserez `compat-sap-c++-7`.
* uuidd : maintient la prise en charge du système d'exploitation pour la création des UUID.

### Vérification de l'installation de uuidd

1. Vérifiez si le démon `uuid daemon (uuidd)` est installé. Si ce n'est pas le cas, installez-le et démarrez-le.
```
[root@sdb192 ~]# rpm -qa | grep uuidd
[root@sdb192 ~]# yum install uuidd
[root@sdb192 ~]# chkconfig uuidd on
[root@sdb192 ~]# service uuidd start
```

### Installation du package compat-sap-c++-7

1. Suivez la [note SAP 2195019 ![Icône de lien externe](../icons/launch-glyph.svg "Icône de lien externe")](https://launchpad.support.sap.com/#/notes/2195019){: new_window} et installez le package compat-sap-c++-7, puis créez un lien lointain spécifique (requis par les fichiers binaires SAP). Consultez les notes SAP propres à l'édition du produit que vous installez pour déterminer si la bibliothèque est requise ou non.
```
[root@sdb192 ~]# yum install compat-sap-c++-7-7.2.1-2.e17_4.x86_64.rpm
....
[root@sdb192 ~]# mkdir -p /usr/sap/lib
[root@sdb192 ~]# ln -s /opt/rh/SAP/lib64/compat-sap-c++.so /usr/sap/lib/libstdc++.so.6
```

## Téléchargement de votre logiciel SAP
{: download_software}

Connectez-vous au [portail de support SAP ![Icône de lien externe](../icons/launch-glyph.svg "Icône de lien externe")](https://support.sap.com/en/index.html){: new_window}, cliquez sur **Download Software**, et téléchargez les DVD requis vers une unité partagée locale. Transférez les fichiers vers votre serveur mis à disposition. Vous pouvez également télécharger le [gestionnaire de téléchargement du logiciel SAP ![Icône de lien externe](../icons/launch-glyph.svg "Icône de lien externe")](https://support.sap.com/en/my-support/software-downloads.html#section_995042677){: new_window}, l'installer sur votre serveur cible puis télécharger directement les images du DVD sur le serveur.

## Préparation pour l'interface SWPM de SAP
{: #prepare_for_GUI}

Suivant la latence et la bande passante du réseau, vous souhaiterez peut-être exécuter l'interface utilisateur SWPM (SAP Software Provisioning Manager) à distance dans une session VNC. Une autre option est d'exécuter l'interface localement et de se connecter à SWPM sur l'ordinateur cible. Consultez la [documentation de SWPM ![Icône de lien externe](../icons/launch-glyph.svg "Icône de lien externe")](https://wiki.scn.sap.com/wiki/display/SL/Software+Provisioning+Manager+1.0+and+2.0){: new_window} si vous décidez d'exécuter l'interface utilisateur localement.

Les étapes ci-dessous décrivent l'exécution de l'interface SWPM à distance dans une session VNC. Cette option installe un serveur VNC qui risque de ne pas être en ligne avec la sécurisation renforcée de votre système d'exploitation. Veillez à respecter vos mesures de sécurité. Consultez la [documentation relative à VNC ![Icône de lien externe](../icons/launch-glyph.svg "Icône de lien externe")](http://searchnetworking.techtarget.com/definition/virtual-network-computing){: new_window} pour obtenir un aperçu de ses fonctions si vous ne les connaissez pas.

1. Utilisez les commandes suivantes pour installer un serveur VNC.
```
  [root@sdb192 ~]# yum install tigervnc-server

  ...
```

2. Utilisez la commande suivante pour installer le gestionnaire de fenêtre X11, `twm`, inclus dans la distribution Linux.

`[root@sdb192 ~]# yum install twm`

3. Installez un émulateur de terminal, par exemple `xterm`.

 `[root@sdb192 ~]# yum install xterm`

4. Démarrez le serveur VNC à partir de la ligne de commande.

 `[root@sdb192 ~]# vncserver`

Vous avez maintenant besoin d'un programme de client VNC. Plusieurs implémentations sont disponibles pour tous les systèmes d'exploitation de manière gratuite. Le port `590X` (où X est le nombre de serveurs en cours d'exécution, partant de 1) doit généralement être accessible depuis votre client.

Vous devrez peut-être démarrer un `xterm` depuis le menu d'arrière-plan de `twm`. Vous pouvez démarrer `SWPM` (`sapinst`) depuis `xterm`.

## Installation du logiciel SAP
{: #install_software}

Après avoir téléchargé le support d'installation, suivez la procédure d'installation standard décrite dans le guide d'installation de SAP pour votre version et vos composants SAP ainsi que les notes SAP correspondantes.

Vous pouvez démarrer SAP SWPM depuis `xterm` et exécuter les étapes d'installation.

### Installation du logiciel SAP dans un environnement à trois niveaux

Suivez les instructions de SAP SWPM relatives à une configuration à trois niveaux.

1. Sélectionnez **Système distribué** et exécutez l'installation de l'ASCS et l'installation de la base de données sur le serveur de base de données.
2. Installez l'ABAP sur le serveur d'applications. Veillez à utiliser les adresses privées pour l'ASCS et les noms d'hôte de la base de données lors de l'installation du serveur d'applications.

L'utilisation des adresses privées et des noms d'hôte garantit que le trafic réseau entre le serveur d'applications et ASCS, ou la base de données, passe par le réseau privé et non par le réseau public.