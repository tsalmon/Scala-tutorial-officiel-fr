# Introduction

## Scala est un langage moderne multi-paradigme conçu pour exprimer les patterns
courants de programmation d'une manière concise, élégante et sûr.
Il intègre entièrement les caractéristiques des langages orienté objet et
fonctionnels

## Scala est orienté objet
Scala est un langage orienté objet pur dans le sens où [chaque valeur est un
objet]. Les types et le comportement des objets est décrit dans les [classes] et
les [traits]. Les classes sont étendues en sous classes et un [mécanisme de
mixage basé sur la composition] permet de faire un héritage multiple

## Scala est fonctionnel
Scala est également un langage fonctionnel dans le sens où [chaque fonction est
une valeur]. Scala offre une syntaxe légère pour définir des fonctions anonymes
(ie sans nom). Il supporte les [fonctions d'ordre supérieur], il permet aux
fonctions d'être [imbriquées], et supporte les [<<curifiage>>], Les
[case classes] de Scala sont conçus pour supporter le [pattern matching]
algébrique en utilisant le fonctionnement des langages fonctionnels.

De plus, la notion de pattern matching dans Scala est naturellement étendue dans
le [processing des données XML] avec l'aide des
[sequences de pattern ignorable]. C'est dans ce contexte que les
[séquences de compréhension] sont utiles afin de formuler des requêtes.
Ces caractéristiques font du Scala un langage idéal pour développer des
applications web.

## Scala est typé statiquement
Scala est muni d'un système de types d'expression qui applique de manière
statique une abstraction utilisable de manière sûre et cohérente.
En particulier, le système de types supporte: [la généricité des classes],
[les annotations variantes], [type de bornes supérieures et inférieures],
[sous classes de classe], et [type abstrait] des objets membres
[compositions explicites de types autoréférencés], [vues],
[méthodes polymorphes].

Un [mécanisme d'inférence de type locale] prend en charge ce que l'utilisateur
n'utilise pas pour annoter le programme avec un type d'information redondant.
En les combinant, ces fonctionnalitées produisent une base puissante,
réutilisable et sûre de la programmation abstraite et pour les extensions de
type de sécurisé du programme.

## Scala est extensible
En pratique, le développement dans un domaine d'application spécifique requière
souvent des domaines d'extensions spécifique de langages. Scala offre une
combinaison unique de mécanique de langages qui lui permette d'ajouter
facilement de nouvelles constructions de langages sous forme de bibliothèques:
N'importe quelle méthode peut être utilisée comme un opérateur infixe ou postfix
les clôtures sont construites automatiquement en dépendant d'un type espéré
(celui ciblé).

Une jointure utilisée dans chacune des fonctionnalitées facilitées la définition
de nouveaux états sans extensions avec la syntaxe et sans utiliser de macro

Scala est inter-opérable avec Java(dont JRE) et .NET. En particulier, les
intéractions avec Java sont aussi faciles que possible. Scala a le même model de
compilation (compilation séparée, chargement dynamique des classes) comme Java
et permet l'acces de millier de bibliothèqyes de hautes qualitées. Scala
support aussi le framework .NET (CLR).
