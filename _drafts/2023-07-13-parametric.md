---
layout: post
title: "Representation of parametrics "
date: 2023-07-13 12:00:00 
background: '/img/posts/bg-posts.jpg'
author: Thomas Wattebled
---

# Introduction

In Java generic types allow you to write a general, generic class (or method) that works with different types, allowing for code re-use.

But their modeling and how it works can be difficult to understand. Let's take an example.

## Generic class

```Java 
public class ClassA<T>
```
Here, ClassA is a generic class because there is one generic type T. We can't use ClassA without specify the generic type.

``` Java
ClassA<Integer> class1 = new ClassA<Integer> ;
ClassA<String> class2 = new ClassA<String>
```

class1 and class2 are variables of type ClassA, but this time classA doesn't have a generic type but String or Integer. So how do we represent all that ?

![Modelisation_generic](/img/posts/2023-07-13-parametric/Modelisation_generic.png)

We have 5 new traits in our model :
- TParametricEntity is used by all parametric entities it can be a ParametricClass, ParametricMethod, ParametricInterface. 
- TConcretisation allows us to have a link between two TParametricEntity. A TParametricEntity can have one or more concretisations with other TParametricEntity. Each TParametricEntity that is a concretisation of another TParametricEntity has a genericEntity.
- TConcreteParameterType for concrete parameters.
- TGenericParameterType for generic parameters.
- TParameterConcretisation is the same as TConcretisation but instead of two TParametricEntity it has TConcreteParameter and TGenericParameterType. TGenericParameterType can have one or more concretisations and TConcreteParameterType has generics.

A TParametricEntity knows its concrete and generic parameters.

ParameterType uses the TWithInheritance trait because in Java we can do this: ```<T extends Object>``` or ```<? super Number>```. For the first, it means that T can be all subclasses of Object and for the second, it means Number and all its superclasses (Number, Object, Serializable). 
ParameterType also uses the TThrowable trait because we can have a genericException so ParameterType should be considered like it.
```Java
public interface GenericThrower<T extends Throwable> {
    public void doThrow() throws T;
}
```

<br>

### Lets describe an example :

![example](/img/posts/2023-07-13-parametric/exampleParametric.png)

If we take the first class. We have a ParametricClass with one ParameterType name T.

![classA<T>](/img/posts/2023-07-13-parametric/genParametric.png)

For the second class we have a class that extends a parametric class with one parameter named String. String here is a class. This is not a ParameterType anymore.

![classB extends class<String>](/img/posts/2023-07-13-parametric/classB_extends_classA.png)

So what is the link between the two parametric classes and the parameters T and String?

![concretisation](/img/posts/2023-07-13-parametric/concretisation.png)

We have here a Concretisation. ClassA with the parameter T has one concretisation and the parameter T has one parameter Concretisation that is String.

<br> <br>

If we take back our first example:
```Java 
public class ClassA<T>
ClassA<Integer> class1 = new ClassA<Integer> 
ClassA<String> class2 = new ClassA<String>
```
We have 3 ParametricClass, one ParameterType and two types (String and Integer). T is our ParameterType and has two ParameterConcretisations : String and Integer. We can say that T is generic and String or Integer are concrete because we know what they are: classes. ClassA with the ParameterType T (ClassA<T>) has also two concretisations. This is ClassA<Integer> and ClassA<String>. The three different classA know their parameters. T is in genericParameters. String and Integer are in concreteParameters.

A class is generic if it has at least one ParameterType. We can have concretisation of a parametric class that is also generic. See the example below:

``` Java
public class ParametricClass<T, V, K, Z> 

public class ParametricClass2<Z> extends ParametricClass<String, Integer, Integer, Z>
```
The Second ParametricClass has one ParameterType, so the class is generic. The four parameters (T, V, K, Z) has each one concretisation (String, Integer, Integer, Z). Even if Z is still a ParameterType.

ParametricClass2 has for superclass ParametricClass which has for generic Entity ParametricClass with 4 ParameterTypes.

## Generic method 

![methodParametric](/img/posts/2023-07-13-parametric/methodParametric.png)

Let's see what we have here. First of all, we recognize a ParametricClass with one ParameterType. This class has two methods. One is a regular method and the second is a parametricMethod.
The first one isn't generic because when the class is concretized, the ParameterType T will become String, Integer, Animals... and it will be the same for the method.
The parameter of the first method depends on the class and this is not the case for the second method. That is why the second method is generic, not the first one.



## Example with Pharo


```Java 
public classA<T>  
public classB extends classA<String>
```

This is how we can represent this in pharo.

``` smalltalk
classAgen := FamixJavaParametricClass named:'ClassA'.
t := FamixJavaParameterType named:'T'.
classAgen addGenericParameter: t.

classAcon := FamixJavaParametricClass named:'ClassA'.
string := FamixJavaClass named:'String'.
classAgen addConcreteParameter: string.

FamixJavaConcretisation new concreteEntity: classAcon ; genericEntity: classAgen.

FamixJavaParameterConcretisation new concreteParameter: string ; genericParameter: t.

classB := FamixJavaClass named:'ClassB'.
FamixJavaInheritance new subclass: classB ; superclass: classAcon .
```

# Conclusion

In this post, we have seen how generics types are modelled with VerveinJ and Moose for code analysis.