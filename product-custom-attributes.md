---
description: Créer des champs à volonté... sans surcharger la base de donnée !
---

# Product Custom Attributes

Modules développés par Akrétion : [https://github.com/shopinvader/odoo-pim/pull/6](https://github.com/shopinvader/odoo-pim/pull/6)

## Objectif

Pouvoir créer n'importe quel type de **Champs personnalisable** d'Articles \(_Attributes_ en anglais\) et les associer à certaines **Familles d'Article** __\(_Atribute Set_\).

En choisissant la Famille d'un article, on fait apparaître les Champs personnalisables de cet article. Ainsi un article de la Famille des 'Tables' pourra avoir des champs de dimension \(longueur, largeur, hauteur...\) qui n'apparaîtront pas dans les articles de la famille des 'Ordinateurs' :

![Liste des &apos;Attributes&apos; de la famille &apos;Computer&apos;](.gitbook/assets/image%20%2827%29.png)

Ces Champs personnalisables sont regroupés dans des **Catégories de champs** \(_Attribute Group_\) comme _Technical_ et _General_ dans notre exemple.

Un **Champ personnalisable** \(_Attribute_\) peut apparaître dans les **plusieurs Familles** d'articles \(_Attribute Set_\) mais il ne peut être que dans **une seule Catégorie de champs** \(_Attribute Group_\). On peut consulter la liste des différents Champs, Catégories de champs et Familles d'articles dans le Menu _Sales_ &gt; _Configuration_ :

![](.gitbook/assets/image%20%2819%29.png)

{% hint style="info" %}
Le module permet théoriquement la création de Champs pour d'autres objets Odoo que les Articles. Mais pour l'instant seuls les Champs personnalisables d'Articles peuvent être affichés.
{% endhint %}

## Usage

Dans le menu _Sale_ &gt; _Configuration_ &gt; _Attributes Set_, on crée une **Famille d'Articles** :

![](.gitbook/assets/image%20%2834%29.png)

...à laquelle on associe des Champs personnalisables :

![](.gitbook/assets/image%20%2840%29.png)

Chaque Champ a de nombreux paramètres dont :

* son **Type**, à choisir parmi :
  * Char _\(Texte en ligne\)_
  * Text _\(Paragraphe\)_
  * Select _\(menu déroulant d'options à définir\)_
  * Multiselect _\(choix multiple d'options à définir\)_
  * Boolean _\(case à cocher\)_
  * Date
  * Datetime _\(Date avec heure\)_
  * Binary _\(photo, fichier pdf...\)_
  * Float _\(nombre à virgule\)_
  * Integer _\(nombre entier\)_
* Sa **Séquence** : l'ordre dans lequel il sera présenté **dans sa Catégorie \(**_**Attribute Group**_**\)**

   par rapport aux autres Champs.

* **JSON Field** : Tous les champs qui ont cette case cochée auront leurs valeurs regroupées au même endroit de la base de donnée sous la forme d'un gros fichier au [format JSON](https://fr.wikipedia.org/wiki/JavaScript_Object_Notation). Dans le cas de milliers d'Articles et de centaines de champs différents cela permet d'**accéder aux valeurs des champs en un temps record** en économisant le nombre de colonnes des Articles dans la base de donnée.

{% hint style="info" %}
Les Catégories de Champs ont aussi un paramètre "_Séquence_" à définir. Cela donnera leur **ordre d'apparition dans l'onglet "**_**Attribute**_**"** de la fiche de l'Article \(pour les Articles qui ont des _Attributes_ de plusieurs Catégories différentes\).
{% endhint %}









