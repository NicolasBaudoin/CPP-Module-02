# CPP-Module-02

![C++](https://img.shields.io/badge/C++-98-00599C?style=flat-square&logo=cplusplus&logoColor=white)
![Top language](https://img.shields.io/github/languages/top/NicolasBaudoin/CPP-Module-02?style=flat-square)
![Last commit](https://img.shields.io/github/last-commit/NicolasBaudoin/CPP-Module-02?style=flat-square)

> Ad-hoc polymorphism, operator overloading and the Orthodox Canonical class form.

Troisième module du parcours C++ à 42. Nombres à virgule fixe (`Fixed`) et surcharge d'opérateurs. Tout le code suit la norme **C++98**.

---

- [Règles générales](#règles-générales)
- [Nouvelle règle — Orthodox Canonical Form](#nouvelle-règle--orthodox-canonical-form)
- [Exercice 00 — My First Class in Orthodox Canonical Form](#exercice-00--my-first-class-in-orthodox-canonical-form)
- [Exercice 01 — Towards a more useful fixed-point number class](#exercice-01--towards-a-more-useful-fixed-point-number-class)
- [Exercice 02 — Now we're talking](#exercice-02--now-were-talking)
- [Exercice 03 — BSP](#exercice-03--bsp)
- [Rendu et évaluation](#rendu-et-évaluation)

## Règles générales

- Compiler avec `c++` et les flags `-Wall -Wextra -Werror`, compatible `-std=c++98`
- Dossiers d'exercices : `ex00`, `ex01`, ..., `exn`
- STL interdite avant les Modules 08/09 ; `using namespace` et `friend` interdits

## Nouvelle règle — Orthodox Canonical Form

**À partir de ce module et jusqu'au Module 09**, toute classe doit implémenter les 4 fonctions membres canoniques (sauf mention contraire) :

- Constructeur par défaut
- Constructeur par copie
- Opérateur d'affectation par copie
- Destructeur

Header (`.hpp`) = déclaration, source (`.cpp`) = implémentation.

---

## Exercice 00 — My First Class in Orthodox Canonical Form

| | |
|---|---|
| **Dossier** | `ex00/` |
| **Fichiers à rendre** | `Makefile`, `main.cpp`, `Fixed.{h, hpp}`, `Fixed.cpp` |
| **Interdit** | Aucun |

Classe `Fixed` représentant un **nombre à virgule fixe** :

- Privé : un `int` pour la valeur brute, un `static const int` = **8** pour le nombre de bits fractionnaires
- Public : constructeur par défaut (valeur 0), constructeur par copie, opérateur d'affectation, destructeur
- `int getRawBits(void) const;` / `void setRawBits(int const raw);`

Chaque fonction canonique doit afficher un message identifiant son appel.

---

## Exercice 01 — Towards a more useful fixed-point number class

| | |
|---|---|
| **Dossier** | `ex01/` |
| **Fichiers à rendre** | `Makefile`, `main.cpp`, `Fixed.{h, hpp}`, `Fixed.cpp` |
| **Autorisé** | `roundf` (`<cmath>`) |

Ajouter à `Fixed` :

- Constructeur depuis un `int` constant (conversion en valeur fixe, 8 bits fractionnaires)
- Constructeur depuis un `float` constant (idem)
- `float toFloat(void) const;` / `int toInt(void) const;`
- Surcharge de l'opérateur d'insertion `<<` (affiche la représentation flottante)

---

## Exercice 02 — Now we're talking

| | |
|---|---|
| **Dossier** | `ex02/` |
| **Fichiers à rendre** | `Makefile`, `main.cpp`, `Fixed.{h, hpp}`, `Fixed.cpp` |
| **Autorisé** | `roundf` (`<cmath>`) |

Ajouter à `Fixed` :

- Les **6 opérateurs de comparaison** : `>`, `<`, `>=`, `<=`, `==`, `!=`
- Les **4 opérateurs arithmétiques** : `+`, `-`, `*`, `/`
- Les **4 opérateurs d'incrément/décrément** (pré/post), pas de la plus petite valeur représentable ε
- 4 fonctions statiques : `min`/`max`, chacune en version non-const et const (références)

> Une division par 0 peut légitimement faire planter le programme.

---

## Exercice 03 — BSP

| | |
|---|---|
| **Dossier** | `ex03/` |
| **Fichiers à rendre** | `Makefile`, `main.cpp`, `Fixed.{h, hpp}`, `Fixed.cpp`, `Point.{h, hpp}`, `Point.cpp`, `bsp.cpp` |
| **Autorisé** | `roundf` (`<cmath>`) |
| **Optionnel** | Le module passe sans cet exercice |

Classe `Point` en Orthodox Canonical Form (2 attributs `Fixed const x, y`), puis :

```cpp
bool bsp( Point const a, Point const b, Point const c, Point const point );
```

Indique si `point` est **strictement à l'intérieur** du triangle `abc` (un point sur un bord ou un sommet renvoie `false`). BSP = Binary Space Partitioning.

---

## Rendu et évaluation

- Rendu sur le dépôt Git ; seul le contenu du repo est évalué
- Une petite modification peut être demandée en soutenance pour vérifier la compréhension réelle du code
