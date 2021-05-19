## Workshop HUB : Installer une nouvelle distribution de Linux en multi boot sur les config d'epitech
  
  Dans l'idée globale ce workshop fonctionne pour toutes les distributions de Linux mais certaines choses
  comme les chemins d'accès sont spécifiques à Fedora, cependant, rien de sorcier, si vous avez reussi à changer
  de distribution vous réussirez à en ajouter une.

### 0. Prérequis
  a. Un ordinateur avec un disque dur disposant d'assez d'espace libre pour votre nouvel OS
     avec si vous le souhaitez, Fedora 32 et Windows 10 déja installés.
    
  b. Une clé USB avec assez d'espace libre pour contenir l'installateur de votre nouvel OS.
  
### 1. Créez une clé usb bootable de votre nouveau Linux
  a. vous pouvez utiliser le logiciel BalenaEtcher sous windows ou Linux : https://www.balena.io/etcher
  
  b. Redémarrez votre machine et bootez sur la clé
  
### 2. Installez votre nouvel OS sans installer de logiciel dit "bootloader"

  Les programmes d'installation d'OS installent généralement un logiciel comme Grub2, ces logiciels sont appelés bootloaders,
  grub démarre votre OS à l'allumage de la machine. Dans le cas présent nous avons déjà un bootloader.
  (Grub2 si vous avez la config d'epitech avec le dual boot windows et Fedora)
  
  Comme nous avons dèja un bootloader, pas besoin de l'installer, la plupart des installateurs proposent cette option à un moment ou un autre,
  pretez attention aux instructions à l'écran pour ne pas vous tromper. Pretez également attention à la partition de votre disque où s'installe l'OS,
  vous en aurez besoin plus tard.
  
### 3. Ajoutez l'OS à la configuration de votre bootloader
  Vous avez installer votre OS, plus qu'a lui donner vie !
  Pour se faire commencer par monter la partition où se trouve votre nouvel OS dans votre système.
 
  A présent que vous avez monté la bonne partition, vous devez récupérer ses informations, pour ce faire,
  vous devez d'abord installer le cli pour linux os-prober.
  Puis mettez à jour la configuration de grub,
    "grub2-mkconfig -o /chemin/de/la/config/grub.cfg"
    
    sous fedora 32 et 33 le chemin est normalement le suivant : "/boot/efi/EFI/fedora/grub.cfg"
    \!/ Vous devez théoriquement placer la configuration au bon endroit, avant de \!/
    \!/     faire cette commande, vérifiez l'emplacement du fichier grub.cfg      \!/
    
  Le fichier grub.cfg d'origine doit se trouver au chemin que vous spécifiez après le -o de la commande "grub2-mkconfig".
  
  Une fois que vous avez entrez la commande, Grub est sensé detecté votre nouvel OS et afficher un message du type :
  "Found ${Nom de votre nouvel OS} on ${la partition du nouvel OS}"
  par exemple : "Found Kali Linux 5.4.1 on /dev/sda2"
  
  Si tout est normal et que le message s'est bien affiché, vous n'avez plus qu'a redémarrer la machine
  pour constater que votre nouvel OS apparait dans le menu grub au démarrage
 
 Amusez vous bien avec votre multi boot !
