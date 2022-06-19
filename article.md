---
title: |
  "Python : Generators and Iterators Protocol"
date: June, 2022
lang: fr-FR
urlcolor: blue
geometry: "left=2.5cm,right=2.5cm,top=3cm,bottom=3cm"
documentclass: article
fontfamily: Alegreya
header-includes: |
    \usepackage{fancyhdr}
    \pagestyle{fancy}
    \fancyhf{}
    \rhead{Dakar Institute of Technology}
    \lhead{Mamadou Seybane KEBE}
    \rfoot{Page \thepage}
    \hypersetup{pdftex,
            pdfauthor={Mamadou Seybane KEBE},
            pdftitle={Python : Generators and Iterators Protocol},
            pdfsubject={Python : Generators and Iterators Protocol},
            pdfkeywords={Python, Programming, Generator, Iterator},
            pdfproducer={Emacs, Pandoc, Latex, Markdown},
            pdfcreator={Emacs, Pandoc, Latex, Markdown}}
    
---

# Introduction

Dans la vie des être humain les tâches répétitives sont exécutés quotidiennement. Dans l’informatique pour faciliter la vie, les applications développées dans ce sens implémentes beaucoup de tâches répétitives. Python qui est l’un des langages de programmation les plus populaire aujourd’hui implémente également ce principe de tâches réplétives appelé itération.\
En programmation python ou tout autres langages de programmation boucler ou traverser une séquence est l’aspect le plus commun. Les boucle for et while dans python peuvent traiter presque toutes les tâches répétitives exécuter par les programmes. Itérer sur une séquence est tellement utilisé dans que python offre des capacités extras pour faciliter son utilisation et le rendre plus performant et efficient.\
Certains de ces capacités pour traiter les séquences sont les itérateurs et les générateurs. Cet article va disséquer les itérateurs et générateurs.

# Itérable et Itérateurs en Python

Un itérateur est un objet qui contient un nombre comptable d’élément et il est utilisé pour itérer les objets comme les listes, les tuples, les strings, etc. les itérateurs sont implémentés comme classe et une variable locale pour itérer n’est pas requise. Ils utilisent la «lazy evaluation » où l’évaluation de l’expression sera maintenue et gardée en mémoire jusqu’à ce qu’il soit rappelé spécifiquement pour éviter l’évaluation répétitive.\
Pour être considéré comme itérable, l’objet doit implémenter les méthodes __iter__() et __next__().\
\
Supposons que nous avons :


```python

Name = "Mamadou"

print(type(Name))
print(dir)
```
```output
['__add__', '__class__', '__contains__', '__delattr__', '__dir__', '__doc__', '__eq__', '__format__', '__ge__', '__getattribute__', '__getitem__', '__getnewargs__', '__gt__', '__hash__', '__init__', '__init_subclass__', '__iter__', '__le__', '__len__', '__lt__', '__mod__', '__mul__', '__ne__', '__new__', '__reduce__', '__reduce_ex__', '__repr__', '__rmod__', '__rmul__', '__setattr__', '__sizeof__', '__str__', '__subclasshook__', 'capitalize', 'casefold', 'center', 'count', 'encode', 'endswith', 'expandtabs', 'find', 'format', 'format_map', 'index', 'isalnum', 'isalpha', 'isascii', 'isdecimal', 'isdigit', 'isidentifier', 'islower', 'isnumeric', 'isprintable', 'isspace', 'istitle', 'isupper', 'join', 'ljust', 'lower', 'lstrip', 'maketrans', 'partition', 'removeprefix', 'removesuffix', 'replace', 'rfind', 'rindex', 'rjust', 'rpartition', 'rsplit', 'rstrip', 'split', 'splitlines', 'startswith', 'strip', 'swapcase', 'title', 'translate', 'upper', 'zfill']
```
On constate dans le resultat du code que la methode __iter__() est présent 

![iter](img/iter.png "Iter")