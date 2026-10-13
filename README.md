# Base de données composites : notice d'utilisation

Outil pour suivre les plaques testées (composites et impression 3D) : composition, paramètres de fabrication, résultats d'essais, graphiques de comparaison et empreinte carbone.

---

## 1. Principe de fonctionnement

L'application est un seul fichier (`index.html`) hébergé par GitHub Pages. Les données de référence de l'équipe sont dans un second fichier, `donnees.json`, placé à côté.

- Quand on ouvre l'application, elle charge automatiquement `donnees.json`.
- Les modifications faites dans l'application sont enregistrées **dans le navigateur de la personne** qui les fait.
- Pour que les autres les voient, **une personne met à jour `donnees.json`** dans le dépôt (voir partie 4).

> Ce n'est pas de la saisie en direct à plusieurs : le fichier `donnees.json` du dépôt fait référence. Le plus fiable est qu'**une seule personne** tienne ce fichier à jour.

---

## 2. Utiliser l'application

### Acces a l'application
- Lien sous about (à droite)
  
  Ou bien

- Aller dans l'onglet  **Actions** puis **Deployement** pour avoir acces à l'interface 

### Onglet « Plaques »
Liste de toutes les plaques, avec recherche et filtres par statut et par type.
- **Nouvelle plaque** : ouvre la fiche à remplir.
- **Clic sur une ligne** : ouvre la fiche pour la modifier, la dupliquer ou la supprimer.

### La fiche d'une plaque
- **Type d'échantillon** : *Composite* ou *Impression 3D*. Les champs changent selon le type.
- **Composite** : fibre, résine, layup (empilement), procédé, Vf visée et mesurée.
- **Impression 3D** : matériau, procédé d'impression, hauteur de couche, remplissage, motif, orientation, température de buse, vitesse.
- **Communs** : statut, porosité, épaisseur mesurée, date, notes.
- **Plaque de référence** : à cocher sur la plaque de comparaison (par exemple le carbone vierge). Il y a une référence par type. Les pourcentages sont calculés par rapport à elle.
- **Empreinte carbone** : cinq postes en kg CO₂e (fibre, résine, procédé, transport, fin de vie) et la source des données.
- **Résultats d'essais** : pour chaque propriété, moyenne, écart-type, nombre d'éprouvettes et source (*Essai interne* ou *Fiche technique*).

### Onglet « Matrice »
Deux grilles : fibre × résine pour les composites, matériau × procédé pour l'impression 3D. Chaque case montre les plaques existantes. Le bouton **+** crée la plaque correspondante, déjà pré-remplie.

### Onglet « Résultats »
Tableau d'une propriété à la fois, avec la plaque de référence en premier et le pourcentage de la référence.

### Onglet « Graphiques »
Un graphique en barres par propriété, avec des barres d'erreur (écart-type). On peut basculer entre **valeurs brutes** et **% de la référence**, et filtrer par type d'échantillon.

### Onglet « Empreinte carbone »
Barres empilées par plaque (un poste par couleur) et tableau avec le total et le pourcentage de la référence. L'unité fonctionnelle (par exemple « 1 pièce à rigidité équivalente ») se règle dans Paramètres.

### Onglet « Paramètres »
Tout ce qui apparaît dans les listes déroulantes se modifie ici, et les changements s'appliquent tout de suite :
- fibres, résines, procédés de fabrication, statuts ;
- matériaux, procédés, motifs et orientations d'impression 3D ;
- propriétés mesurées (nom, unité, norme) ;
- unité fonctionnelle de l'empreinte carbone.

Une valeur déjà utilisée par une plaque ne peut pas être supprimée tant que la plaque n'est pas modifiée.

---

## 3. Partager et mettre à jour les données de l'équipe

### Pour la personne qui tient la base
1. Faire ses modifications dans l'application.
2. Aller dans **Paramètres** et cliquer sur **Sauvegarder (JSON)**. Un fichier `donnees.json` est téléchargé.
3. Dans le dépôt GitHub : **Add file** > **Upload files**, glisser `donnees.json` (il remplace l'ancien), puis **Commit changes**.
4. Attendre une ou deux minutes : GitHub Pages met à jour le site.

### Pour les autres utilisateurs
Il suffit d'ouvrir le lien. La dernière version de `donnees.json` se charge toute seule.

Si une personne a fait des modifications dans son navigateur **sans les avoir partagées**, un bandeau apparaît quand une nouvelle version existe. Elle choisit alors :
- **Charger la version du dépôt** : ses modifications locales sont perdues ;
- **Garder la mienne** : elle conserve sa copie, qui ne sera pas partagée tant qu'elle n'a pas été déposée.

### Restaurer une sauvegarde
Dans **Paramètres**, **Restaurer une sauvegarde** charge un fichier JSON dans le navigateur. **Tout réinitialiser** remet la base d'origine, en demandant une confirmation.

---

## 4. Règles de mise à jour (à lire avant de déposer un fichier)

`donnees.json` contient **toute** la base. Quand on dépose un nouveau fichier, il **remplace** l'ancien : si deux personnes déposent chacune leur version, la dernière efface les saisies de l'autre. D'où ces règles.

**Responsables de la mise à jour :** *(à compléter : 1 à 3 personnes maximum)*

1. **Prévenir avant de commencer.** Envoyer un message dans le groupe de l'équipe, du type « je mets à jour la base », pour que personne d'autre ne dépose en même temps.
2. **Partir de la dernière version.** Ouvrir le lien du site. Si un bandeau « nouvelle version disponible » s'affiche, cliquer sur **Charger la version du dépôt**.
3. **Saisir les nouveaux résultats**, puis cliquer **tout de suite** sur **Sauvegarder (JSON)** dans Paramètres.
4. **Déposer `donnees.json`** dans le dépôt : **Add file** > **Upload files** > **Commit changes**. Écrire dans le champ du commit ce qui a été ajouté (par exemple « Résultats traction lin, plaques 3 et 4 »), pour s'y retrouver dans l'historique.
5. **Prévenir que c'est terminé** : « base à jour ».

**Pour tous les autres :**
- Consulter, filtrer, faire des graphiques et exporter vers Excel ne demande aucune règle particulière.
- Les saisies faites dans son navigateur ne sont pas partagées. Les résultats à ajouter à la base sont à transmettre à un responsable.

**À ne pas faire :**
- Ne déposer que `donnees.json`. Ne pas modifier ni supprimer `index.html`, qui est l'application elle-même.
- Ne pas déposer un fichier `donnees.json` plus ancien que celui du dépôt.
- Ne pas utiliser **Tout réinitialiser** avant d'avoir sauvegardé un JSON.

**En cas d'erreur (un fichier écrasé par erreur) :** GitHub garde toutes les versions. Ouvrir `donnees.json` dans le dépôt, cliquer sur **History**, ouvrir la version voulue, la télécharger, puis la redéposer comme à l'étape 4.

---

## 5. Exporter vers Excel

Le bouton **Exporter vers Excel (.xlsx)** en haut de la page télécharge un classeur de trois onglets :
- **Plaques** : une ligne par plaque ;
- **Résultats** : une ligne par plaque et par propriété, avec le pourcentage de la référence (pratique pour les tableaux croisés dynamiques) ;
- **Empreinte carbone** : les cinq postes, le total et le pourcentage de la référence.

Un export **CSV** est aussi disponible dans Paramètres.

> L'export est à sens unique : modifier le fichier Excel ne modifie pas la base. Pour changer une donnée, passer par l'application.
> L'export `.xlsx` demande une connexion internet.

---

## 6. Questions fréquentes

**Mes modifications ont disparu.**
Elles sont enregistrées dans le navigateur utilisé. Elles disparaissent si on change de navigateur ou d'ordinateur, ou si on vide les données du navigateur. Pensez à utiliser **Sauvegarder (JSON)** régulièrement.

**Le site ne montre pas la dernière version des données.**
Attendre une ou deux minutes après le dépôt de `donnees.json`, puis recharger la page (Ctrl+F5 ou Cmd+Maj+R).

**Je vois un bandeau « nouvelle version disponible ».**
Voir la partie 4, *Pour les autres utilisateurs*.

**Le message « Possible data loss » s'affiche dans Excel.**
Il concerne uniquement l'export CSV. Utiliser l'export `.xlsx`, ou faire *Enregistrer sous* au format Classeur Excel.

**Je veux ajouter une fibre, une résine ou une propriété.**
Onglet **Paramètres**.

**Une plaque ne s'affiche pas dans les graphiques.**
Vérifier qu'au moins un résultat (moyenne) est renseigné pour la propriété, et que le filtre de type n'exclut pas la plaque.
