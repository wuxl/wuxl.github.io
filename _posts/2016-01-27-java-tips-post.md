---
layout: post
title: Java Tips
date: 2016-01-27 16:03:00
---

The issue which is Violation in Java language.

### `equals(Object obj)` and `hashCode()` should be overridden in pairs

According to the Java Language Specification, there is a contract between `equals(Object)` and `hashCode()`:

>If two objects are equal according to the equals(Object) method, then calling the hashCode method on each of the two objects must produce the same integer result.
>It is not required that if two objects are unequal according to the equals(java.lang.Object) method, then calling the hashCode method on each of the two objects must produce distinct integer results.
>However, the programmer should be aware that producing distinct integer results for unequal objects may improve the performance of hashtables.

In order to comply with this contract, those methods should be either both inherited, or both overridden [1].

{% highlight java %}
class MyClass {    // Compliant

  @Override
  public boolean equals(Object obj) {
    /* ... */
  }

  @Override
  public int hashCode() {
    /* ... */
  }

}
{% endhighlight %}

### Throwable and Error should not be caught 

Throwable is the superclass of all errors and exceptions in Java.

Error is the superclass of all errors, which are not meant to be caught by applications.

Catching either Throwable or Error will also catch OutOfMemoryError and InternalError, from which an application should not attempt to recover.

[1]: <http://cwe.mitre.org/data/definitions/581.html>


