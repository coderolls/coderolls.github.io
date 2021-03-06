﻿---
layout: post
title: "How To Convert double To int In Java?"
author: gaurav
image: assets/images/2021-03-02/double-to-int-in-java.webp
categories: [ Java, Core Java, String]
description: "In this article you are going to learn how can we convert a double value to an integer value."
---


In this article, we will see how we can convert a double to an int.

In java programming, you will have a double primitive value (ex 82.14), but to do the further operations you need an int value (ex. 82) so let's see how to convert double to int in java.

There are three ways you can convert double to int. I will list them all below and, then we will see them one by one.

1. convert double to int - using typecasting
2. convert double to int - using `Math.round()`
3. convert double to int - using `Double.IntValue()`

> You may like to visit:
> [How To Convert An Integer To String In Java](https://coderolls.com/convert-int-to-string/)

## 1. convert double to int - using typecasting

We know  `double` is a 64-bit primitive value, and int is a 32-bit primitive value. So, to convert double to int, we can downcast the double value to int.

I have given a simple example below that shows to convert double to int using typecasting.

```java
/**
 * A java program to convert double to int using typecasting 
 * @author Gaurav Kukade at coderolls.com
 **/
public class DoubleToIntUsingTypecasting{

     public static void main(String []args){
        
        double doubleValue = 82.14; // 82.14
        
        System.out.println("doubleValue: "+doubleValue);
        
        //typecase double to int
        int intValue = (int) doubleValue; // 82
        
        System.out.println("intValue: "+intValue);
     }
}
```
Output:
```java
doubleValue: 82.14
intValue: 82
```

The problem with the typecasting is that it will truncate the value after the decimal point. It will not round it.

In the case of 82.14, we will get an int value of 82, which looks ok. But when we have a double value like 82.99, we will get only 82 and loss the 0.99 that is ~1.

It may create an issue in your calculations.

In the case of 82.99, it should be rounded to 83 and then converted to int.

It is not possible with typecasting, but our next solution can achieve it.

## 2. convert double to int  - using [`Math.round()`](https://docs.oracle.com/javase/8/docs/api/java/lang/Math.html#round-double-)

[`Math.round()`](https://docs.oracle.com/javase/8/docs/api/java/lang/Math.html#round-double-) method will round the floating-point value to the nearest long value. Then we can typecast it to the int.

I have given a simple java program below that shows how to convert double to int using the [`Math.round()`](https://docs.oracle.com/javase/8/docs/api/java/lang/Math.html#round-double-)  method.

```java
/** 
 * A java program to convert double to int using 
 * Math.round() method 
 * @author Gaurav Kukade at coderolls.com
 **/
public class DoubleToIntUsingRoundMethod{

     public static void main(String []args){
        
        // case 1
        double doubleValue = 82.14; // 82.14
        
        System.out.println("doubleValue: "+doubleValue);
        
        //typecase double to int
        int intValue = (int) Math.round(doubleValue); // 82
        
        System.out.println("intValue: "+intValue);
        
        System.out.println();
        
        // case 2
        double nextDoubleValue = 82.99; // 

        
        System.out.println("nextDoubleValue: "+nextDoubleValue);
        
        // Math.round(nextDoubleValue) returns long value
        //typecase long to int
        int nextIntValue = (int) Math.round(nextDoubleValue); // 83
        
        System.out.println("nextIntValue: "+nextIntValue);              
     }
}
```
Output:

```java
doubleValue: 82.14
intValue: 82

nextDoubleValue: 82.99
nextIntValue: 83
```
## 3. convert double to int - using [`Double.IntValue()`](https://docs.oracle.com/javase/8/docs/api/java/lang/Double.html#intValue--)


In this way, we will convert the double primitive value to the `Double` wrapper class, and then we can use the `intValue()` method of the `Double` wrapper class.

This method does not round the value before converting it to the int value. It will remove the digits after the decimal point.

I have given a simple java program below that shows how to convert double to int using the [`Double.IntValue()`](https://docs.oracle.com/javase/8/docs/api/java/lang/Double.html#intValue--) method.

```java
/**
 * 
 * A java program to convert double to int using 
 * Double.intValue() method  
 * @author Gaurav Kukade at coderolls.com
 * 
 **/
public class DoubleToIntUsingIntValueMethod{

     public static void main(String []args){

        double doubleValue = 82.14; // 82.14
        
        System.out.println("doubleValue: "+doubleValue);
        
        //create Double wrapper object
        Double doubleValueObject = new Double(doubleValue);
        
        
        //typecase double to int
        int intValue = doubleValueObject.intValue(); // 82
        
        System.out.println("intValue: "+intValue);
     }
}
```

Output:
```java
doubleValue: 82.14
intValue: 82
```
## Conclusion

We can convert double to int in java using the three ways given below.

**1. convert double to int - using typecasting**

In this method we typecast the double value to int as give below,
```java
int intValue = (int) Math.round(doubleValue);
```
But in this way, we will lose the value after the decimal point. It will not do the rounding before converting double to int.
   
**2. convert double to int - using [`Math.round()`](https://docs.oracle.com/javase/8/docs/api/java/lang/Math.html#round-double-) **


In this way, we use the [`Math.round()`](https://docs.oracle.com/javase/8/docs/api/java/lang/Math.html#round-double-)  method for the rounding purpose. 

[`Math.round()`](https://docs.oracle.com/javase/8/docs/api/java/lang/Math.html#round-double-)  method round the double value to the nearest long, and then we can typecast long to the int as given below.
```java
int nextIntValue = (int) Math.round(nextDoubleValue);
```
**3. convert double to int - using [`Double.IntValue()`](https://docs.oracle.com/javase/8/docs/api/java/lang/Double.html#intValue--)**

In this way, we convert the `double` value to the `Double` wrapper class, and then we use the [`Double.IntValue()`](https://docs.oracle.com/javase/8/docs/api/java/lang/Double.html#intValue--) method to get the int value.

```java
//create Double wrapper object
Double doubleValueObject = new Double(doubleValue);
        
//typecase double to int
int intValue = doubleValueObject.intValue(); 
```
In this way also we will lose the digits after the decimal points.

So this is how we do convert a double to int in java. You can check all three ([DoubleToIntUsingTypecasting.java](https://github.com/coderolls/blogpost-coding-examples/blob/main/java-basic/DoubleToIntUsingTypecasting.java), [DoubleToIntUsingRoundMethod.java](https://github.com/coderolls/blogpost-coding-examples/blob/main/java-basic/DoubleToIntUsingRoundMethod.java), [DoubleToIntUsingIntValueMethod.java](https://github.com/coderolls/blogpost-coding-examples/blob/main/java-basic/DoubleToIntUsingIntValueMethod.java)) programs on GitHub 

You can read more about [string to int](https://coderolls.com/convert-int-to-string/) and [int to string](https://coderolls.com/convert-string-to-int/) conversion.

-------
You can visit my [YouTube channel 'coderolls'](https://www.youtube.com/channel/UCl31HHUdQbSHOQfc9L-wo3w?view_as=subscriber?sub_confirmation=1) to find more video tutorials.

If you found this article worth, support me by  [giving a cup of Coffee ☕](https://www.paypal.me/GauravKukade)

### Related Articles

- [How To Convert An Integer To String In Java](https://coderolls.com/convert-int-to-string/)

- [How to convert String to Integer in Java](https://coderolls.com/convert-string-to-int/)

- [How To Convert StringBuilder To String In Java?](https://coderolls.com/convert-stringbuilder-to-string-in-java/)

- [How Do I Compare Strings In Java](https://coderolls.com/compare-strings-in-java/)

-  [How To Reverse A String In Java (5 ways)](https://coderolls.com/reverse-a-string-in-java/)




