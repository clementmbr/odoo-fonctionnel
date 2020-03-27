---
description: Créer des champs à volonté... sans surcharger la base de donnée !
---

# Product Custom Attributes

Modules développés par Akrétion : [https://github.com/shopinvader/odoo-pim/pull/6](https://github.com/shopinvader/odoo-pim/pull/6)

## Objectif

Pouvoir créer n'importe quel type de **Champs personnalisable** d'Articles \(_Attribute_ en anglais\) et les associer à certaines **Familles d'Article** __\(_Atribute Set_\).

En choisissant la Famille d'un article, on fait apparaître les Champs personnalisables de cet article. Ainsi un article de la Famille des Tables pourra avoir des champs de dimension \(longueur, largeur, hauteur...\) qui n'apparaîtront pas dans les articles de la famille des Ordinateurs :

![](.gitbook/assets/image.png)

![](.gitbook/assets/image%20%2815%29.png)

Ces Champs personnalisables peuvent être regroupés dans des **Catégories de champs** \(_Attribute Group_\) qui permettront de regrouper les champs à afficher dans des sous-onglets de l'onglet Attributes.

Un **Champ personnalisable** \(_Attribute_\) peut apparaître dans les **plusieurs Familles** d'articles \(_Attribute Set_\) mais il ne peut être que dans **une seule Catégorie de champs** \(_Attribute Group_\). On peut consulter la liste des différents Champs, Catégories de champs et Familles d'articles dans le Menu _Sales_ &gt; _Configuration_ :

![](.gitbook/assets/image%20%2819%29.png)

{% hint style="info" %}
Le module permet théoriquement la création de Champs pour d'autres objets Odoo que les Articles. Mais pour l'instant seuls les Champs personnalisables d'Articles sont affichés dans les fiches d'Articles.
{% endhint %}

## Usage

Dans le menu Sale &gt; Configuration &gt; Attributes Set, on crée une famille d'Articles :

![](.gitbook/assets/image%20%2834%29.png)

...à laquelle on associe des Champs personnalisables. Chaque Champ a de nombreux paramètres dont :

![](.gitbook/assets/image%20%2839%29.png)

* son Type, à choisir parmi :
* Char
* Text
* Select
* Multiselect
* Boolean
* Date
* Datetime
* Binary
* Float
* Integer







