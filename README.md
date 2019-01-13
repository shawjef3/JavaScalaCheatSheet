# Java/Scala Cheet Sheet

<table align="center">
  <tr><th>Java</th><th>Scala</th></tr>
  <tr><th colspan="2">packages</td></tr>
  <tr><td><div class="highlight highlight-source-java"><pre>package me.jeffshaw;</pre></div></td><td><div class="highlight highlight-source-scala"><pre>package me.jeffshaw</pre></div></td></tr>
  <tr><td><div class="highlight highlight-source-java"><pre>import me.jeffshaw.Class;</pre></div></td><td><div class="highlight highlight-source-scala"><pre>import me.jeffshaw.Class</pre></div></td></tr>
  <tr><td><div class="highlight highlight-source-java"><pre>import me.jeffshaw.Class0;
import me.jeffshaw.Class1;</pre></div></td><td><div class="highlight highlight-source-scala"><pre>import me.jeffshaw.Class0
import me.jeffshaw.Class1</pre></div>
or
<div class="highlight highlight-source-scala"><pre>import me.jeffshaw.{Class0, Class1}</pre></div></td></tr>
  <tr><td><div class="highlight highlight-source-java"><pre>import me.jeffshaw.*;</pre></div></td><td><div class="highlight highlight-source-scala"><pre>import me.jeffshaw._</pre></div></pre></td></tr>
  <tr><td></td><td><div class="highlight highlight-source-scala"><pre>import me.jeffshaw.{Class => RenamedClass}</pre></div></td></tr>
  <tr><td></td><td><div class="highlight highlight-source-scala"><pre>import me.jeffshaw.{Class => RenamedClass}</pre></div></td></tr>
  <tr><th colspan="2">classes</td></tr>
  <tr><td><div class="highlight highlight-source-java"><pre>class C {}</pre></div></td><td><div class="highlight highlight-source-scala"><pre>class C</pre></div></td></tr>
  <tr><td><div class="highlight highlight-source-java"><pre>class C {
  public int i;
}</pre></div></td><td><div class="highlight highlight-source-scala"><pre>class C {
  var i: Int = _
}</pre></div></td></tr>
  <tr><td><div class="highlight highlight-source-java"><pre>class C {
  public int i = 0;
}</pre></div></td><td><div class="highlight highlight-source-scala"><pre>class C {
  var i = 0
}</pre></div></td></tr>
  <tr><td><div class="highlight highlight-source-java"><pre>class C {
  public int i;

  public C(int i) {
    this.i = i;
  }
}</pre></div></td><td><div class="highlight highlight-source-scala"><pre>class C(var i: Int)</pre></div>
is shorthand for
<div class="highlight highlight-source-scala"><pre>class C {
  var i: Int = _
  def C(i: Int) {
    this.i = i
  }
}</pre></div></td></tr>
  <tr><td><div class="highlight highlight-source-java"><pre>class C&lt;A&gt; {}</pre></div></td><td><div class="highlight highlight-source-scala"><pre>class C[A]</pre></div></td></tr>
  <tr><td><div class="highlight highlight-source-java"><pre>class C&lt;A extends Comparable&gt; {}</pre></div></td><td><div class="highlight highlight-source-scala"><pre>class C[A <: Comparable]</pre></div></td></tr>
  <tr><td><div class="highlight highlight-source-java"><pre>class C&lt;A extends Comparable, Serializable&gt; {}</pre></div></td><td><div class="highlight highlight-source-scala"><pre>class C[A <: Comparable with Serializable]</pre></div></td></tr>
  <tr><td><div class="highlight highlight-source-java"><pre></pre></div></td><td><div class="highlight highlight-source-scala"><pre>class C[-A]</pre></div></td></tr>
  <tr><td><div class="highlight highlight-source-java"><pre></pre></div></td><td><div class="highlight highlight-source-scala"><pre>class C[+A]</pre></div></td></tr>
  <tr><th colspan="2">methods</td></tr>
  <tr><td><div class="highlight highlight-source-java"><pre>void f(int i) {}</pre></div></td><td><div class="highlight highlight-source-scala"><pre>def f(i: Int): Unit = {}</pre></div>
  or
<div class="highlight highlight-source-scala"><pre>def f(i: Int): Unit = ()</pre></div></td></tr>
  <tr><td><div class="highlight highlight-source-java"><pre>int f(int i) {return i;}</pre></div></td><td><div class="highlight highlight-source-scala"><pre>def f(i: Int): Int = i</pre></div></td></tr>
  <tr><th colspan="2">statics</td></tr>
  <tr><td><div class="highlight highlight-source-java"><pre>class C {
    static int i = 0;
}</pre></div></td><td><div class="highlight highlight-source-scala"><pre>object C {
  var i = 0
}</pre></div></td></tr>
  <tr><td><div class="highlight highlight-source-java"><pre>class C {
    static int f(int i) {
        return i + 1;
    }
}</pre></div></td><td><div class="highlight highlight-source-scala"><pre>object C {
  def f(i: Int): Int = i + 1
}</pre></div></td></tr>
  <tr><th colspan="2">mutability</td></tr>
  <tr><td><div class="highlight highlight-source-java"><pre>int i;</pre></div></td><td><div class="highlight highlight-source-scala"><pre>var i: Int</pre></div></td></tr>
  <tr><td><div class="highlight highlight-source-java"><pre>final int i;</pre></div></td><td><div class="highlight highlight-source-scala"><pre>val i: Int</pre></div></td></tr>
<tr><th colspan="2">immutable data structure</td></tr>
  <tr><td><div class="highlight highlight-source-java"><pre>public class C implements Serializable {
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
</pre></div></td><td><div class="highlight highlight-source-scala"><pre>case class C(c: Int)</pre></div></td></tr>
  <tr><th colspan="2">bean / mutable data structure</td></tr>
  <tr><td><div class="highlight highlight-source-java"><pre>public class C implements Serializable {
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
}
</pre></div></td><td><div class="highlight highlight-source-scala"><pre>case class C(
  @BeanProperty var c: Int
) {
  def this() {
    this(0)
  }
}</pre></div></td></tr>
  <tr><th colspan="2">member access permissions</td></tr>
  <tr><th colspan="2">private</td></tr>
  <tr><td><div class="highlight highlight-source-java"><pre>private int i;</pre></div></td><td><div class="highlight highlight-source-scala"><pre>private var i: Int</pre></div></td></tr>
  <tr><th colspan="2">package private</td></tr>
  <tr><td><div class="highlight highlight-source-java"><pre>int i;</pre></div></td><td><div class="highlight highlight-source-scala"><pre>private[package] var i: Int</pre></div></td></tr>
  <tr><th colspan="2">public</td></tr>
  <tr><td><div class="highlight highlight-source-java"><pre>public int i;</pre></div></td><td><div class="highlight highlight-source-scala"><pre>var i: Int</pre></div></td></tr>
  <tr><th colspan="2">protected</td></tr>
  <tr><td><div class="highlight highlight-source-java"><pre>protected int i;</pre></div></td><td><div class="highlight highlight-source-scala"><pre>protected var i: Int</pre></div></td></tr>
  <tr><th colspan="2">control structures</td></tr>
  <tr><td><div class="highlight highlight-source-java"><pre>return;</pre></div></td><td><div class="highlight highlight-source-scala"><pre>()</pre></div></td></tr>
  <tr><td><div class="highlight highlight-source-java"><pre>return 0;</pre></div></td><td><div class="highlight highlight-source-scala"><pre>0</pre></div></td></tr>
  <tr><td><div class="highlight highlight-source-java"><pre>if (test) {
  doSomething();
} else {
  doSomethingElse();
}</pre></div></td><td><div class="highlight highlight-source-scala"><pre>if (test) {
  doSomething()
} else {
  doSomethingElse()
}</pre></div></td></tr>
  <tr><td><div class="highlight highlight-source-java"><pre>int i = 0;
while (i < 10) {
  i++;
}</pre></div></td><td><div class="highlight highlight-source-scala"><pre>var i = 0
while (i < 10) {
  i += 1
}</pre></div></td></tr>
  <tr><td><div class="highlight highlight-source-java"><pre>int i = 0;
do {
  i++;
} while (i < 10)</pre></div></td><td><div class="highlight highlight-source-scala"><pre>var i = 0
do {
  i += 1
} while (i < 10)</pre></div></td></tr>
  <tr><td><div class="highlight highlight-source-java"><pre>for (int i: collection) {}</pre></div></td><td><div class="highlight highlight-source-scala"><pre>for (i <- collection) {}</pre></div></td></tr>
  <tr><td><div class="highlight highlight-source-java"><pre>for (int i: collection) {
  for (int j: otherCollection) {}
}</pre></div></td><td><div class="highlight highlight-source-scala"><pre>for {
  i <- collection
  j <- otherCollection
} {}</pre></div></td></tr>
  <tr><td><div class="highlight highlight-source-java"><pre>switch (value) {
  case 0:
    break;
  default:
}</pre></div></td><td><div class="highlight highlight-source-scala"><pre>value match {
  case 0 =>
  case _ =>
}</pre></div></td></tr>
  <tr><td><div class="highlight highlight-source-java"><pre>// cases share switch's scope
switch (value) {
  case 0: {
    int i = 0;
    break;
  }
  default: {
    int i = 0;
  }
}</pre></div></td><td><div class="highlight highlight-source-scala"><pre>// cases each have their own scope
value match {
  case 0 =>
    val i = 0;
  case _ =>
    val i = 0;
}</pre></div></td></tr>
  <tr><th colspan="2">data types</td></tr>
  <tr><td><div class="highlight highlight-source-java"><pre>void</pre></div></td><td><div class="highlight highlight-source-scala"><pre>Unit</pre></div></td></tr>
  <tr><td><div class="highlight highlight-source-java"><pre>bool</pre></div></td><td><div class="highlight highlight-source-scala"><pre>Boolean</pre></div></td></tr>
  <tr><td><div class="highlight highlight-source-java"><pre>byte</pre></div></td><td><div class="highlight highlight-source-scala"><pre>Byte</pre></div></td></tr>
  <tr><td><div class="highlight highlight-source-java"><pre>char</pre></div></td><td><div class="highlight highlight-source-scala"><pre>Char</pre></div></td></tr>
  <tr><td><div class="highlight highlight-source-java"><pre>int</pre></div></td><td><div class="highlight highlight-source-scala"><pre>Int</pre></div></td></tr>
  <tr><td><div class="highlight highlight-source-java"><pre>long</pre></div></td><td><div class="highlight highlight-source-scala"><pre>Long</pre></div></td></tr>
  <tr><td><div class="highlight highlight-source-java"><pre>float</pre></div></td><td><div class="highlight highlight-source-scala"><pre>Float</pre></div></td></tr>
  <tr><td><div class="highlight highlight-source-java"><pre>double</pre></div></td><td><div class="highlight highlight-source-scala"><pre>Double</pre></div></td></tr>
  <tr><td><div class="highlight highlight-source-java"><pre>Object</pre></div></td><td><div class="highlight highlight-source-scala"><pre>AnyRef</pre></div></td></tr>
  <tr><td><div class="highlight highlight-source-java"><pre></pre></div></td><td><div class="highlight highlight-source-scala"><pre>Any</pre></div></td></tr>
  <tr><td><div class="highlight highlight-source-java"><pre></pre></div></td><td><div class="highlight highlight-source-scala"><pre>AnyVal</pre></div></td></tr>
  <tr><th colspan="2">arrays</td></tr>
  <tr><td><div class="highlight highlight-source-java"><pre>int[] ints = new int[] {1,2,3};</pre></div></td><td><div class="highlight highlight-source-scala"><pre>var ints = Array(1,2,3)</pre></div></td></tr>
  <tr><td><div class="highlight highlight-source-java"><pre>int[][] ints = new int[][] {{1,2,3},{4,5,6},{7,8,9}};</pre></div></td><td><div class="highlight highlight-source-scala"><pre>var ints = Array(Array(1,2,3), Array(4,5,6), Array(7,8,9))</pre></div></td></tr>
  <tr><td><div class="highlight highlight-source-java"><pre>int[] ints = new int[3];</pre></div></td><td><div class="highlight highlight-source-scala"><pre>var ints = Array.ofDim[Int](3)</pre></div></td></tr>
  <tr><td><div class="highlight highlight-source-java"><pre>int[][] ints = new int[3];
for (int i=0; i<3; i++) {
  ints[i] = new int[3]; 
}</pre></div></td><td><div class="highlight highlight-source-scala"><pre>var ints = Array.ofDim[Int](3, 3)</pre></div></td></tr>
  <tr><td><div class="highlight highlight-source-java"><pre>int[] ints = new int[3];
Arrays.fill(ints, 0);</pre></div></td><td><div class="highlight highlight-source-scala"><pre>var ints = Array.fill(3)(0)</pre></div></td></tr>
  <tr><td><div class="highlight highlight-source-java"><pre>String[] intStrings = new String[3];
for (int i=0; i<3; i++) {
  intStrings[i] = Integer.toString(i);
}</pre></div>
or
<div class="highlight highlight-source-java"><pre>IntStream.range(0, 3).mapToObj(Integer::toString).toArray();</pre></div>
</td><td><div class="highlight highlight-source-scala"><pre>var intStrings = Array.tabulate(3)(_.toString)</pre></div></td></tr>
  <tr><th colspan="2">operations</td></tr>
  <tr><td><div class="highlight highlight-source-java"><pre>&&, ||, !</pre></div></td><td><div class="highlight highlight-source-scala"><pre>&&, ||, !</pre></div></td></tr>
  <tr><td><div class="highlight highlight-source-java"><pre>==, !=</pre></div></td><td><div class="highlight highlight-source-scala"><pre>eq, ne</pre></div></td></tr>
  <tr><td><div class="highlight highlight-source-java"><pre>Object#equals(Object)</pre></div></td><td><div class="highlight highlight-source-scala"><pre>==, !=</pre></div></td></tr>
  <tr><td><div class="highlight highlight-source-java"><pre>&lt;, &gt;, &lt;=, &gt;=</pre></div></td><td><div class="highlight highlight-source-scala"><pre>&lt;, &gt;, &lt;=, &gt;=</pre></div></td></tr>
  <tr><td><div class="highlight highlight-source-java"><pre>+, -, *, /, %</pre></div></td><td><div class="highlight highlight-source-scala"><pre>+, -, *, /, %</pre></div></td></tr>
  <tr><td><div class="highlight highlight-source-java"><pre>&, |, ^, ~, &lt;&lt;, &gt;&gt;, &gt;&gt;&gt;</pre></div></td><td><div class="highlight highlight-source-scala"><pre>&, |, ^, ~, &lt;&lt;, &gt;&gt; &gt;&gt;&gt;</pre></div></td></tr>
  <tr><td><div class="highlight highlight-source-java"><pre>+=, -=, *=, /=, %=, &lt;&lt=, &gt;&gt;=, &amp;=, ^=, |=</pre></div></td><td><div class="highlight highlight-source-scala"><pre>+=, -=, *=, /=, %=, &lt;&lt=, &gt;&gt;=, &amp;=, ^=, |=</pre></div></td></tr>
  <tr><td><div class="highlight highlight-source-java"><pre>++, --</pre></div></td><td></td></tr>
  <tr><td><div class="highlight highlight-source-java"><pre>?:</pre></div>
  example
<code class="java">int i = test ? 0 : 1;</pre></div></td><td><div class="highlight highlight-source-scala"><pre>var i = if (test) 0 else 1</pre></div></td></tr>
  <tr><th colspan="2">io</td></tr>
  <tr><th colspan="2">writing to files or standard error is the same<td></tr>
  <tr><td><div class="highlight highlight-source-java"><pre>System.out.println("hi");</pre></div></td><td><div class="highlight highlight-source-scala"><pre>System.out.println("hi")</pre></div>or<div class="highlight highlight-source-scala"><pre>println("hi")</pre></div></td></tr>
  <tr><td><div class="highlight highlight-source-java"><pre>new BufferedReader(new InputStreamReader(System.in)).readLine();</pre></div></td><td><div class="highlight highlight-source-scala"><pre>io.StdIn.readLine()</pre></div></td></tr>
  <tr><td><div class="highlight highlight-source-java"><pre>for (String line: Files.newBufferedReader(Paths.get("file")).lines().iterator()) {}</pre></div></td><td><div class="highlight highlight-source-scala"><pre>for (line <- Files.newBufferedReader(Paths.get("file")).lines.iterator) {}</pre></div>
or
<div class="highlight highlight-source-scala"><pre>for (line <- io.Source.fromFile("file").getLines()) {}</pre></div></td></tr>
  <tr><th colspan="2">singleton</td></tr>
  <tr><td><div class="highlight highlight-source-java"><pre>public class S {
    private static S ourInstance = new S();

    public static S getInstance() {
        return ourInstance;
    }

    private S() {
    }
}</pre></div></td><td><div class="highlight highlight-source-scala"><pre>class S

object Instance extends S</pre></div></td></tr>
  <tr><td><div class="highlight highlight-source-java"><pre>public class Number {

    private int i;

    private static Number ourZero = new Number(0);

    public static Number getZero() {
        return ourZero;
    }

    public Number(int i) {
        this.i = i;
    }
}
</pre></div></td><td><div class="highlight highlight-source-scala"><pre>class Number(val i: Int)

object Zero extends Number(0)</pre></div></td></tr>
</table>
