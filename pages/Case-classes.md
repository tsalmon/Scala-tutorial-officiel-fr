Case Classes
=============

Scala supporte la notion de *case classes*. celles ci sont des classes commes les autres, mais qui ont la particularité d'exporter les parametres de leurs constructeurs ainsi que de permettre une décomposition via le [pattern matching](https://github.com/tsalmon/Scala-tutorial-officiel-fr/blob/master/pages/Pattern-matching.md).

Ceci est un exemple de la hiérarchie des classes, une classe abstraite Term et 3 cases classes Var, Fun et App

```scala
abstract class Term
case class Var(name: String) extends Term
case class Fun(arg: String, body: Term) extends Term
case class App(f: Term, v: Term) extends Term
```

Cette hiérarchie peut utilisée pour représenter des termes du [lamba-calcul non typé](http://fr.wikipedia.org/wiki/Lambda-calcul#Le_lambda-calcul_non_typ.C3.A9). Afin de facilier la construction d'instances de cases classes, le Scala ne requière pas d'utiliser la primitive `new`. On peut simplement utiliser le nom de la classe comme une fonction

Exemple:

```scala
Fun("x", Fun("y", App(Var("x"), Var("y"))))
```
Les paramètres du constructeur sont traités publiquement, et sont donc accessible directement:

```scala
val x = Var("x")
println(x.name)
```

Pour toute case class, le compilateur de Scala génère une méthode `equals` qui implémente l'égalité et une methode `toString` pour voir les instances affichées.

Exemple:

```scala
val x1 = Var("x")
val x2 = Var("x")
val y1 = Var("y")
println("" + x1 + " == " + x2 + " => " + (x1 == x2))
println("" + x1 + " == " + y1 + " => " + (x1 == y1))
```

affichera:

```scala
Var(x) == Var(x) => true
Var(x) == Var(y) => false
```

Cela donne n'a de sens que pour définir la case class si le pattern matching est utilisé pour décomposer la structure de données. L'objet suivant défini une fonction d'affichage pour notre implémentation du lambda calcul

```scala
object TermTest extends scala.App {
  def printTerm(term: Term) {
    term match {
      case Var(n) =>
        print(n)
      case Fun(x, b) =>
        print("^" + x + ".")
        printTerm(b)
      case App(f, v) =>
        print("(")
        printTerm(f)
        print(" ")
        printTerm(v)
        print(")")
    }
  }
  def isIdentityFun(term: Term): Boolean = term match {
    case Fun(x, Var(y)) if x == y => true
    case _ => false
  }
  val id = Fun("x", Var("x"))
  val t = Fun("x", Fun("y", App(Var("x"), Var("y"))))
  printTerm(t)
  println
  println(isIdentityFun(id))
  println(isIdentityFun(t))
}
```

Dans notre exemple, la fonction `printTerm` est exprimé comme un état de pattern matching qui commence par "matcher" les mots clé (Var, Fun et App)  et consiste en une séquence de `case Pattern => Body clauses`/ Le programme définie aussi une fonction `isIdentityFun` qui vérifie si le terme donné correspond à une fonction. Cette exemple utilise principalement les patterns et les "guards". Apres avoir "matché" une pattern avec une valeur donnée, la "guard" (définie apres le mot clé `if`) est évaluée. Si elle retourne vrai, le match est réussi. sinon on passe au pattern suivant.
