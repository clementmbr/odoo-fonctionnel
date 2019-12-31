---
description: >-
  Module d'inclusion des frais d'approche dans le calcul du prix de revient d'un
  produit.
---

# Purchase Landed Costs

## Objectif

Le module ‘_Purchase Landed Costs_’ permet d’actualiser le prix de revient des produits en incluant tous types de frais d’approches \(transport, douane, frais de paiement…\) au prix d’achat d’origine \(de la facture du fournisseur\).

Le bouton pour accéder à l’historique du prix de revient d'une produit se trouve dans l’onglet _“Information Générale”_ de la fiche produit :

![](https://lh5.googleusercontent.com/s35se7KM7lYaLYK3Ba2vmoMVeCLABfWCRhbwu541Da060zuxbOzo3NFC-PqLUzmmQtsU2pxwYZOsjh6xq7DvuWMGEDKd4WffAmN1KNTRHfSBdKUdYBj-A_E3ledrFms0kqb4Zt9V)

Il permet d'afficher un historique de ce type :

![](https://lh4.googleusercontent.com/x5Lr7Chklez0qo-UpWSRgqfrbbcd0lT6HoH19i6DZ_Y1pzXHAvz-r5QBDx11rrlEhQjBT6g4YG8HfYmUrp4eOZolmF_N2ptiN0_UyF-0B-aXLdR0Is6FCQDiscxBELQ0jsW9aVRq)

Le nouveau prix de revient sera calculé par une moyenne prenant en compte :

* l'ancien prix de revient du produit
* la quantité en stock avant l'arrivage
* la quantité de l'arrivage
* le prix d'achat incluant les frais d'approches de l'arrivage



$$
Nouveau Prix = \frac{(Nouveau Stock*Ancien Prix ) + Arrivage*(Prix Arrivage - Ancien Prix))}{Nouveau Stock}
$$



