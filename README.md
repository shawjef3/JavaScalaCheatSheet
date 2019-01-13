# Java and Scala Comparison Cheat Sheet

## Introduction

This is a reference to help people fluent in Java or Scala to become fluent in the other. I was inspired by the [C# and VB.NET Comparison Cheat Sheet](http://aspalliance.com/625).

## Other Cheat Sheets

https://www.rea-group.com/blog/java-to-scala-cheatsheet/  
http://www.cis.upenn.edu/~matuszek/Concise%20Guides/Concise%20Java%20to%20Scala.html

## Cheat Sheet

<table align="center">
  <tr><th>Java</th><th>Scala</th></tr>
  <tr><th colspan="2">packages</td></tr>
  <tr><td><pre>package me.jeffshaw;</pre></td><td><pre>package me.jeffshaw</pre></td></tr>
  <tr><td><pre>import me.jeffshaw.Class;</pre></td><td><pre>import me.jeffshaw.Class</pre></td></tr>
  <tr><td><pre>import me.jeffshaw.Class0;
import me.jeffshaw.Class1;</pre></td><td><pre>import me.jeffshaw.Class0
import me.jeffshaw.Class1</pre>
or
<pre>import me.jeffshaw.{Class0, Class1}</pre></td></tr>
  <tr><td><pre>import me.jeffshaw.*;</pre></td><td><pre>import me.jeffshaw._</pre></pre></td></tr>
  <tr><td>☹</td><td><pre>import me.jeffshaw.{Class => RenamedClass}</pre></td></tr>
  <tr><th colspan="2">classes</td></tr>
  <tr><td><pre>class C {}</pre></td><td><pre>class C</pre></td></tr>
  <tr><td><pre>class C {
  public int i;
}</pre></td><td><pre>class C {
  var i: Int = _
}</pre></td></tr>
  <tr><td><pre>class C {
  public int i = 0;
}</pre></td><td><pre>class C {
  var i = 0
}</pre></td></tr>
  <tr><td><pre>class C {
  public int i;

  public C(int i) {
    this.i = i;
  }
}</pre></td><td><pre>class C(var i: Int)</pre>
is shorthand for
<pre>class C {
  var i: Int = _
  def C(i: Int) {
    this.i = i
  }
}</pre></td></tr>
  <tr><td><pre>class C&lt;A&gt; {}</pre></td><td><pre>class C[A]</pre></td></tr>
  <tr><td><pre>class C&lt;A extends Comparable&gt; {}</pre></td><td><pre>class C[A <: Comparable]</pre></td></tr>
  <tr><td><pre>class C&lt;A extends Comparable, Serializable&gt; {}</pre></td><td><pre>class C[A <: Comparable with Serializable]</pre></td></tr>
  <tr><td>☹</td><td><pre>class C[-A]</pre></td></tr>
  <tr><td>☹</td><td><pre>class C[+A]</pre></td></tr>
  <tr><th colspan="2">interfaces</td></tr>
  <tr><td><pre>interface I {}</pre></td><td><pre>trait I {}</pre></td></tr>
  <tr><td><pre>interface I&lt;A&gt; {}</pre></td><td><pre>trait I[A] {}</pre></td></tr>
  <tr><td><pre>interface I {
  void method(int i) {}
}</pre></td><td><pre>trait I {
  def method(i: Int): Unit = {}
}</pre></td></tr>
  <tr><td>☹</td><td><pre>trait I {
  val i: Int = 3
}</pre></td></tr>
  <tr><th colspan="2">methods</td></tr>
  <tr><td><pre>void f(int i) {}</pre></td><td><pre>def f(i: Int): Unit = {}</pre>
  or
<pre>def f(i: Int): Unit = ()</pre></td></tr>
  <tr><td><pre>int f(int i) {return i;}</pre></td><td><pre>def f(i: Int): Int = i</pre></td></tr>
  <tr><td><pre>int f(int ints...) {return Arrays.stream(ints).sum();}</pre></td><td><pre>def f(ints: Int*): Int = ints.sum</pre></td></tr>
  <tr><td><pre>f(1,2,3);</pre></td><td><pre>f(1,2,3)</pre></td></tr>
  <tr><td><pre>int[] ints;
f(ints);</pre></td><td><pre>val ints: Array[Int]
f(ints: _*)</pre></td></tr>
  <tr><td><pre>&lt;T, U&gt; U f(T arg);</pre></td><td><pre>def f[T, U](arg: T): U</pre></td></tr>
  <tr><th colspan="2">statics</td></tr>
  <tr><td><pre>class C {
    static int i = 0;
}</pre></td><td><pre>object C {
  var i = 0
}</pre></td></tr>
  <tr><td><pre>class C {
    static int f(int i) {
        return i + 1;
    }
}</pre></td><td><pre>object C {
  def f(i: Int): Int = i + 1
}</pre></td></tr>
  <tr><th colspan="2">member access permissions</td></tr>
  <tr><th colspan="2">private</td></tr>
  <tr><td><pre>private int i;</pre></td><td><pre>private var i: Int</pre></td></tr>
  <tr><th colspan="2">package private</td></tr>
  <tr><td><pre>int i;</pre></td><td><pre>package a
class C {
  private[a] var i: Int
}</pre></td></tr>
  <tr><th colspan="2">public</td></tr>
  <tr><td><pre>public int i;</pre></td><td><pre>var i: Int</pre></td></tr>
  <tr><th colspan="2">protected</td></tr>
  <tr><td><pre>protected int i;</pre></td><td><pre>protected var i: Int</pre></td></tr>
  <tr><th colspan="2">mutability</td></tr>
  <tr><td><pre>int i;</pre></td><td><pre>var i: Int</pre></td></tr>
  <tr><td><pre>final int i;</pre></td><td><pre>val i: Int</pre></td></tr>
  <tr><td><pre>void f(int i) {
  i = 4;
}</pre></td><td>☹</td></tr>
  <tr><td><pre>void f(final int i) {}</pre></td><td><pre>def f(i: Int): Unit = ()</pre></td></tr>
<tr><th colspan="2">immutable data structure</td></tr>
  <tr><td><pre>public class C implements Serializable {
    private final int c;

    public C(int c) {
        this.c = c;
    }

    public int getC() {
        return c;
    }

    @Override
    public boolean equals(Object o) {
        if (this == o) {
            return true;
        }
        if (o == null || getClass() != o.getClass()) {
            return false;
        }
        C c1 = (C) o;
        return getC() == c1.getC();
    }

    @Override
    public int hashCode() {
        return Objects.hash(getC());
    }
}
</pre></td><td><pre>case class C(c: Int)</pre></td></tr>
  <tr><th colspan="2">bean / mutable data structure</td></tr>
  <tr><td><pre>public class C implements Serializable {
    private int c;

    public C() {}

    public int getC() {
        return c;
    }

    public void setC(int c) {
        this.c = c;
    }

    @Override
    public boolean equals(Object o) {
        if (this == o) {
            return true;
        }
        if (o == null || getClass() != o.getClass()) {
            return false;
        }
        C c1 = (C) o;
        return getC() == c1.getC();
    }

    @Override
    public int hashCode() {
        return Objects.hash(getC());
    }
}</pre></td><td><pre>case class C(
  @BeanProperty var c: Int
) {
  def this() {  
    this(0)
  }
}</pre></td></tr>
  <tr><th colspan="2">control structures</td></tr>
  <tr><td><pre>return;</pre></td><td><pre>()</pre></td></tr>
  <tr><td><pre>return 0;</pre></td><td><pre>0</pre></td></tr>
  <tr><td><pre>return test ? 0 : 1;</pre></td><td><pre>if (test) 0 else 1</pre></td></tr>
  <tr><td><pre>if (test) {
  doSomething();
} else {
  doSomethingElse();
}</pre></td><td><pre>if (test) {
  doSomething()
} else {
  doSomethingElse()
}</pre></td></tr>
  <tr><td><pre>int i = 0;
while (i < 10) {
  i++;
}</pre></td><td><pre>var i = 0
while (i < 10) {
  i += 1
}</pre></td></tr>
  <tr><td><pre>int i = 0;
do {
  i++;
} while (i < 10)</pre></td><td><pre>var i = 0
do {
  i += 1
} while (i < 10)</pre></td></tr>
  <tr><td><pre>for (int i: collection) {}</pre></td><td><pre>for (i <- collection) {}</pre></td></tr>
  <tr><td><pre>for (int i: collection) {
  for (int j: otherCollection) {}
}</pre></td><td><pre>for {
  i <- collection
  j <- otherCollection
} {}</pre></td></tr>
  <tr><td><pre>switch (value) {
  case 0:
    break;
  default:
}</pre></td><td><pre>value match {
  case 0 =>
  case _ =>
}</pre></td></tr>
  <tr><td><pre>switch (value) {
  case 0:
  case 1:
    break;
  default:
}</pre></td><td><pre>value match {
  case 0 | 1 =>
  case _ =>
}</pre></td></tr>
  <tr><td><pre>// cases share switch's scope
switch (value) {
  case 0: {
    int i = 0;
    break;
  }
  default: {
    int i = 0;
  }
}</pre></td><td><pre>// cases each have their own scope
value match {
  case 0 =>
    val i = 0;
  case _ =>
    val i = 0;
}</pre></td></tr>
  <tr><th colspan="2">exceptions</td></tr>
  <tr><td><pre>throw new Exception();</pre></td><td><pre>throw new Exception()</pre></td></tr>
  <tr><td><pre>try {
} catch (IOException e) {
} catch (RuntimeException e) {
} finally {}</pre></td><td><pre>try {
} catch {
    case e: IOException =>
    case e: RuntimeException =>
} finally {}</pre></td></tr>
  <tr><th colspan="2">try-with-resources</td></tr>
  <tr><td><pre>try (InputStream i0 = new InputStream();
     InputStream i1 = new InputStream()) {
}</pre></td><td>☹</td></tr>
  <tr><th colspan="2">data types</td></tr>
  <tr><td><pre>void</pre></td><td><pre>Unit</pre></td></tr>
  <tr><td><pre>bool</pre></td><td><pre>Boolean</pre></td></tr>
  <tr><td><pre>byte</pre></td><td><pre>Byte</pre></td></tr>
  <tr><td><pre>char</pre></td><td><pre>Char</pre></td></tr>
  <tr><td><pre>int</pre></td><td><pre>Int</pre></td></tr>
  <tr><td><pre>long</pre></td><td><pre>Long</pre></td></tr>
  <tr><td><pre>float</pre></td><td><pre>Float</pre></td></tr>
  <tr><td><pre>double</pre></td><td><pre>Double</pre></td></tr>
  <tr><td><pre>Object</pre></td><td><pre>AnyRef</pre></td></tr>
  <tr><td>☹</td><td><pre>Any</pre></td></tr>
  <tr><td>☹</td><td><pre>AnyVal</pre></td></tr>
  <tr><th colspan="2">null</td></tr>
  <tr><td><pre>null</pre></td><td><pre>null</pre></td></tr>
  <tr><th colspan="2">arrays</td></tr>
  <tr><td><pre>int[] ints = new int[] {1,2,3};</pre></td><td><pre>var ints = Array(1,2,3)</pre></td></tr>
  <tr><td><pre>int[][] ints = new int[][] {
  {1,2,3},
  {4,5,6},
  {7,8,9}
};</pre></td><td><pre>var ints = Array(
  Array(1,2,3),
  Array(4,5,6),
  Array(7,8,9)
)</pre></td></tr>
  <tr><td><pre>int[] ints = new int[3];</pre></td><td><pre>var ints = Array.ofDim[Int](3)</pre></td></tr>
  <tr><td><pre>int[][] ints = new int[3];
for (int i=0; i<3; i++) {
  ints[i] = new int[3]; 
}</pre></td><td><pre>var ints = Array.ofDim[Int](3, 3)</pre></td></tr>
  <tr><td><pre>int[] ints = new int[3];
Arrays.fill(ints, 0);</pre></td><td><pre>var ints = Array.fill(3)(0)</pre></td></tr>
  <tr><td><pre>String[] intStrings = new String[3];
for (int i=0; i<3; i++) {
  intStrings[i] = Integer.toString(i);
}</pre>
or
<pre>IntStream.range(0, 3)
  .mapToObj(Integer::toString)
  .toArray();</pre>
</td><td><pre>var intStrings = Array.tabulate(3)(_.toString)</pre></td></tr>
  <tr><td>☹</td><td><pre>def triple[T: ClassTag](): Array[T] = {
  Array.ofDim[T](3)
}</pre></td></tr>
  <tr><td><pre>int[] ints;
int thirdInt = int[3];</pre></td><td><pre>val ints: Array[Int]
val thirdInt = ints(3)</pre></td></tr>
  <tr><th colspan="2">operations</td></tr>
  <tr><td><pre>&&, ||, !</pre></td><td><pre>&&, ||, !</pre></td></tr>
  <tr><td>for primitives<pre>==, !=</pre></td><td><pre>==, !=</pre></td></tr>
  <tr><td>for references<pre>==, !=</pre></td><td><pre>eq, ne</pre></td></tr>
  <tr><td>for references<pre>.equals</pre></td><td><pre>==, !=</pre></td></tr>
  <tr><td><pre>&lt;, &gt;, &lt;=, &gt;=</pre></td><td><pre>&lt;, &gt;, &lt;=, &gt;=</pre></td></tr>
  <tr><td><pre>+, -, *, /, %</pre></td><td><pre>+, -, *, /, %</pre></td></tr>
  <tr><td><pre>&, |, ^, ~, &lt;&lt;, &gt;&gt;, &gt;&gt;&gt;</pre></td><td><pre>&, |, ^, ~, &lt;&lt;, &gt;&gt; &gt;&gt;&gt;</pre></td></tr>
  <tr><td><pre>+=, -=, *=, /=, %=, &lt;&lt=, &gt;&gt;=, &amp;=, ^=, |=</pre></td><td><pre>+=, -=, *=, /=, %=, &lt;&lt=, &gt;&gt;=, &amp;=, ^=, |=</pre></td></tr>
  <tr><td><pre>++, --</pre></td><td>☹</td></tr>
  <tr><td><pre>?:</pre>
  example
<pre>int i = test ? 0 : 1;</pre></td><td><pre>var i = if (test) 0 else 1</pre></td></tr>
  <tr><th colspan="2">io</td></tr>
  <tr><td colspan="2">writing to files or standard error is the same</td></tr>
  <tr><td><pre>System.out.println("hi");</pre></td><td><pre>System.out.println("hi")</pre>or<pre>println("hi")</pre></td></tr>
  <tr><td><pre>InputStreamReader reader =
  new InputStreamReader(System.in);
new BufferedReader(reader).readLine();</pre></td><td><pre>io.StdIn.readLine()</pre></td></tr>
  <tr><td><pre>Path path = Paths.get("file");
BufferedReader reader = Files.newBufferedReader(path);
for (String line: reader.lines().iterator()) {}</pre></td><td><pre>import scala.collection.JavaConverters._
val path = Paths.get("file")
val reader = Files.newBufferedReader(path)
for (line <- reader.lines.iterator.asScala) {}</pre>
or
<pre>val source = io.Source.fromFile("file")
for (line <- source.getLines()) {}</pre></td></tr>
  <tr><th colspan="2">singleton</td></tr>
  <tr><td><pre>public class S {
    private static S ourInstance = new S();

    public static S getInstance() {
        return ourInstance;
    }

    private S() {
    }
}</pre></td><td><pre>class S

object Instance extends S</pre></td></tr>
  <tr><td><pre>public class Number {

    private int i;

    private static Number ourZero = new Number(0);

    public static Number getZero() {
        return ourZero;
    }

    public Number(int i) {
        this.i = i;
    }
}
</pre></td><td><pre>class Number(val i: Int)

object Zero extends Number(0)</pre></td></tr>
  <tr><th colspan="2"><code>for</code> syntax</td></tr>
  <tr><td>
  Classic Java
  <pre>static List&lt;Integer&gt; duplicate(int i) {
    return Arrays.asList(i, i);
}

List&lt;Integer&gt; is = Arrays.asList(1,2,3);
List&lt;Integer&gt; js = Arrays.asList(4,5,6);

List&lt;Integer&gt; duplicateSums = new ArrayList&lt;&gt;();

for (int i: is) {
    for (int j : js) {
        for (int duplicated : duplicate(i + j)) {
            duplicateSums.add(duplicated);
        }
    }
}

return duplicateSums;
</pre>

Java Streams
<pre>static IntStream duplicate(int i) {
    return IntStream.of(i, i);
}

IntStream is = IntStream.of(1,2,3);
IntStream js = IntStream.of(4,5,6);
IntStream duplicateSums =
    is.flatMap(i -&gt;
      js.flatMap(j -&gt;
        duplicate(i + j)
      )
    );

return duplicateSums.boxed().collect(Collectors.toList());</pre>
</td><td><pre>def duplicate(i: Int): Seq[Int] = Seq(i, i)
val is = Seq(1,2,3)
val js = Seq(4,5,6)
for {
  i <- is
  j <- js
  duplicated <- duplicate(i + j)
} yield duplicated
</pre></td></tr>
  <tr><td><pre>ListenableFuture&lt;Integer&gt; future0;
ListenableFuture&lt;Integer&gt; future1;

// Add the results of two futures.
return Futures.transformAsync(
    future0,
    value0 -&gt;
        Futures.transform(
            future1,
            value1 -&gt; value0 + value1
        )
);</pre></td><td><pre>val future0: Future[Int]
val future1: Future[Int]

// Add the results of two futures.
for {
value0 <- future0
value1 <- future1
} yield value0 + value1</pre></td></tr>
  <tr><th colspan="2"><a href="https://docs.scala-lang.org/overviews/collections/conversions-between-java-and-scala-collections.html">collections</a></th></tr>>
  <tr><th colspan="2"><a href="https://docs.scala-lang.org/overviews/collections/conversions-between-java-and-scala-collections.html">collection conversions</a></th></tr>
  <tr><td><pre>class Integers {
  public static java.util.List&lt;Integer&gt; list;
}</pre></td><td><pre>
import scala.collection.JavaConverters._
val list: Seq[Integer] = Integers.list.asScala</pre></td></tr>
   <tr><td><pre>import scala.collection.JavaConverters;
Collection&lt;String&gt; list =
   JavaConverters.asJavaCollection(Strings.list());</pre></td><td><pre>object Strings {
  val list: Seq[String] = Seq("hi")
}</pre></td></tr>
   <tr><td><pre>// Java can't handle collections of primitives.
import scala.collection.JavaConverters;
Collection&lt;Object&gt; list =
  JavaConverters.asJavaCollection(Integers.list());</pre></td><td><pre>object Integers {
  val list: Seq[Int] = Seq(1)
}</pre></td></tr>
  <tr><th colspan="2">lambda creation</th></tr>
  <tr><td><pre>Function&lt;Integer, String&gt; toString =
  i -> i.toString();</pre></td><td><pre>val toString: Integer => String =
  i => i.toString</pre></td></tr>
  <tr><td><pre>Function&lt;Integer, String&gt; toString;
Integer result = toString.apply(3);</pre></td><td><pre>val toString: Integer => String
val result = toString(3)</pre></td></tr>
  <tr><td><pre>Function&lt;Integer, String&gt; toString =
  Object::toString;</pre></td><td><pre>val toString: Int => String =
  _.toString</pre></td></tr>
  <tr><td><pre>IntFunction&lt;String&gt; toString =
  Integer::toString;</pre></td><td><pre>val toString: Int => String =
  i => i.toString</pre></td></tr>
  <tr><td><pre>Consumer&lt;String&gt; print =
  System.out::println;</pre></td><td><pre>val print: String => Unit =
  println</pre></td></tr>
  <tr><td><pre>IntConsumer print =
  System.out::println;</pre></td><td><pre>val print: Int => Unit =
  println</pre></td></tr>
  <tr><td><pre>Supplier&lt;Integer&gt; read =
  () -> 3;</pre></td><td><pre>val read: Unit -> Integer =
  () => 3</pre></td></tr>
  <tr><td><pre>IntSupplier read =
  () -> 3;</pre></td><td><pre>val read: Unit -> Int =
  () => 3</pre></td></tr>
   <tr><th colspan="2">lambda calls</th></tr>
  <tr><td><pre>Function&lt;Integer, String&gt; toString;
toString.apply(3)</pre></td><td><pre>val toString: Integer => String
toString(3)</pre></td></tr>
  <tr><td><pre>Consumer&lt;String&gt; print;
print.accept("hi");</pre></td><td><pre>val print: String => Unit
print("hi")</pre></td></tr>
  <tr><td><pre>Supplier&lt;Integer&gt; read;
  read.get();</pre></td><td><pre>val read: Unit => Integer
read()</pre></td></tr>
   <tr><th colspan="2"></th></tr
  <tr><td><pre></pre></td><td><pre></pre></td></tr>
</table>
