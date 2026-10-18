![CalcFlow](banner.png)

# CalcFlow

Calculatrice à feuille libre, dans l'esprit de Tydlig, à l'allure de la Calculatrice d'Apple. Chaque résultat devient une cellule que l'on réutilise : les calculs restent liés et se mettent à jour d'eux-mêmes.

**Démo :** https://ninjathune-human.github.io/calcflow/

## L'essentiel

- **Feuille libre** : on pose un calcul où l'on veut, le résultat apparaît avec `=`.
- **Cellules liées** : on glisse un résultat dans un autre calcul. Les liens prennent la couleur de la cellule ; modifier la source recalcule toute la chaîne, chiffre après chiffre.
- **Calcul entre cellules** : on sélectionne une cellule, on appuie sur une opération, on approche une seconde cellule, puis `=`.
- **Devises et cryptos** : un appui long sur une cellule crée sa conversion, liée à la source. Taux en direct, avec un jeu de taux intégré hors ligne.
- **Partout** : clavier sur 40 % de l'écran sur iPhone et sur un tiers sur iPad, fonctions scientifiques dépliables (touche fx), clavier à droite en paysage, clavier physique sur ordinateur. Tactile, stylet et souris.
- **Écriture manuscrite** : le crayon de la barre active l'écriture au doigt, au stylet ou à la souris. Le crayon passe au bleu ; on écrit sans limite de temps, et `=` reconnaît puis résout le calcul, là où l'on a écrit. La lecture se fait dans la page, sans connexion : un réseau de neurones reconnaît chaque symbole, un second décide quels traits forment un même symbole (tous deux entraînés sur l'encre réelle de plusieurs centaines de scripteurs, jeu CROHME), puis la mise en page (racines, fractions, exposants) est analysée et la lecture la plus probable qui forme un calcul valide est retenue. Sous le résultat, deux autres lectures possibles s'affichent quelques secondes : un toucher remplace le calcul. Si la lecture locale échoue, Google prend le relais (connexion requise). Racines (√ avec vinculum, indice 3 pour la racine cubique), fractions à barre, exposants en position haute, `sin`, `cos`, `tan`, `ln`, `log`, `π`, `%` et `!` s'écrivent à la main ; une virgule décimale est un petit trait bas entre deux chiffres. En mode écriture, un doigt posé sur un résultat le déplace comme d'habitude (le stylet continue d'écrire). Une écriture qui commence par une opération (`× 3`), posée à droite de la ligne en cours (un résultat déplacé par exemple), en est la suite. Un trait rectiligne vers 45° (« / ») est toujours une division.
- **Règle de trois** : en mode écriture, dessiner une grande croix, écrire un nombre dans trois de ses cases et un `x` dans la quatrième (ou la laisser vide), puis `=`. Les produits en croix étant égaux (haut-gauche × bas-droite = haut-droite × bas-gauche), la valeur de x est calculée et le calcul s'écrit sur la feuille, par exemple `12 × 30 ÷ 4 = 90`.
- **Division posée** : en mode écriture, poser la division à la française (le dividende, la potence, le diviseur au-dessus du trait horizontal), puis `=`. Le calcul s'écrit sur la feuille et un volet en détaille la résolution : la potence complète (soustractions en vert, chiffres abaissés fléchés, quotient en orange, reste), la table du diviseur et chaque étape expliquée, du premier dividende partiel à la vérification (`16 × 395 + 4 = 6324`). Toucher une étape l'éclaire sur la potence. Division entière (quotient et reste) ou décimale (on abaisse des 0 après la virgule) ; un diviseur décimal est d'abord rendu entier.
- **Entraînement de l'écriture** : en mode écriture, le bouton « A » ouvre la zone d'entraînement. On choisit un symbole (chiffres, signes, lettres des fonctions) ou on suit le parcours guidé, on l'écrit entre les deux lignes ; il est ajouté 1,4 s après le dernier trait, et la zone indique si le réseau l'aurait reconnu. Les exemples restent dans le navigateur (`localStorage`) ; à la lecture, l'exemple le plus proche (empreinte calculée par le réseau) renforce sa classe : utile pour une forme personnelle (un 4 ouvert, un 1 à longue attaque). L'interrupteur « Mon écriture » coupe ce renfort ; appui long sur le crayon : le HUD indique les symboles lus et leurs probabilités.
- **Sauvegarde automatique** dans le navigateur, annulation pas à pas.

## Gestes

| Geste | Effet |
| --- | --- |
| Toucher la feuille | Nouveau calcul à cet endroit |
| Toucher une cellule | Sélection |
| Glisser une cellule | Réutiliser la valeur, avec un lien |
| Appui long sur une cellule | Conversion en devise ou en crypto |
| Cellule sélectionnée, puis une opération | Calcul qui part de cette cellule |
| Nombre sélectionné, puis ⌫ | Modifier le nombre dans sa cellule |
| Résultat sélectionné, puis ⌫ | Efface le résultat ; `=` refait le calcul |
| ⌫ : toucher, maintenir, glisser à gauche | Effacer un caractère, la ligne, toute la feuille |

## Utilisation

Un seul fichier, `index.html`, sans installation ni dépendance : il s'ouvre dans n'importe quel navigateur.

Mise en ligne avec GitHub Pages : **Settings › Pages › Deploy from a branch**, branche `main`, dossier `/ (root)`.

Sur iPhone et iPad, **Partager › Sur l'écran d'accueil** l'ouvre en plein écran, comme une app.

## Technique

HTML, CSS et JavaScript natifs. Police Inter (Google Fonts, repli sur la police système). Taux de change : API publique Coinbase.
Reconnaissance de l'écriture : deux petits réseaux de neurones (reconnaissance des symboles, regroupement des traits) exécutés dans la page en JavaScript, poids intégrés au fichier.

## Crédits

Les réseaux de lecture de l'écriture ont été entraînés sur le jeu de données **CROHME** (Competition on Recognition of Online Handwritten Mathematical Expressions, 2011-2013, © Université de Nantes / CNRS et contributeurs : University of Sao Paulo, University of Waterloo, KAIST, Czech Technical University), distribué sous licence [CC BY-NC-SA 3.0](https://creativecommons.org/licenses/by-nc-sa/3.0/). Les poids de ces réseaux, intégrés à `index.html`, sont diffusés sous la même licence : usage non commercial, avec attribution.

H. Mouchère, C. Viard-Gaudin, R. Zanibbi, U. Garain, D. H. Kim, J. H. Kim, *ICDAR 2013 CROHME: Third International Competition on Recognition of Online Handwritten Mathematical Expressions*, ICDAR 2013.
