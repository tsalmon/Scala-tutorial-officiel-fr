##Type Abstrait

En Scala, les classes sont paramétées avec des valeurs (le constructeur de paramètres) et avec des types (si les classes sont génériques). Pour des raisons de continuité, non seulement il est posssible de d'avoir des valeurs objet, mais de plus, les types avec des valeurs sont membres des objets*. Par ailleurs, les differentes formes des membres peuvent etre abstraite et concrêtes. Voici un exemple qui définit une valeur non définie et un type abstrait en étant membres de la classe Buffer

```scala
trait Buffer {
  type T  
  val element: T
}
```

Les types abstraits sont des types dont l'identité n'est pas précisement connue. Dans l'exemeple ci-dessus, nous savons seulement que chaque objet de la classe Buffer est un membre du type T mais la définition de la classe Buffer ne précise pas concrétement à quoi le type T correspond. Comme les définitions de valeurs, nous pouvons recouvrire la définition de type dans une sous classe. Ceci nous  permettant de réveler plus d'informations sur le type abstrait par contraction de type liés (qui décrivent les instanciations du type abstrait).


Dans le programme ci-dessous, nous dérivons la classe SeqBuffer qui nous permet seulement de mémoriser dans un buffer indiquant que le type T doit être un sous type de Seq[U]:

```scala
abstract class SeqBuffer extends Buffer {
  type U
  type T <: Seq[U]
  def length = element.length
}
```

Les traits, ou classes avec types abstraits sont souvent utilisés en se servant d'instances de classes anonymes:

```scala
abstract class IntSeqBuffer extends SeqBuffer {
  type U = Int
}

object AbstractTypeTest1 extends App {
  def newIntSeqBuf(elem1: Int, elem2: Int): IntSeqBuffer =
    new IntSeqBuffer {
         type T = List[U]
         val element = List(elem1, elem2)
       }
  val buf = newIntSeqBuf(7, 8)
  println("length = " + buf.length)
  println("content = " + buf.element)
}
```

Le type retour de la methode `newIntSeqBuf` se réfère à un spécialisation du trait `Bufer` dans lequel le type `U` est équivalent au `Int`, nous avons des types alias de types similaires dans la classe anonyme instanciée  dans le corps de cette méthode. Ici nous créons une nouvelle instance de `IntSeqBuf` dans laquelle le type T se réfère à une liste d'entiers.

Veuillez notez qu'il est souvent possible de convertir un type abstrait en un type de paramètre de classe  et vice versa. Voici une version du code ci-dessus avec seulement des type parametres:

```scala
abstract class Buffer[+T] {
  val element: T
}
abstract class SeqBuffer[U, +T <: Seq[U]] extends Buffer[T] {
  def length = element.length
}
object AbstractTypeTest2 extends App {
  def newIntSeqBuf(e1: Int, e2: Int): SeqBuffer[Int, Seq[Int]] =
    new SeqBuffer[Int, List[Int]] {
      val element = List(e1, e2)
    }
  val buf = newIntSeqBuf(7, 8)
  println("length = " + buf.length)
  println("content = " + buf.element)
}
```

Notez que nous avons utilisé une variante de notation, ailleurs nous ne pourrions pas cachez l'implémentation du type de la séquence des objets retournés depuis la méthode. De plus, il y a des cas où il est pas possible de remplacer un type abstrait avec un type paramètre


*types along with values are members of objects
