---
description: >-
  Module d'inclusion des frais d'approche dans le calcul du prix de revient d'un
  article.
---

# Purchase Landed Costs

Module mis à jour par Akretion :  [https://github.com/akretion/purchase-workflow/tree/12.0-purchase-landed-cost-usability/purchase\_landed\_cost](https://github.com/akretion/purchase-workflow/tree/12.0-purchase-landed-cost-usability/purchase_landed_cost)

## Objectif

Le module ‘_Purchase Landed Costs_’ permet d’actualiser le prix de revient des articles en incluant tous types de frais d’approches \(transport, douane, frais de paiement…\) au prix d’achat d’origine \(de la facture du fournisseur\).

Le bouton pour accéder à l’historique du prix de revient d'un article se trouve dans l’onglet _“Information Générale”_ de la fiche article :

![](.gitbook/assets/image%20%287%29.png)

Il permet d'afficher un historique de ce type :

![](.gitbook/assets/image%20%2810%29%20%283%29.png)

Grâce au module, on pourra donc calculer ce "nouveau prix de revient" grâce à une moyenne pondérée :

$$
Nouveau Prix = \frac{AncienStock*Ancien Prix + Arrivage*Prix Acquisition}{AncienStock + Arrivage}
$$

Avec :

* `AncienStock` la quantité d'articles en stock avant l'arrivage \(nul si négatif\)
* `AncienPrix` l'ancien prix de revient de l'article
* `Arrivage` la quantité d'articles de l'arrivage
* `PrixAcquisition` le prix total d'acquisition de l'article \(_'landed cost'_ en anglais\) incluant le prix d'achat au fournisseur et les frais d'approche.

## Usage

### 1. Achat d'articles

Une fois le module installé, il suffit de réaliser un achat d'un article stockable. Une fois qu'on confirme la commande et que l'option _'Doit être lié à des Frais d'approche'_ est cochée, le bouton _"Enregistrer les Frais d'approche"_ apparaît :

![](.gitbook/assets/image%20%2818%29.png)

### 2. Création de l'objet _'Distribution de frais d'approche'_

En cliquant sur _"Enregistrer les Frais d'approche"_  on créé un brouillon d'un nouvel objet Odoo appelé _'Distribution de frais d'approche'_ qui associe à un ou plusieurs _'Mouvements d'Opération de réception'_ , les frais d'approches liés aux Articles de ces Mouvements :

![](.gitbook/assets/image%20%284%29%20%281%29.png)

{% hint style="info" %}
Une _'Opération'_  \(ou plus précisément dans notre cas _'Opération de réception'_\) est un objet Odoo, composé de différents _'Mouvements'_. 

Une _'Opération de réception'_ est le plus souvent liée à un _'Bon de Commande'_ et regroupe tous les différents mouvements de stock qui vont devoir être réalisés pour enregistrer l'entrée en stock de **tous les articles** \(stockables\) achetés dans le _'Bon de Commande'._

Un _'Mouvement'_  \(ou _'Mouvement de réception'_ dans notre cas\) est donc un sous-objet d'une _'Opération',_ contenant les informations liées à l'entrée en stock d'**un type d'article** particulier de cette _'Opération de réception'_ \(et donc généralement de ce _'Bon de Commande'_\)_._
{% endhint %}

Dans l'onglet _"Mouvements de réception"_ on aura donc la liste des mouvements de stocks auxquels on veut associer certains frais d'approches.

Pour comprendre la signification des colonnes, on a :

* **Prix unitaire** : Prix d'achat unitaire de l'article
* **Montant total** : le prix total \(Quantity \* Unit Price\) du Mouvement de réception sans frais d'approche
* **Montant des frais** : les frais d'approche pour ce Mouvement de réception
* **Frais unitaire** : La valeur des frais d'approche pour chaque unité d'article du Mouvement
* **Ancien prix de revient** : l'ancien prix de revient de l'article \(cf `AncienPrix`\)
* **Prix d'Acquisition** : le prix total d'acquisition de l'article via cet achat en particulier, incluant le prix d'achat et les frais d'approches \(cf `PrixAcquisition` \)

Dans l'onglet _"Frais d'approche"_ on aura la liste des frais d'approches associés à ces Mouvements de réception de stock :

![](.gitbook/assets/image%20%286%29%20%281%29.png)

Les colonnes représentent :

* **Type de frais**: le type de frais d'approche à appliquer. On peut les configurer dans le menu _"Frais d'approche &gt; Types de frais d'approche"_, voir en définir des "par défaut" \(qui seront présents automatiquement dans tous les nouveaux objets _'Distribution de frais d'approche'_\) :
* **Méthode de calcul** : La méthode de répartition de ce frais d'approche \(défini dans les caractéristiques du _'Type de frais d'approche'_\) parmi les _Mouvements de réception_ de notre objet _'Distribution de frais d'approche'_. On peut répartir ce frais d'approche de différentes manières : proportionnellement au nombre d'articles de chaque Mouvement, au prix de chaque article, au prix total du Mouvement, de manière égale sur chaque Mouvement, etc...
* **Montant du frais** : La valeur totale du frais d'approche à répartir sur les différents _'Mouvements de réception'_.
* **Mouvements concernés** : Les _'Mouvements de réception'_  correspondant aux articles auxquels on souhaitent ajouter ce frais d'approche \(le frais sera réparti sur tous les Mouvements si le champs est laissé vide\)
* **Ligne de facture fournisseur** : La Ligne de facture associée à cette dépense de frais d'approche, à ne pas confondre avec les lignes de la Facture d'achat des articles achetés auxquels on ajoute ces frais d'approche.

![Configuration des &apos;Types de Frais d&apos;approche&apos; via le menu du m&#xEA;me nom](.gitbook/assets/image%20%2816%29.png)

{% hint style="info" %}
Tout comme les _'Opérations'_ de stock, les _'Factures'_ sont des objets Odoo généralement associés à des _'Bons de Commande'_ et composés de sous-objets appelés _'Lignes de facture'_.

Généralement, si une _'Facture'_ est associée à un '_Bon de Commande',_ une _'Ligne de facture'_ sera associée à une ligne de ce _'Bon de Commande'_. La _'Ligne de facture'_ contiendra alors les informations relatives à la sortie d'argent liée à l'achat d'un type d'Article particulier.

Voilà pourquoi il faut lier un frais d'approche à une _'Ligne de facture'_ et non une _'Facture'_ complète. Le fournisseur ayant réalisé le service du frais d'approche peut avoir émis une facture incluant différents services dont un seul correspond à la dépense su frais.
{% endhint %}

### 3. Calcul du nouveau prix de revient

En cliquant sur _"Calculer le prix d'acquisition"_ on calcule le prix de revient des articles présents dans notre objet _'Distribution de Frais d'approche'_ en cours __. Il faut ensuite cliquer sur _"Mettre à jour le prix de revient"_ pour actualiser le prix de revient \(pondéré\) des articles en question.

![](.gitbook/assets/image%20%288%29.png)

Il faut bien noter que la valeur du _'Prix d'Acquisition'_ inscrite dans l'onglet _"Mouvements de réception"_  correspond à la valeur `PrixAcquisition`  de notre calcul incluant le prix d'achat et les frais d'approches \(73,06€ dans notre exemple\). À ne pas confondre avec le nouveau prix de revient \(pondéré\) de l'article qui sera calculé et enregistré en cliquant sur _"Mettre à jour le prix de revient"_ \(28,32€ dans notre exemple\) :

![](.gitbook/assets/image%20%2817%29.png)

## Configuration

### Bouton "Enregistrer les Frais d'approche"

Le bouton _"Enregistrer les Frais d'approche"_  est disponible non seulement sur le bon de commande lié aux articles dont on veut actualiser le prix de revient mais aussi sur le bon de livraison lié à cet achat. Cette option est disponible sur les deux objets à partir du moment où le bon de livraison est dans l'état "Prêt" ou "Terminé".

En revanche, si on crée un bon de livraison sans qu'il soit lié à un bon de commande, l'option ne sera évidemment pas disponible.

### Option 'Doit être lié à des Frais d'approche'

L'option _'Doit être lié à des Frais d'approche'_ d'un Bon de commande est automatiquement pré-remplie \(bien que restant éditable\) lorsqu'on choisit le Fournisseur, suivant l'information donnée par le champ _'Articles liés à des Frais d'approche'_ de la fiche du Fournisseur :

![](.gitbook/assets/image%20%2810%29%20%281%29.png)

### Condition d'actualisation du Prix de revient

Le prix de revient ne sera réellement actualisé sur un produit que si la Catégorie du Produit a une méthode de calcul de coût qui est _'Coût moyen \(AVCO\)'_ :

![](.gitbook/assets/image%20%2810%29%20%282%29.png)

Si la méthode sélectionner est _'Prix standard'_ ou _'First in first out \(FIFO\)'_ le prix de revient ne sera pas actualisé et l'action _"Mettre à jour le prix de revient"_ n'aura aucun effet.

### Lier une Facture de frais à un Frais d'approche

On peut créer un Frais d'approche à partir de sa Ligne de Facture de fournisseur correspondante en cliquant sur _"Importer une ligne de facture"_ puis en sélectionnant le fournisseur, la facture de ce fournisseur, la ligne de cette facture, et le type de frais que l'on veut ajouter.

![](.gitbook/assets/image%20%2824%29.png)

Mais il est aussi possible d'ajouter un frais en laissant la colonne _'Ligne de facture fournisseur'_ vide tant que la facture correspondante au frais d'approche n'est pas émise et en le renseignant par la suite si nécessaire.

On pourra retrouver l'information de ce lien entre une certaine Ligne de facture et un Frais d'approche dans l'onglet _'Frais d'approche'_ de la Facture de la Ligne de facture correspondante :

![](.gitbook/assets/image%20%2825%29.png)





