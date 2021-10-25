# QCheckComboBox

## Version Française :

### Présentation :
![01](https://user-images.githubusercontent.com/48289933/138738623-fee58278-7c69-42d5-99da-05d0a62a11a0.png)

**QCheckComboBox** est un widget personnalisé pour **PySide6** (ou PyQt6) voire PySide2 (PyQt5).

Ce widget est un **QComboBox** affichant une liste d’éléments avec des cases à cocher.

Le but est de proposer un petit widget affichant possiblement une longue liste de propositions.

Chaque case (partiellement) cochée est affichée dans le **QLineEdit**.

### Utilisation :

Pour modifier l'état d'une case à cocher :
 - Via un clic souris, la fenêtre de choix ne se ferme pas.
 - Via la touche espace, la fenêtre de choix ne se ferme pas.
 - Via la touche entrée, la fenêtre de choix se ferme.

Un clic droit (que se soit sur le **QLIneEdit**, le **QComboBox* ou le **QStandardItemModel**) ouvre un context menu permettant :
 - De copier le texte de la **QLineEdit**.
 - D'annuler une action.
 - De refaire une action.
 - De cocher toutes les cases.
 - De cocher partiellement toutes les cases si **TristateMode** est actif.
 - De décocher toutes les cases.
 - De restaurer des valeurs par défaut (si **setDefaultValues** a été utilisé).
Chaque action à son raccourci clavier qui peut être appelé depuis le **QLineEdit** et le **QStandardItemModel**.

Pour afficher la liste des éléments :
 - Un clic sur le **QLineEdit**.
 - Un clic sur le **QComboBox**.
 - L'utilisation de la flèche BAS, la barre espace, de la touche tabulation ou bien la touche entrée lorsque le widget a le focus.

Les flèches HAUT et BAS permettent de naviguer dans le **QStandardItemModel** sans que ça pose de problème lorsque le **QComboBox** a le focus.

Il semble que l'utilisation des icônes plante avec QT5.

### Initialisation :
Comme d'habitude, il suffit d'appeler la classe : **NewWidget = QCheckComboBox()**.

Les arguments possibles sont les suivants :
 - **TristateMode** : Exécute la fonction **setTristateMode** avec le bool indiqué.
 - **CopyIcon** : Exécute la fonction **setIcons** pour cette icône avec le str / QIcon indiqué.
 - **UndoIcon** : Exécute la fonction **setIcons** pour cette icône avec le str / QIcon indiqué.
 - **RedoIcon** : Exécute la fonction **setIcons** pour cette icône avec le str / QIcon indiqué.
 - **AllCheckIcon** : Exécute la fonction **setIcons** pour cette icône avec le str / QIcon indiqué.
 - **AllUncheckIcon** : Exécute la fonction **setIcons** pour cette icône avec le str / QIcon indiqué.
 - **AllPatriallyCheckIcon** : Exécute la fonction **setIcons** pour cette icône avec le str / QIcon indiqué.
 - **DefaultValuesIcon** : Exécute la fonction **setIcons** pour cette icône avec le str / QIcon indiqué.
 - **Titre** + **TitleIcon** : Exécute la fonction **setTtitle** avec le titre (str) indiqué ainsi que l'icône (str / QIcon) si indiqué.
 - **Items** : Exécute la fonction **addItems** avec la liste de dictionnaires de clés data, text, state, icon indiquée.
 - **DefaultValuesCase** : À coupler avec **DefaultValues** afin de definir si la recherche des éléments respecte la casse avec le bool indiqué.
 - **DefaultValues** : Exécute la fonction **setDefaultValues** avec le dictionnaire indiqué, il doit être comme suit :
   - État de case : [éléments recherchés].
     - État de case : Qt.Checked / Qt.PartiallyChecked
     - Liste des éléments recherchés : 
       - Si c'est un entier (int), recherche de l'index (qui ajoutera +1 s'il y a un titre).
       - Si c'est un texte (str), recherche dans les data et les textes des éléments.

### Fonctions :
 - **setIcons** : Modification des icônes des actions du context menu (utilisation d'icônes par défaut).
   - Arguments (str) acceptés : Copy, Undo, Redo, AllCheck, AllUncheck, AllPatriallyCheck, DefaultValues.
   - Valeurs acceptées (str / QIcon).
 - **setTristateMode** : Activation du mode tristate (faux par défaut).
   - Etat du mode (bool).
 - **updateLang**: Mise à jour du menu contextuel (langue et icônes), doit être appelé si une traduction des textes est appliquée.
 - **addItem** : Ajout d'un élément dans le **QStandardItemModel**.
   - Texte (str) de l'élément : **obligatoire**.
   - Data (str) de l'élément : permet d'utiliser un texte invisible à l'utilisateur (si vide, utilisation du texte).
   - Etat de la case (Qt.Checked / Qt.PartiallyChecked).
   - Icône de l'item (str / QIcon).
 - **addItems** : Ajout d'éléments dans le **QStandardItemModel**.
   - Items : Liste de dictionnaires contenant les clés : data, text, state, icon.
 - **setStateItems** : Utilisation d'un état de case à cocher pour les éléments donnés.
   - État de case (Qt.Checked / Qt.PartiallyChecked / Qt.Unchecked).
   - Liste des éléments recherchés : 
     - Si c'est un entier (int), recherche de l'index (qui ajoutera +1 s'il y a un titre).
     - Si c'est un texte (str), recherche dans les data et les textes des éléments.
   - Prise en compte de la casse (bool) (faux par défaut).
 - **setStateAll** : Utilisation d'un état de case à cocher pour tous les éléments.
   - État de case (Qt.Checked / Qt.PartiallyChecked / Qt.Unchecked).
 - **setTitle** : Insère un élément non cliquable au début du **QStandardItemModel**.
   - Titre (str).
   - Icône (str ou QIcon).
 - **setDefaultValues** : Définition de valeurs par défaut pour réinitialisation.
   - État de case (Qt.Checked / Qt.PartiallyChecked).
   - Liste des éléments recherchés : 
     - Si c'est un entier (int), recherche de l'index (qui ajoutera +1 s'il y a un titre).
     - Si c'est un texte (str), recherche dans les data et les textes des éléments.
   - Prise en compte de la casse (bool) (faux par défaut).
 - **resetDefaultValues** : Réinitialisation de toutes les cases à cocher avec les valeurs par défaut.
 - **setReUndoAction** : Annulation ou de rétablissant d'une action.
   - Action (str) : Undo / Redo.
 - **copyText** : Copie dans le presse-papiers le texte du QLineEdit.
 - **currentText** : Retourne les textes des éléments sélectionnés.
 - **currentData** : Retourne les data des éléments sélectionnés.

