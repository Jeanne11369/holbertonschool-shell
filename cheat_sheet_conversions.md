# Cheat Sheet : Conversions Binaire, Décimal & Hexadécimal (Sans aspirine)

Petit récapitulatif de notre session ! Comme promis, on oublie les divisions euclidiennes à rallonge qu'on apprend à l'école. En tant que dev, on veut aller vite et surtout ne pas se tromper. 

Voici la méthode des grilles. Gardez toujours ce principe en tête : **on n'a besoin de savoir faire que de simples additions.**

---

## 1. Le Binaire et le Décimal : Le tableau magique

La seule chose que vous devez retenir par cœur, c'est la suite des puissances de 2 pour un octet (8 bits). Dessinez toujours ce tableau sur votre brouillon avant de commencer :

| 128 | 64 | 32 | 16 | 8 | 4 | 2 | 1 |
| :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| | | | | | | | |

### Cas A : Du Binaire vers le Décimal (L'Addition)
**Exemple :** On veut convertir `01010110`.
Placez simplement votre nombre binaire dans le tableau, de gauche à droite :

| 128 | 64 | 32 | 16 | 8 | 4 | 2 | 1 |
| :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| 0 | **1** | 0 | **1** | 0 | **1** | **1** | 0 |

**La règle :** Additionnez les en-têtes des colonnes où il y a un "1".
Calcul : `64 + 16 + 4 + 2 = 86`. 
C'est tout. 
> **💡 Le tips de survie :** Regardez la dernière colonne (le 1). S'il y a un 0, le résultat sera forcément pair. S'il y a un 1, il sera impair. Ça permet d'éviter les erreurs bêtes !

### Cas B : Du Décimal vers le Binaire (Le jeu du "Est-ce que ça rentre ?")
**Exemple :** On veut convertir `100` en binaire.
On part de la gauche du tableau (la plus grande valeur) et on se pose la question : est-ce que ça rentre ?

1. **128** rentre-t-il dans 100 ? **Non.** On met `0`.
2. **64** rentre-t-il dans 100 ? **Oui.** On met `1`. Il nous reste `100 - 64 = 36` à placer.
3. **32** rentre-t-il dans 36 ? **Oui.** On met `1`. Il nous reste `36 - 32 = 4` à placer.
4. **16** rentre-t-il dans 4 ? **Non.** On met `0`.
5. **8** rentre-t-il dans 4 ? **Non.** On met `0`.
6. **4** rentre-t-il dans 4 ? **Oui.** On met `1`. Il nous reste `0`.
7. Le reste ne rentre plus, on met des `0`.

**Résultat pas à pas :**

| 128 | 64 | 32 | 16 | 8 | 4 | 2 | 1 | Reste à placer |
| :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :--- |
| **0** | | | | | | | | 100 |
| 0 | **1** | | | | | | | 100 - 64 = 36 |
| 0 | 1 | **1** | | | | | | 36 - 32 = 4 |
| 0 | 1 | 1 | **0** | | | | | 4 |
| 0 | 1 | 1 | 0 | **0** | | | | 4 |
| 0 | 1 | 1 | 0 | 0 | **1** | | | 4 - 4 = 0 |
| 0 | 1 | 1 | 0 | 0 | 1 | **0** | **0** | 0 |

Votre binaire est : `01100100`.

---

## 2. Le pont magique : Hexadécimal & Binaire

Pourquoi l'Hexa (Base 16) ? Parce que 16, c'est 2 à la puissance 4. Cela signifie qu'**un caractère hexadécimal correspond EXACTEMENT à 4 bits** (un "nibble").

Pour compter en hexa, après le 9, on utilise l'alphabet :
* `A` = 10
* `B` = 11
* `C` = 12
* `D` = 13
* `E` = 14
* `F` = 15

On utilise un **mini-tableau de 4 cases** :

| 8 | 4 | 2 | 1 |
| :---: | :---: | :---: | :---: |

### Cas A : Du Binaire vers l'Hexa (La technique de la découpe)
**Exemple :** On veut convertir `11011010`.
On coupe ce gros bloc en deux petits paquets de 4 bits : `1101` et `1010`. On les passe dans notre mini-tableau.

**Premier paquet (`1101`) :**
| 8 | 4 | 2 | 1 |
| :---: | :---: | :---: | :---: |
| 1 | 1 | 0 | 1 |

*Calcul :* `8 + 4 + 1 = 13`. Dans notre alphabet, 13 correspond à **D**.

**Deuxième paquet (`1010`) :**
| 8 | 4 | 2 | 1 |
| :---: | :---: | :---: | :---: |
| 1 | 0 | 1 | 0 |

*Calcul :* `8 + 2 = 10`. Dans notre alphabet, 10 correspond à **A**.

**Résultat final :** `11011010` en binaire s'écrit `DA` en hexadécimal.

### Cas B : De l'Hexa vers le Binaire (L'inverse)
**Exemple :** La couleur web `#3F`.
On traduit chaque lettre/chiffre en un paquet de 4 bits.

* Le `3` : Comment faire 3 avec `8, 4, 2, 1` ? C'est `2 + 1`. Donc **`0011`**.
* Le `F` : C'est le max (15). Pour faire 15, on prend tout : `8 + 4 + 2 + 1`. Donc **`1111`**.

**Résultat final :** `00111111`.

---

## 3. La Règle d'Or : Décimal ↔ Hexadécimal

**Ne faites JAMAIS une conversion directe entre Décimal et Hexa de tête.**
Faire des multiplications ou divisions par 16 sur un brouillon, c'est l'erreur garantie.

La technique infaillible ? **Utilisez le binaire comme un pont.**

**Exemple :** Convertir `150` (Décimal) en Hexadécimal.
1. **Décimal -> Binaire :** On passe `150` dans le grand tableau de 8 cases.
   * *150 = 128 + 16 + 4 + 2* -> Ce qui donne `10010110`.
2. **On coupe en deux :** `1001` et `0110`.
3. **Binaire -> Hexa :** On passe les morceaux dans le mini-tableau.
   * `1001` = 8 + 1 = **9**
   * `0110` = 4 + 2 = **6**
4. **Résultat :** `96` en hexa.

C'est implacable, visuel, et ça vous évitera de chercher des bugs pendant des heures !