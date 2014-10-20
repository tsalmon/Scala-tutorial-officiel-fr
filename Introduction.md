# Introduction

## Scala est un langage moderne multi-paradigme conçu pour exprimer les patterns
courants de programmation d'une manière concise, élégante et sûr.
Il intègre entièrement les caractéristiques des langages orienté objet et
fonctionnels

## Scala est orienté objet
Scala est un langage orienté objet pur dans le sens où
[chaque valeur est un objet](https://github.com/tsalmon/Scala-documentation-francaise/blob/master/Unified-types.md).
Les types et le comportement des objets est décrit dans les
[classes](https://github.com/tsalmon/Scala-documentation-francaise/blob/master/Classes.md)
et les
[traits](https://github.com/tsalmon/Scala-documentation-francaise/blob/master/Traits.md).
Les classes sont étendues en sous classes et un
[mécanisme de mixage basé sur la composition](https://github.com/tsalmon/Scala-documentation-francaise/blob/master/Mixin-class-composition.md)
permet de faire un héritage multiple.

## Scala est fonctionnel
Scala est également un langage fonctionnel dans le sens où
[chaque fonction est une valeur](https://github.com/tsalmon/Scala-documentation-francaise/blob/master/Unified-types.md).
Scala offre une syntaxe légère pour définir des fonctions anonymes
(ie sans nom). Il supporte les
[fonctions d'ordre supérieur](https://github.com/tsalmon/Scala-documentation-francaise/blob/master/Higher-order-functions.md),
il permet aux
fonctions d'être
[imbriquées](https://github.com/tsalmon/Scala-documentation-francaise/blob/master/Nested-functions.md),
et supporte la
[curryfication](https://github.com/tsalmon/Scala-documentation-francaise/blob/master/Currying.md),
Les
[case classes](https://github.com/tsalmon/Scala-documentation-francaise/blob/master/Case-classes.md)
de Scala sont conçus pour supporter le
[pattern matching](https://github.com/tsalmon/Scala-documentation-francaise/blob/master/Pattern-matching.md)
algébrique en utilisant le fonctionnement des langages fonctionnels.

De plus, la notion de pattern matching dans Scala est naturellement étendue dans
le
[processing des données XML](https://github.com/tsalmon/Scala-documentation-francaise/blob/master/XML-processing.md)
avec l'aide des
[sequences de pattern ignorable](https://github.com/tsalmon/Scala-documentation-francaise/blob/master/regular-expression-patterns.md).
C'est dans ce contexte que les
[séquences de compréhension](https://github.com/tsalmon/Scala-documentation-francaise/blob/master/sequence-comprehensions.md)
sont utiles afin de formuler des requêtes.
Ces caractéristiques font du Scala un langage idéal pour développer des
applications web.

## Scala est typé statiquement
Scala est muni d'un système de types d'expression qui applique de manière
statique une abstraction utilisable de manière sûre et cohérente.
En particulier, le système de types supporte:
[la généricité des classes](https://github.com/tsalmon/Scala-documentation-francaise/blob/master/Generic-classes.md),
[les annotations variantes](https://github.com/tsalmon/Scala-documentation-francaise/blob/master/Variances.md),
[type de bornes supérieures](https://github.com/tsalmon/Scala-documentation-francaise/blob/master/Upper-type-bounds.md)
et
[inférieures](https://github.com/tsalmon/Scala-documentation-francaise/blob/master/Lower-type-bounds.md),
[sous classes de classe](https://github.com/tsalmon/Scala-documentation-francaise/blob/master/Inner-classes.md),
et
[type abstrait](https://github.com/tsalmon/Scala-documentation-francaise/blob/master/Abracts-types.md)
 des objets membres
[compositions explicites de types autoréférencés](https://github.com/tsalmon/Scala-documentation-francaise/blob/master/Explicitly-typed-self-references.md),
[vues](https://github.com/tsalmon/Scala-documentation-francaise/blob/master/Views.md),
[méthodes polymorphes](https://github.com/tsalmon/Scala-documentation-francaise/blob/master/Polymorphic-methods.md).

Un
[mécanisme d'inférence de type locale](https://github.com/tsalmon/Scala-documentation-francaise/blob/master/Local-type-inference.md)
 prend en charge ce que l'utilisateur
n'utilise pas pour annoter le programme avec un type d'information redondant.
En les combinant, ces fonctionnalitées produisent une base puissante,
réutilisable et sûre de la programmation abstraite et pour les extensions de
type de sécurisé du programme.

## Scala est extensible
En pratique, le développement dans un domaine d'application spécifique requière
souvent des domaines d'extensions spécifique de langages. Scala offre une
combinaison unique de mécanique de langages qui lui permette d'ajouter
facilement de nouvelles constructions de langages sous forme de bibliothèques:
N'importe quelle méthode peut être utilisée comme un opérateur
[infixe ou postfix](https://github.com/tsalmon/Scala-documentation-francaise/blob/master/Operators.md), 
[les clôtures](https://github.com/tsalmon/Scala-documentation-francaise/blob/master/Automatic-closures.md)
sont construites automatiquement en dépendant d'un type espéré
(celui ciblé).

Une jointure utilisée dans chacune des fonctionnalitées facilitées la définition
de nouveaux états sans extensions avec la syntaxe et sans utiliser de macro

Scala est inter-opérable avec Java(dont JRE) et .NET. En particulier, les
intéractions avec Java sont aussi faciles que possible. Scala a le même model de
compilation (compilation séparée, chargement dynamique des classes) comme Java
et permet l'acces de millier de bibliothèqyes de hautes qualitées. Scala
support aussi le framework .NET (CLR).
