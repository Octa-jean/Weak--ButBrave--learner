# Weak--ButBrave--learner

Weak-ButBrave-Learner, est un projet pédagogique C++ en cours de développement dont l’objectif est de permettre de constituer une base d'images annotées pour un apprentissage supervisé, puis de la multiplier par augmentation de données. 

## Cahier des charges

### Annotation 

	L'utilisateur ouvre un dossier contenant des images. L'interface affiche l'image courante avec zoom et déplacement, la liste des images du dossier avec un indicateur annotée / non annotée, et la liste des classes définies par l'utilisateur. À la souris, il trace des rectangles englobants, leur associe une classe, redimensionne ou déplace un rectangle existant, ou le supprime. La navigation d'une image à l'autre doit être possible au clavier. 

### Persistance 

	Les annotations sont sauvegardées et relues dans un format texte au choix, documenté dans le cahier des charges : soit un fichier .txt par image au format YOLO (classe, centre x, centre y, largeur, hauteur, normalisés), soit un fichier JSON unique décrivant toute la base. Le programme doit être capable de relire ce qu'il a écrit, et ne doit jamais perdre le travail en cours en cas de fermeture. 

### Augmentation 

	À partir de la base annotée, le programme génère N variantes par image en enchaînant des transformations paramétrables : miroir horizontal ou vertical, rotation, changement d'échelle et recadrage, variation de luminosité et de contraste, flou gaussien, bruit gaussien ou poivre-et-sel, variation de teinte. 
Les boîtes englobantes doivent être transformées de façon cohérente avec l’image : c'est le point le plus délicat du sujet, et il devra être traité explicitement dans le cahier des charges (que devient une boîte qui sort partiellement ou totalement du cadre après une rotation ?). Une fenêtre de prévisualisation montre le résultat d'un tirage aléatoire avant de lancer la génération complète. 

La génération produit un dossier de sortie contenant les images et les annotations correspondantes, un fichier récapitulatif indiquant le nombre d'images par classe (histogramme affiché dans l'interface), et une répartition apprentissage / validation selon un pourcentage choisi par l'utilisateur. 

La bibliothèque de traitement d'image sera opencv 

L'interface graphique pourra être réalisée avec les MFC, ou wxWidgets, ou Qt, ou SDL3 

### Architecture 

	Le programme doit être conçu de manière modulaire : une classe CBaseImages gère le modèle de données indépendamment de l'interface, une classe CAnnotation représente une boîte et sa classe, une hiérarchie de classes CTransformation expose une méthode virtuelle appliquant la transformation à l'image et aux annotations, une classe gère la lecture et l'écriture des formats de fichiers, et d'autres classes gèrent l'interface graphique. 

La génération doit pouvoir être lancée en ligne de commande, sans interface graphique, à partir d'un fichier de configuration. 
L'interface graphique doit pouvoir être modifiée/remplacée sans impacter le reste du code.

### Collaborateurs

Membres du groupe 2A, MEEA&TSI UBE.

