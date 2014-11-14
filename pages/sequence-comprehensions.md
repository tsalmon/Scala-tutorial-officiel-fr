Scala offre une notation assez légère pour les compréhension de séquences d'expressions. Les compréhensions ont la forme suivante: `for (enumerateurs) yield e`, où les énumérateurs sont exprimé dans une liste séparé de points-virgules d'énumérateurs (ie : (énumérateur 1 ; ... ; énumerateur n) ). Un énumérateur est soit un générateur qui introduit une nouvelle variable, soit un filtre. Une compréhension évalue `e` pour chaque valeurs généré par les énumérateurs et retourne la séquence de ces évaluations

Voici un exemple:

```scala
object ComprehensionTest1 extends App {
  def even(from: Int, to: Int): List[Int] =
    for (i <- List.range(from, to) if i % 2 == 0) yield i
  Console.println(even(0, 20))
}
```

La for-expression dans la fonction introduit une nouvelle variable `i` de type Int qui est produite pour chaque valeurs de la liste `List(from, from + 1, ... , to - 1)`. La garde `if i % 2 == 0` filtre toutes les valeurs impaires donc on ne ressort que toutes les valeurs paires.

Le programme produit la sortie suivante:
```scala
List(0, 2, 4, 6, 8, 10, 12, 14, 16, 18)
```

Voici un exemple plus complexe qui joint toutes les paires de nombres compris entre 0 et n - 1, égaux et qui donne une valeur v:

```scala
object ComprehensionTest2 extends App {
  def foo(n: Int, v: Int) =
    for (i <- 0 until n;
         j <- i until n if i + j == v) yield
      Pair(i, j);
  foo(20, 32) foreach {
    case (i, j) =>
      println("(" + i + ", " + j + ")")
  }
}
```

Cet exemple montre que les compréhensions ne se restreignent pas qu'aux listes. Le programme précédent utilise ainsi des itérateurs Tout type de donnée qui support les opérations de `filterWith`, `map`, et `flatMap` (avec leurs propres types) peuvent êtres utilisées dans une séquence de compréhensions.

La sortie du programme:

```scala
(13, 19)
(14, 18)
(15, 17)
(16, 16)
```

Il y a aussi une forme spéciale pour les séquences de compréhension qui ne retourne rien (Unit). Ici, les valeurs qui sont crées a partir de la liste des générateurs et de filtres sont utilités pour produire un effet de bord. Le programmeur a ommit le mot-clé `yield` pour faire la séquence de compréhension souhaitée. Ci dessous le programme équivalant au précédent mais qui utilise la forme spéciale renvoyant Unit

```scala
object ComprehensionTest3 extends App {
  for (i <- Iterator.range(0, 20);
       j <- Iterator.range(i, 20) if i + j == 32)
    println("(" + i + ", " + j + ")")
}
```
