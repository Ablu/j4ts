# J4TS
Java APIs for TypeScript

The goal of J4TS is to implement some Java APIs in TypeScript when it makes sense. It intends to be usefull for the following cases:

- Programmers used to the Java APIs can be more efficient using J4TS than when having to learn basic JavaScript APIs.
- It can ease code sharing between Java and TypeScript/JavaScript (and also hopefully, ease the understanding and relationships between the Java fans and TypeScript/JavaScript ones).
- Typically, J4TS can be used as a runtime for transpilers, so that you can use the Java APIs in your transpiled Java programs. So far, J4TS main target is the [JSweet transpiler](http://www.jsweet.org)|[Github](https://github.com/cincheo/jsweet), but it is not limited to it. In a way, J4TS can be seen as an alternative to GWT's JRE emulation library, but for TypeScript.

J4TS currently covers a very small subset of the Java APIs, and is intended to be completed on-the-fly as more use cases are needed. So feel free to contribute.

## Examples
```TypeScript
import List = java.util.List;
import ArrayList = java.util.ArrayList;
import Set = java.util.Set;
import HashSet = java.util.HashSet;
import Map = java.util.Map;
import HashMap = java.util.HashMap;

var l: List<String> = new ArrayList<String>();
l.add("a");
l.add("b");
l.add("c");
assertEquals("[a, b, c]", l.toString());
assertEquals(l.indexOf("a"), 0);

var s: Set<String> = new HashSet<String>();
s.add("a");
s.add("a");
s.add("b");
s.add("c");
s.add("c");
assertEquals(3, s.size());
assertTrue(s.contains("c"));

var s: Map<String, String> = new HashMap<String, String>();
s.put("a", "aa");
s.put("b", "bb");
s.put("c", "cc");
assertEquals("bb", s.get("b"));
```

## Disclaimer

J4TS is not made for implementing Java semantics in JavaScript. It will be close and mimic Java behavior, but it will never be completely Java. J4TS is full of heuristics and approximations, trying to get the best of it at a reasonable cost. So, programmers using J4TS should not expect to use it for porting complex Java applications (although it may help). On the other hand, J4TS should be fine to share and port small portions of code between Java and TypeScript. Typically, when using J4TS, some business logic may be shared more easily between a Java server and a TypeScript/JavaScript client.

## Contributions

J4TS is meant to serve the public interest and be as open as possible. So anyone is more than welcome to contribute as long as it does not deviate J4TS from its initial goals stated above. When you meet a class or a method that is not supported, please feel free to contribute under the terms of the license.

## How to use

You can use the current JavaScript bundle (runtime): ``js/j4ts.js``. 

From TypeScript, you can compile with ``js/j4ts.d.ts``.

From JSweet, add the candy dependency in your ``pom.xml``.

```xml
<dependency>
	<groupId>org.jsweet.candies</groupId>
	<artifactId>j4ts</artifactId>
	<version>0.0.1-SNAPSHOT</version>
</dependency>
```

## How to build

Use Gulp to generate the JavaScript bundle in the ``js`` directory (required: Gulp and required modules).

```
> gulp clean bundle
```

To build and install the JSweet candy in your local Maven repository (required: Maven).

```
> gulp prepare-jsweet-candy
> cd packaging/jsweet-candy
> mvn clean install
```

## License

J4TS is licensed under the Apache Open Source License version 2.