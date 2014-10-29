# Classes

Les classes en Scala sont des templates statiques qui s'instancient dans de nombreux objets à l'execution. Ici nous avons des définitions de classes qui représentent la classe Point:

```scala
class Point(xc: Int, yc: Int) {
  var x: Int = xc
  var y: Int = yc
  def move(dx: Int, dy: Int) {
    x = x + dx
    y = y + dy
  }
  override def toString(): String = "(" + x + ", " + y + ")";
}
```

Cette classe est définie avec 2 variables, `x` et `y`, et deux méthodes: `move` et `toString`. `move` prend 2 entiers en paramètres mais ne retourne pas de valeurs (elle return le type Unit qui correspond au void de Java). `toString`, de son coté, ne prend aucun paramètres mais retourne une chaîne de caractères. Comme `toString` réécrit (override) la fonction prédéfinie `toString`, c'est cette fonction que nous recevrons en l'appellant.

Les classes sont paramétrables avec des arguments, le code du dessus en utilise 2: `xc` et `yc`, ils sont visibles dans tout le corps de la classe. Dans notre exemple ils sont utilisé pour initialiser les variables x et y.

Les classses sont instanciées avec une nouvelle primitive ainsi que le montre cet exemple:

```scala
object Classes {
  def main(args: Array[String]) {
    val pt = new Point(1, 2)
    println(pt)
    pt.move(10, 10)
    println(pt)
  }
}
```

Le programme définit une application executable `Classes` dans la forme d'un objet singleton de haut-niveau avec une méthode main. Cette méthode crée un nouveau `Point` et le stocke dans une valeur `pt`. Notons que les valeurs se définissent avec le constructeur `val` (voir classe ci desus) dans laquelle elles ne sont pas modifiable (c'est à dire que la valeur est constante).


Voici la sortie du programme redirigé vers la sortie standart:

```
(1, 2)
(11, 12)
```
