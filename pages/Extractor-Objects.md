Extracteur d'objets
===================

En scala, les patterns peuvent être définis endépendamemment des cases classes. En ce sens, une méthode nommé et non définie est utilisée pour renvoyer le-dit extracteur . Par exemple, le code suivant défini un extracteur d'objets de Twice

```scala
object Twice {
  def apply(x: Int): Int = x * 2
  def unapply(z: Int): Option[Int] = if (z%2 == 0) Some(z/2) else None
}
object TwiceTest extends App {
  val x = Twice(21)
  x match { case Twice(n) => Console.println(n) } // prints 21
}
```

Il y a deux conventions syntaxiques à prendre en compte:

Le cas du pattern `Twice(n)` causera une invocation de la fonction `Twice.unapply` qui est utilisé pour reconnaître n'importe quel nombre; la valeur de retour est une valuer de la fonction unapply si l'argument a reconnu ou pas. Et n'importe quelle sous-valeurs qui peut être utilisé pour davantage match.
Ici, la sous-valeur est `z/2`.

La méthode `apply` n'est pas nécessaire pour le pattern matching. Elle est suelement utiliser pour imiter un constructeur. `val x = Twice.apply(21)`.

Le type de retour de `unapply` devrait être choisi comme suit:
* Si c'est seulement un test, retourner un booléen. Pour le reste, renvoyer autre chose.
* Si elle donne une sous-valeur de type T, retourner un `Option[T]`
* Si l'on souhaite renvoyer plusieurs sous valeurs T1, ..., Tn, alors les grouper dans un tuple optionel `Option[(T1, ... , Tn)]`

Parfois, le nombre de sous-valeurs est fixé et on aimerait retourner une séquence. C'est pour cela que l'on peut définir les patterns, à l'instart de `unapplySeq`. Le dernier type de sous-valeur Tn doit être `Seq[S]`. Ce mécanisme est utilisé poru les instances dans les cas de `List(x1, ..., xn)`

Les extracteurs peuvent produire du code plus maintenable. Pour plus de détails, lisez l'article [“Matching Objects with Patterns”](http://lampwww.epfl.ch/~emir/written/MatchingObjectsWithPatterns-TR.pdf) (voir la section 4) par Emir, Odersky et William (janvier 2007).
