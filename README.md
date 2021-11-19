## Fichiers dans ce repo

  - Deux fichiers `.tex` minimales pour exemplifier l'usage de `biblatex` avec deux formats différents ("numeric" et APA)
  - Un fichier `.bib` minimale appelé depuis les fichier `.tex`, exporté depuis Zotero
  - Deux fichiers `.pdf` compilés en utilisant les fichier `.tex` dans mon ordinateur personnel

## Outils et environnement utilisés

  - Distribution LaTeX [texlive](https://packages.debian.org/stretch/texlive-full) (spécifiquement, `texlive-full`) pour Debian Linux
    + Important : elle contient le package `biblatex` utilisé dans mon exemple
  - Éditeur de texte [TeXstudio](https://www.texstudio.org/)
    + Compilation faite avec XeLaTeX
  - Logiciel [Zotero](https://www.zotero.org/download/)
    + Complément [Better BibTeX for Zotero](https://retorque.re/zotero-better-bibtex/) : pour exporter une selection dans Zotero au format `.bib` utilisable avec LaTeX + biblatex ; configuration personnelle du format des *citation keys* : `[auth.etal:lower][year]`
    + Une compte personnelle Zotero : pour synchroniser ma libraire Zotero dans tous mes appareils
  - Complément [Zotero Connector](https://www.zotero.org/download/) pour Firefox

## Workflow

1. Trouver des textes académiques potentiellement utilisables sur internet

2. Ouvrir Zotero (logiciel) et utiliser le complément Zotero Connector du navigateur web pour envoyer le texte à la librairie personnelle Zotero
  - N.B. le logiciel Zotero doit être ouvert pour que le complément (au moins celui de Firefox) fonctionne

3. Nettoyer l'entrée dans la librairie Zotero.
Zotero Connector marche très bien mais il n'est pas infaillible, il faut s'assurer que les champs (auteur, année, etc.) de chaque entrée soient correctes

4. Exporter une selection della libraire Zotero comme un fichier `.bib`:\
  4.1 Dans le logiciel Zotero, sélectionner (visuellement, avec la touche "shift" ou "ctrl") les textes à exporter\
  4.2 Faire clic droit et appuyer sur la commande `Export items…`\
  4.3 Choisir `Better BibLaTeX` comme format, sans aucune "Translator Options"\
  4.4 Definir l'emplacement et nom du fichier `.bib`

5. Appeler le fichier `.bib` dans le préambule du fichier `.tex` et compiler le document :\
  5.1 Ajouter `\usepackage[<options>]{biblatex}` et les packages recommandés par biblatex avant appeler le `.bib` :
```tex
\usepackage{csquotes, xpatch}  % Recommandé par biblatex
\usepackage[backend=biber,bibstyle=numeric-verb,citestyle=numeric,sorting=none]{biblatex}
\addbibresource{bibliography.bib}
```
  5.2 Et imprimer la section de références en utilisant la commande `\printbibliography[<options>]` dans le corps du texte :
```tex
\begin{document}
```
⋮
```tex
\printbibliography
\end{document}
```
  - N.B. des fois il faut ajouter des options ou des autres commandes pour manipuler la compilation finale.
Par ex., si on ne fait pas référence à un des textes du fichier `.bib`, ce texte ne sera pas imprimé avec `\printbibliography`. Pour changer cela on ajoute la commande `\nocite{*}` avant dans le corps pour forcer l'apparition de tous les textes du fichier `.bib` dans la section des références.


6. Consulter [TeX Stack Exchange](https://tex.stackexchange.com/) si quelque chose ne marche pas !
