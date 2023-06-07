# Guide de conversion et configuration avec Pandoc

- [Pandoc](https://github.com/jgm/pandoc) est un logiciel libre de conversion de documents numériques en ligne de commande.

On souhaite dans notre cas effectuer des conversions **md** -> **pdf** et **md** -> **html**. Pour cela, on doit tout d'abord installer le paquetage [**LATEX**](https://packages.debian.org/sid/texlive-latex-recommended), il s'agit d'un langage/système de composition de documents destiné à faciliter l'utilisation du « processeur de texte » [**TeX**](https://fr.wikipedia.org/wiki/TeX) *(logiciel libre de composition de documents)*.

On l'installe en utilisant cette commande : 

```sh
sudo apt install texlive-latex-recommended
```

Une fois fait, nous pouvons sans problèmes effectuer nos conversions, commençons par le **pdf** :

```sh
pandoc -f markdown -t pdf Rapport_FINAL.md -o Rapport_FINAL.pdf --number-sections --toc --metadata title="Rapport S2.03" -V colorlinks=true -V linkcolor=cyan -V urlcolor=cyan
```

Pour finir par le **html** :

```sh
pandoc -f markdown -t html Rapport_FINAL.md -o Rapport_FINAL.html --number-sections --css=css/style.css --standalone --toc --metadata title="Rapport S2.03"
```

Chaque option dans ces commandes ont leur importance :

- `-f markdown` : **f** signifie **from**, soit le format initial.
- `-t html/pdf` : **t** signifie **to**, soit le format d'arrivée.
- `-o result.html/.pdf` **o** signifie **output**, soit le fichier de destination.
- `--number-sections` : sert à numéroter automatiquement chacune des sections.
- `--css=css/style.css` : lier un fichier css à notre résultat html.
- `--standalone` ou `-s` : permet de donner un fichier html complet (un fichier HTML valide comprenant <head> et <body>),
- `--toc` : **toc** signifie **table of contents**, permet d'ajouter automatiquement une table des matières.
- `--metadata` : permet d'ajouter des paramètres en plus à nos conversions, par exemple :
    - `title="Rapport S2.03"` : titrer notre document, et l'afficher tout en haut de celui-ci.
- `-V` : **V** signifie **variable**, comme son nom l'indique permet de modifier la valeurs de certaines variables comme :
    - `colorlinks=true` : pour activer la coloration des liens cliquables.