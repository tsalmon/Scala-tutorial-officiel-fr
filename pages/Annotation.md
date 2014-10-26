# Annotations

Les annotations associe des meta-informations avec des définitions.


Une simple clause d annotation est de la forme `@C` ou bien `@C(a1,...,an)`. Ici, `C` est un constructeur de la classe `C`, laquelle doit être conforme à la classe `scala.Annotation`. Tous les arguments a1, ..., an donnés aux constructeurs doivent êtres des expressions constantes (cad des expression de nombres littéraux, des chaînes de caractères, des classes littérales, des énumations Java et des tableaux d'une dimension).

Une clause d'annotation s'applique à la premiere définition ou a la première déclaration qui la suie.
Plus d'une clause peut en précéder. L'ordre dans laquelle ces clauses sont données n'a pas d'importance.

La signification des clauses est celle d'une dépendance-implémentée*. Sur une plateforme java, les annotations de scala ont une signification normalisée


 Scala |	Java
 --- | ---
scala.SerialVersionUID	| serialVersionUID (field)
scala.cloneable|	java.lang.Cloneable
scala.deprecated	| java.lang.Deprecated
scala.inline (since 2.6.0) |	no equivalent
scala.native (since 2.6.0) |	native (keyword)
scala.remote |	java.rmi.Remote
scala.serializable |	java.io.Serializable
scala.throws |	throws (keyword)
scala.transient |	transient (keyword)
scala.unchecked (since 2.4.0) | 	no equivalent
scala.volatile |	volatile (keyword)
scala.reflect.BeanProperty |	Design pattern

Dans l'exemple qui suit, nous avons ajouté une annotation de cas d'echec à la définition d'une methode de l'ecture dans le but de capturer une exception d'une programme Java.

>Un compilateur Java vérifir que le programme contient un [gestionnaire d'exceptions](http://docs.oracle.com/javase/specs/jls/se5.0/html/exceptions.html) qui lui-même vérifie que des exceptions résultes bien de l'execution d'une méthode ou d'un constructeur. Pour chaque exception vérifiée avec un résultat posssible, la clause de **cas d'echec**  pour la méthode ou le constructeur doit mentionner la classe de cette exception ou une de ses supers classes (comme la classe Exception). Puisque que Scala n'a pas ce genre de technique, les methodes ecritent dans ce language doivent être annotées avec une ou plusieurs clauses d'erreurs (*throw*) afin que Java puisse faire ce travail.

```scala
package examples
import java.io._
class Reader(fname: String) {
  private val in = new BufferedReader(new FileReader(fname))
  @throws(classOf[IOException])
  def read() = in.read()
}
```

Le programme suivant, en Java, affiche le contenu d'un fichier dont le nom est passé en premier argument à la méthode `main`.

```java
package test;
import examples.Reader;  // Scala class !!
public class AnnotaTest {
    public static void main(String[] args) {
        try {
            Reader in = new Reader(args[0]);
            int c;
            while ((c = in.read()) != -1) {
                System.out.print((char) c);
            }
        } catch (java.io.IOException e) {
            System.out.println(e.getMessage());
        }
    }
}
```

En commentant l'annotation de cas d'erreur dans la class Read, cela produit le message d'erreur ci-dessous quand le programme est compilé par Java:

```
Main.java:11: exception java.io.IOException is never thrown in body of
corresponding try statement
        } catch (java.io.IOException e) {
          ^
1 error
```

## Annotations Java
>Note: Vérifiez que vous utilisé bien l'option  -target:jvm-1.5  avec les annotations de Java

Java 1.5 introduit les métadata définies par l'utilisateur en forme d'annotations. la principale caractéristique de cela est qu'elles se fondent sur la spécification de paire nom-valeur pour initialiser leurs élèments. Par exemple, si nous avons besoin d'une annontation pour traquer la source de certaines classes, nous pourrions définir cela comme :

```java
@interface Source {
  public String URL();
  public String mail();
}
```

Et puis appliquer cela:

```java
@Source(URL = "http://coders.com/",
        mail = "support@coders.com")
public class MyClass extends HisClass ...
```

Les applications de l'annotations en Scala sont semblable à l'invocation d'un constructeur. Pour instancier une annotation Java l'une d'elle doit utiliser des arguments nommés:

```java
@Source(URL = "http://coders.com/",
        mail = "support@coders.com")
class MyScalaClass ...
```

Cette syntaxe est assez fastidieuse si l'annotion contien seulement un élèment (sans valeur par défaut) donc, par convention, si le nom est spécifié comme une valeur, elle s'applique en Java en utilisant un constructeur du type:

```java
@interface SourceURL {
    public String value();
    public String mail() default "";
}
```

Et ceci s'applique à cela:

```java
@SourceURL("http://coders.com/")
public class MyClass extends HisClass ...
```

Dans ce cas, Scala offre la même possibilité:

```scala
@SourceURL("http://coders.com/")
class MyScalaClass ...
```

L'élèment `mail` a été spécifié avec une valeur par défaut (null), donc nous n'avons plus besoin de spécifier la provenance de cette valeur.
Quoi qu'il en soit, si nous avons besoin de le faire, nous pourrions tout de même le faire en reprenant le style du java:

```scala
@SourceURL(value = "http://coders.com/",
           mail = "support@coders.com")
public class MyClass extends HisClass ...
```

Scala offre plus de fléxibilité

```scala
@SourceURL("http://coders.com/",
           mail = "support@coders.com")
    class MyScalaClass ...
```

Cette syntaxe étendue est compotatible avec les annotations .NET.

*implementation-dependent
