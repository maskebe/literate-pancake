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
Pour être considéré comme itérable, l’objet doit implémenter les méthodes \__iter__() et \__next__().\
\
Supposons que nous avons :

Code :
```python

Numbers = [1, 2, 3, 4, 5, 6, 7]

print(dir(Numbers))
```
Résultat :
```output
['__class__', '__delattr__', '__dir__', '__doc__', '__eq__', '__format__', '__ge__', '__getattribute__', '__gt__', '__hash__', '__init__', '__init_subclass__', '__iter__', '__le__', '__length_hint__', '__lt__', '__ne__', '__new__', '__next__', '__reduce__', '__reduce_ex__', '__repr__', '__setattr__', '__setstate__', '__sizeof__', '__str__', '__subclasshook__']
```
On constate dans le resultat du code que la methode \__iter__() est présent 

![iter](img/iter.png "Iter")

Pour qu'une boucle fonctionne, elle appelle la méthode \__iter__(), qui retourne un itérateur. La boucle utilise l'itérateur pour parcourir les éléments.

Syntaxe :
```output
iter( object , sentinel )
```
La méthode iter() prend deux paramètres :\
- <span style="color:brown">Object</span> : un objet dont l’itérateur doit être créé par exemple les listes, tuples, sets, etc.\
- <span style="color:brown">Sentinel</span> : une valeur spéciale qui représente la fin de la séquence. Ce paramètre est optionnel.\

Un itérateur est un objet avec un état. C’est-à-dire qu’il se souvient de son état pendant l’itération. L’itérateur sait également comment récupérer l’élément suivant. Ils utilisent la méthode \__next__() pour récupérer l’élément suivant.  Cette méthode est obligatoire pour tout itérateur. La méthode garde une valeur à la foi.

Syntaxe :
```output
next( iterator , default )
```
La méthode next() accepte deux paramètres :\
- <span style="color:brown">Iterator</span> : la méthode next() retourne la valeur suivante de l’itérateur.\
- <span style="color:brown">Default</span> : cette valeur est retournée si l’itérateur n’a plus de valeur à retourner. Ce paramètre est optionnel.\

Nous allons faire un exemple avec une liste de différents types pour mieux comprendre :

```python
list = [ 77 , 1, 'DIT', 'Dakar', 'is fun' ] 
```

Nous allons parcourir cette liste avec le protocol d'itérateur qui comprend les deux méthodes iter() et next()

Code :
```python
#get an iterator using iter()
list_iter = iter(list)

#print the iterator
print(list_iter)

#next for fetching the first element which is 77
print(next(list_iter))

#fetching the remaining elements
print(next(list_iter))
print(next(list_iter))
print(next(list_iter))
print(next(list_iter))
```
Résultat :
```output 
<list_iterator object at 0x0000011229AD3F70>
77
1
DIT
Dakar
is fun

[Done] exited with code=0 in 0.078 seconds
```

Comme vous pouvez le constater quand on imprime le résultat de l’itérateur list_iter, il affiche le type et l’adresse mémoire. Ensuite il affiche les éléments un à un. Qu’est-ce qui va se passer si on essaie d’afficher le prochain élément alors que la liste est déjà parcourue.

Code :
```python
#trying to fetch next element after the last value is returned
print(next(list_iter))
```

Résultat :
```output
Traceback (most recent call last):
  File "c:\masterIA\python\final_exam\literate-pancake\output\tempCodeRunnerFile.py", line 20, in <module>
    print(next(list_iter))
StopIteration

[Done] exited with code=1 in 0.082 seconds
```

Quand on essaie d’afficher la valeur suivante alors que l’itérateur n’en a plus on a une exception de type **Stopiteration** qui veut dire que la séquence a épuisé ses éléments.
Il est important de souligner ici que les boucles for pour itérer, l'exception **Stopiteration** est gérer en interne et utiliser pour terminer la boucle sans erreur. Si nous utilisons un itérateur nous devons gérer nous même le cas des exception **Stopiteration**.

Exemple d'itérateur :
