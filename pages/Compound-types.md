Types composés
==============

Parfois il est nécessaire d'exprimer que le type d'un objet est un sous-type de plusieurs autres types. En scala cela peut être exprimé à l'aide de types composés qui sont des intersections de types objets.


Supposons que nous ayons deux Traits, `Cloneable` et `Resetable`:

```scala
trait Cloneable extends java.lang.Cloneable {
  override def clone(): Cloneable = {
    super.clone().asInstanceOf[Cloneable]
  }
}
trait Resetable {
  def reset: Unit
}
```

Maintenant, supposons que nous voulions ecrire une fonction `cloneAndReset` qui prenne un objet en paramètre, le clone, et réinitialise l'objet de départ:

```scala
def cloneAndReset(obj: ?): Cloneable = {
  val cloned = obj.clone()
  obj.reset
  cloned
}
```

La question que l'on se pose est de savoir quel est le type du paramètre `obj`. Si c'est un objet `Cloneable`, alors l'objet peut être cloné mais pas réinitialisé, si c'est un objet `Resetable` nous pouvons le réinitialiser mais pas le cloner. Pour annuler le le type dans cette situation, nous pouvons spécifier que le type `obj`peut être soit un `Cloneable`, soit un `Resetable`. Ce type compos" est écrit comme en scala : `Cloneable` avec `Resetable`.

Voici notre fonction amélioré:

```scala
def cloneAndReset(obj: Cloneable with Resetable): Cloneable = {
  //...
}
```

Comme les types composés peuvent être constitué de plusieurs types et qu'ils peuvent avoir un raffinement unique qui peut être utilisé pour restreindre la signature des membres ojets existants. La forme générale est `A with B with C ... { raffinement}`
ment }

Un exemple de raffinement peut etre vu sur la page des [types abstraits](https://github.com/tsalmon/Scala-tutorial-officiel-fr/blob/master/pages/Abstracts-types.md)

An example for the use of refinements is given on the page about abstract types.
