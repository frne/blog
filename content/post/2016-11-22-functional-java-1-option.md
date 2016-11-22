+++
date = "2016-11-22T08:22:49+01:00"
draft = true
title = "Functional Java 1 - Options"
tags = [ "fp", "java", "library" ]
categories = [ "Java", "Functional Programming"]
+++

## Preface

This is the first post of my series about functional programming in Java. There's a lot of functional stuff one can do. Everyone knows the Java 8 Lambda expression, but with a little library support, there is way more... In this series, I'll coder som libraries which provide functional paradigms and constructs for Java:

- [FunctionalJava](http://www.functionaljava.org/)
- [JavaSlang](http://www.javaslang.io/)

## Java 8 Optional

There is a native optional type since Java 8, called `Optional<T>`. It's handy and covers the basic need: A typesafe alternative to `Null`.

## Functional Java Option

The [Functional Java library](http://www.functionaljava.org/) has also an `Option<T>` type. It is not something completely different, but in my personal opinion, it's way more flexible and has some nice extra features. The basic operations are heavily inspired by Scala:

```java
Option<String> opt1 = Option.some(new String("foo"));
Option<String> opt2 = Option.none();
Option<String> opt3 = Option.fromNull(new String("foo"));
Option<String> opt4 = Option.fromNull(null);

opt1.isSome() // true
opt2.isSome() // false
opt3.isSome() // true
opt4.isSome() // false
```

