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

Un clic droit (que se soit sur le **QLIneEdit**, le **QComboBox** ou le **QStandardItemModel**) ouvre un context menu permettant :
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

*** ***

## English version :

### Presentation:
![02](https://user-images.githubusercontent.com/48289933/138742737-32b985d0-f9fd-4d9f-90fa-2a6f807e536b.png)


**QCheckComboBox** is a custom widget for **PySide6** (or PyQt6) or PySide2 (PyQt5).

This widget is a **QComboBox** displaying a list of items with checkboxes.

The goal is to propose a small widget displaying possibly a long list of proposals.

Each (partially) checked box is displayed in the **QLineEdit**.

### Usage:

To change the state of a checkbox:
 - Via a mouse click, the choice window does not close.
 - By pressing the space key, the selection window does not close.
 - By pressing the enter key, the selection window closes.

A right click (whether on the **QLIneEdit**, the **QComboBox** or the **QStandardItemModel**) opens a context menu allowing you to:
 - Copy text from the **QLineEdit**.
 - Undo an action.
 - Redo an action.
 - To check all the checkboxes.
 - Partially check all checkboxes if **TristateMode** is active.
 - Uncheck all checkboxes.
 - Restore default values (if **setDefaultValues** has been used).
Each action has a keyboard shortcut that can be called from the **QLineEdit** and the **QStandardItemModel**.

To display the list of items:
 - A click on the **QLineEdit**.
 - A click on the **QComboBox**.
 - Using the DOWN arrow, the space bar, the tab key or the enter key when the widget has the focus.

The UP and DOWN arrows allow you to navigate in the **QStandardItemModel** without any problem when the **QComboBox** has the focus.

It seems that using the icons crashes with QT5.

### Initialization:
As usual, just call the class: **NewWidget = QCheckComboBox()**.

The possible arguments are the following:
 - **TristateMode** : Execute the **setTristateMode** function with the indicated bool.
 - **CopyIcon**: Execute the **setIcons** function for this icon with the indicated str / QIcon.
 - **UndoIcon** : Executes the **setIcons** function for this icon with the indicated str / QIcon.
 - **RedoIcon** : Executes the **setIcons** function for this icon with the specified str / QIcon.
 - **AllCheckIcon** : Executes the **setIcons** function for this icon with the specified str / QIcon.
 - **AllUncheckIcon** : Executes the **setIcons** function for this icon with the specified str / QIcon.
 - **AllPatriallyCheckIcon** : Executes the **setIcons** function for this icon with the specified str / QIcon.
 - **DefaultValuesIcon** : Executes the **setIcons** function for this icon with the indicated str / QIcon.
 - **Title** + **TitleIcon** : Executes the **setTtitle** function with the indicated title (str) and the icon (str / QIcon) if indicated.
 - **Items**: Executes the **addItems** function with the list of key dictionaries data, text, state, icon indicated.
 - **DefaultValuesCase** : To be coupled with **DefaultValues** in order to define if the search for items is case sensitive with the indicated bool.
 - **DefaultValues**: Executes the **setDefaultValues** function with the indicated dictionary, it must be as follows:
   - Case status: [items searched].
     - Case state: Qt.Checked / Qt.PartiallyChecked
     - List of searched elements: 
       - If it is an integer (int), search for the index (which will add +1 if there is a title).
       - If it's a text (str), search in the data and text of the elements.

### Functions :
 - **setIcons** : Change icons of context menu actions (use default icons).
   - Accepted arguments (str) : Copy, Undo, Redo, AllCheck, AllUncheck, AllPatriallyCheck, DefaultValues.
   - Accepted values (str / QIcon).
 - **setTristateMode** : Enable tristate mode (false by default).
   - Status of the mode (bool).
 - **updateLang**: Update contextual menu (language and icons), must be called if a translation of texts is applied.
 - **addItem**: Add an item in the **QStandardItemModel**.
   - Text (str) of the item: **mandatory**.
   - Data (str) of the element : allows to use a text invisible to the user (if empty, use the text).
   - Status of the box (Qt.Checked / Qt.PartiallyChecked).
   - Icon of the item (str / QIcon).
 - **AddItems** : Add items in the **QStandardItemModel**.
   - Items : List of dictionaries containing the keys : data, text, state, icon.
 - **setStateItems** : Use a checkbox state for the given items.
   - Checkbox state (Qt.Checked / Qt.PartiallyChecked / Qt.Unchecked).
   - List of searched elements: 
     - If it is an integer (int), search for the index (which will add +1 if there is a title).
     - If it is a text (str), search in the data and the texts of the elements.
   - Case sensitive (bool) (false by default).
 - **setStateAll** : Use a checkbox state for all elements.
   - Checkbox state (Qt.Checked / Qt.PartiallyChecked / Qt.Unchecked).
 - **setTitle**: Insert a non-clickable element at the beginning of the **QStandardItemModel**.
   - Title (str).
   - Icon (str or QIcon).
 - **SetDefaultValues**: Set default values for reset.
   - Case status (Qt.Checked / Qt.PartiallyChecked).
   - List of searched elements: 
     - If it is an integer (int), search for the index (which will add +1 if there is a title).
     - If it is a text (str), search in the data and the texts of the elements.
   - Case sensitive (bool) (false by default).
 - **resetDefaultValues** : Reset all checkboxes to default values.
 - **SetReUndoAction**: Undo or reset an action.
   - Action (str) : Undo / Redo.
 - **CopyText** : Copy the text from the QLineEdit to the clipboard.
 - **currentText** : Returns the texts of the selected elements.
 - **currentData** : Returns the data of the selected elements.
