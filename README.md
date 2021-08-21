# Best-description-on-3-main-features-of-Java-OOP-language-Encapsulation-Inheritance-Polymorphism
Due to these three features have a high occurrence rate on interviews from many comps, I decide to summary my knowledge.  Encapsulation Inheritance Polymorphism


#Three main features of OOP language. 
___
PREFACE:
(you can just skip this section to Introduction XD )

   Okay, Java and cpp are the language that I learn from my school, though this summer I receive an email from my professor that we "had better" to have some expreience on C. (And I use fews week to be acquainted with this. OMG) 

   And, we know those two languages are __Object Oriented Programming__ languages. So they have three features that are different from Procedure-Oriented Language (like C, so far I have learnt). 

   Due to these three features have a high occurrence rate on interviews from many comps, I decide to summary my knowledge. 

   This blog is based on the language of JAVA, and you should know there are still difference amoung all OOP languages. And in this blog I will try to use "my word" and my thinking to describe what they are and why they exist, how to use them. Please correct me if there is any wrong in my blog. Thank you!

___
##Introduction
1. Encapsulation
2. Inheritance
3. Polymorphism

___
###Encapsulation: What Why How


**1. Defination (What):**

   **Put the objects which have same features or, belongs to the same class together, and pack them well.**

   So you know in the company, there are lots of departments that led by different managers or supervisors. For example, we have `IT_Department` class and `HR_Department` class. 

```java
class HR_Department{

    private String Manager;
    private String[] Dep_Members;

    HR_Department(String manager_name){// constructor of HR_Dep
        Manager = manager_name;
    }

    private void employ(){
        System.out.println("Our company need to employ a new employee.");
    }
    private void dismissal(){
        System.out.println("We decide to dismissal someone...");
    }
}

class IT_Department{

    private String Manager;
    private String[] Dep_Members;

    IT_Department(String manager_name){// constructor of IT_Dep
        Manager = manager_name;
    }

    private void Access_Database(){
        System.out.println("Our IT Department can access database of our company.");
    }
    private void Power_outage(){
        System.out.println("IT Department decide to shut down the power for fixing problems.");
    }
}

class Google_Inc{
    private IT_Department it_Dep;
    private HR_Department hr_Dep;

    Google_Inc(String IT_Manager_Name,String HR_Manager_Name){// constructor of Google_Inc
        it_Dep = new IT_Department(IT_Manager_Name);
        hr_Dep = new HR_Department(HR_Manager_Name);

        System.out.println("Google Inc is established successfully!");
    }
}

public class Test {

    public static void main(String[] args) {
        // set up a company call newGoogle_Inc XD
        Google_Inc google_Inc = new Google_Inc("Jack", "Rose");
    }
}
```
   If you are CEO of this company, you have to employ some managers to help you manage these different departments, and of course you require any department work in perfect order and help each other
. 


**2. Significance (Why):**

   **You can easily imagine that, how messy this scenario would be if we didn't have access to every piece of data in any class.**

   I believe, you can't stand it when HR employee turns off the power without checking in with THE IT department.  (even I never work for any companys XD) It's dangerous and out of line anywhere.

  So the existance of Encapsulation shows its importance right now. The example of company is also suitable for any program's, code's, data's management. It's dangerous  while after you design a program, some of your users could access your data and edit them. 

  So for Java, we usually "pack" our CLASS (data) well through using ***Permission Modifier***.
   1.`public`
   2.`protected` (default)
   3.`private` (most used to modify class and variable, as you can see on previous code block)

Obviously, you can realize that, if you correctly use the 
permission modifier, you can realize the **advantages** of your code:

1.Isolate important variables(vars) or functions(funcs)
2.Conveniently access vars or funcs
3.Increase the importance
4.Enhance the security

And of course, these advantages also cause the code being much more harder to access and leading you spending more steps to access them.


**3. Implement of Encapsulation(HOW):**

Before using them, you need to know the range of different modified vars or funcs that could be accessed.

| Modify | Same class | Same package | Sub class | All class|
| ------------- |:-------------:| -----:| -----:| -----:|
| private   | Yes |     |     |     |
| default   | Yes | Yes | Yes |     |
| protected | Yes | Yes | Yes |     |
| public    | Yes | Yes | Yes | Yes |

**In some way, `protected` equals to default.**

Eg: You can not access manager name of HR department directly by assign `=`:
![image](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/avjpflv118l1irlqv0ne.png)

So, you need to set up some functions called "Getters" and "Setters":

```java
class IT_Department{

    private String Manager;
    private String[] Dep_Members;

    IT_Department(String manager_name){// constructor of IT_Dep
        Manager = manager_name;
    }

    String getManager(){ // a classic getter function
        //return manager's name
        return Manager;
    }
    void setManager(String name){// a classic setter function
        //set name to manager's name
        this.Manager = name;
    }

    private void Access_Database(){
        System.out.println("Our IT Department can access database of our company.");
    }
    private void Power_outage(){
        System.out.println("IT Department decide to shut down the power for fixing problems.");
    }
}
```

Hence, you can realize, the implement of encapsulation is abstract in code. We prefer to call encapsulation a phenomenon or a feature. If you have a clear and strict frame of code, your codes will look so GOOD and COMFORTABLE.

In main function:
```java
public static void main(String[] args) {
        // set up a company call newGoogle_Inc
        Google_Inc google_Inc = new Google_Inc("Jack", "Rose");

        String name = google_Inc.it_Dep.getManager(); // assign "Jack" to name.
        google_Inc.it_Dep.setManager("Ben");// assign "Ben" to IT Department's manager
    }
```
___


###Inheritance : W W H


**1. Defination (What):**
Key word: `extend`
 
When multiple classes have common attributes (member variables) and behavior (member methods), these common parts are extracted and defined in a public class. Other classes and classes can form an inheritance relationship with this public class, so that there is no need to redefine the public part in multiple classes! This common class is the parent class, also known as the superclass or base class, and the other classes are the subclasses. Subclasses can access non-private member variables of the parent class directly, and private member variables of the parent class can be accessed using the super.get() method.

Now we have the codes at the following:
```java
class Father{
    String car = "Toyota";
    String books = "Harry Potter";
}

class Son extends Father{ // son extends from his father
    
}

public class Test {

    public static void main(String[] args) {
        Father Howard_Stark = new Father();
        Son Tony_Stack = new Son();
        
        System.out.println(Tony_Stack.car);
    }
}
```

Seems like son has nothing. However, once the son extends from his father, Tony now could drive the car from his father and read the books, which his father "confer" to him.

```java
public class Test {

    public static void main(String[] args) {
        Father Howard_Stark = new Father();
        Son Tony_Stack = new Son();

        System.out.println(Tony_Stack.car); // output: Toyota
        System.out.println(Tony_Stack.books);// output: Harry Potter
    }
}
```

Some features that you should pay attention about the Inheritance in Java:

1. Every sub class is prowerful than base class, which means sub class would have or cover more vars and funcs than father class has. (Of course, Iron man Tony is much more greater than his father Howard haha)

2. Even son extends from his father, son could not "change" the feature of his father. The reason why son could not change his father's feature is that, father and son are two independent instances of `class Son` and `class Father`.

```java
public class Test {

    public static void main(String[] args) {
        Father Howard_Stark = new Father();
        Son Tony_Stack = new Son();

        Tony_Stack.car = "Mercedes";//Tony changes his car to Mercedes, but could not change Howard's car.

        System.out.println(Howard_Stark.car); // output: Toyota
        System.out.println(Tony_Stack.car); // output: Mercedes
    }
}
```
Hence, what Tony has in the future does not Howard's business, including his Mark One and Mark Two. That's why son class is absolutely greater than father class.

```java
class Father{
    String car = "Toyota";
    String books = "Harry Potter";
}

class Son extends Father{ // son extends from his father
    String suit1 = "Mark One";
    String suit2 = "Mark Two";
}
```

3. Java is single inheritance, not multiple inheritance (unlike C++). However, it is possible to build multi-level subclasses of inheritance.

Like Tony extends from Howard, Morgan Stark (Tony's daughter) extends from Tony, but Morgan could not extend from Howard and Tony at the same time.

Tony_Stark <-(extends)-- Howard_Stark
Morgan_Stark <-(extends)-- Tony_Stark

Morgan_Stark <--X-- Howard_Stark, Tony_Stark 



**2. Significance(Why):**
1. If a class want to get a same function from another class, it can set up an inheritance. (Save your time to coding, and increase the reusing rate of code)

2.Encapsulation and inheritance are the prerequisites for polymorphism implementation.

Of course, when you edit the feature of father class, the common features that the son has would be changed too, unless the son change these common features independently.


**3. Implementation(How):**

It is the best time to implement inheritance among classes:

1. When those classes have many properties in common.
2. When there are obviously relationship among those classes (like `class animals` includes `class dog` and `class cat`, so `class cat` and `class dog` extends the proteries from `class animals`).

After knowing when to use inheritance, you can try to build up the relationship and have a rough frame in your mind.

I'm going to talk about the six points of inheritance.


1.When construct an instance of sub class, the complier will invoke the constructor of base class first, and then invoke the constuctor of sub class.

```java
class Father{
    String car = "Toyota";
    String books = "Harry Potter";

    Father(){
        System.out.println("Father's constructor invoked");
    }
}

class Son extends Father{ // son extends from his father
    String suit1 = "Mark One";
    String suit2 = "Mark Two";

    Son(){
        System.out.println("Son's constructor invoked");
    }
}

public class Test {
    
    public static void main(String[] args) {
        Son Tony_Stack = new Son();
    }
}
```
Output:

>Father's constructor invoked
>Son's constructor invoked



2.`class Object` is the father class of any class in JAVA.

Hence, every instance (object) in Java is the polymorphism of instance of `class Object`.

3.The constructor of a subclass runs super () first, regardless of whether it has arguments or how many;

`super();` equals to default constructor of father class. So you can either explicitly or implicitly call `super()` in the any constructor of sub class.
```java
class Father{
    String car = "Toyota";
    String books = "Harry Potter";

    // where the super() is.
    Father(){
        System.out.println("Father's constructor invoked");
    }

    Father(String car){
        this.car = car;
    }
}

class Son extends Father{ // son extends from his father
    Son(){
        //super(); default
        System.out.println("Son's constructor invoked");
    }

    Son(String book){
        //super(); default
        this.books = book;
    }
}
```

4.Properties that are private to the parent class are not directly accessible to the subclass in test.java, even if the subclass inherits them. 

You can specify the subclass's parameter-constructor only by calling the parent's parameter-constructor. For properties that are not private to the parent class, the child class object can invoke directly.

```java
class Father{
    String car = "Toyota";
    String books = "Harry Potter";
    private String bank_account = "123456"; 
    Father(){
        System.out.println("Father's constructor invoked");
    }

    Father(String car){
        this.car = car;
    }
}

class Son extends Father{ // son extends from his father
    
    Son(){
        //super(); default
        System.out.println("Son's constructor invoked");
    }
    
}

public class Test {

    public static void main(String[] args) {
        Son Tony_Stack = new Son();
        Tony_Stack.bank_account = "111111";// error reported: 'bank_account' has private access in 'test.Father'!!!
    }
}
```

Due to the limitation of the paragraph, here are all my knowledge of Inheritance and, there will be more features' details in Polymorphism Section.

___


###Polymorphism:

Finally, I begin to write about POLYMORPHISM section. This section needs me get much more familier with the core knowledge of *Three Main Features Of Java*.

Inheritance maybe not the most popular in code, but the most important part of programming (at least, I think so XD).


**1. What is Polymorphism:**

**Polymorphism is the implementation of an object having different manifestations.**

For example, pressing the same button "ENTER" in different applications, computer will show up different reactions, like acting 
 "Line Feed" function in Word application, acting "Send" function after you type the text in chat box, etc. Just like invoking the same function, pressing "ENTER" button plays an different roles in different applications. This is also kind of Polymorphism.


**2. Significance of Polymorphism :**

1. Remove coupling between classes
2. Replaceability
3. Scalability
4. Working as interface (like a real `interface` in Java)
5. Flexibility
6. Simplicity


Before describing all of its significance, there are hree necessary conditions for the existence of polymorphisms that you should know:

1. The implementance of inheritance: So you can see, the implementance of polymorphsm is also the implementance of 
2. Override
3. An reference of father class points to an object of a sub class: `Parent p = new Child();`

Now we have classes in our program:
![2384ed46c6540cea9eb1415086bf8c89_2DAC601E-70D8-4B3C-86CC-7E4972FC2466](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/6env33zyq3ir8dfw7p1q.jpg)
 

And we have codes for these:
```java
class Shape {
    void draw() {}// is overridden
}

class Circle extends Shape {
    void draw() {//override function draw() of class Shape
        System.out.println("Circle.draw()");
    }
}

class Square extends Shape {
    void draw() {//override function draw() of class Shape
        System.out.println("Square.draw()");
    }
}

class Triangle extends Shape {
    void draw() {//override function draw() of class Shape
        System.out.println("Triangle.draw()");
    }
}
```

When a method is called in polymorphic mode, it is first checked to see if the method exists in the parent class. If it does not, a compile error occurs. If so, call the method of the same name in the subclass. The phenomenon of calling a function in a subclass with the same name as the one of father class, but showing different results is called Override.

![image](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/krn1ru5f51j9apo77z74.png)

The best way to demonstrate these 6 advantages is to look at the following code:
```java
abstract class Animal {// Abstraction
    abstract void eat();
}

class Cat extends Animal {
    public void eat() {// Interface
        System.out.println("Eat fish.");
    }
    public void work() {
        System.out.println("Catch mouse.");
    }
}

class Dog extends Animal {
    public void eat() {
        System.out.println("Eat bone.");
    }
    public void work() {
        System.out.println("Guard.");
    }
}

public class Test {

    public static void main(String[] args) {
        show(new Cat());  // Invoke the show() through the object of class Cat
        show(new Dog());  // Invoke the show() through the object of class Cat

        Animal a = new Cat();  // Upcasting
        a.eat();               // Invoke eat() of class Cat
        Cat c = (Cat)a;        // Downcasting
        c.work();        // Invoke work() of class Cat
    }

    public static void show(Animal a)  {
        a.eat();
        // Judging the class type
        if (a instanceof Cat)  {  // What a cat does
            Cat c = (Cat)a;
            c.work();
        } else if (a instanceof Dog) { // What a dog does
            Dog c = (Dog)a;
            c.work();
        }
    }
}
```

And you can see the output:

>Eat fish.
>Catch mouse.
>Eat bone.
>Guard.
>Eat fish.
>Catch mouse.



**3. How to implement Polymorphism:**


1. Override: 

**Override exists for polymorphisms.**


We've already discussed method overrides, which are methods that can be overridden by a sub class.

When a subclass object calls an overridden method, the method in the subclass is called, not the overridden method in the superclass.

To call an overridden method in a parent class, you must use the `super` keyword.


2. Interface

Interfaces in Java are similar to interfaces in life, which are collections of method characteristics, but no method implementation. See the [Java Interfaces](https://www.tutorialspoint.com/java/java_interfaces.htm) section for details.

3. Abstract classes and abstract functions (vitural function)

**Virtual functions also exist for polymorphisms.**


Of course, the implementation of polymorphism is not only about the interation among classes. It also can be implemented by `abstract function()` and `abstract class {} `(like the vitural func() in c++). 

___

###Last but not least


Those concepts of `abstract` and `override` could be written in another blogs. However, this blog is the first blog of mine, I hope I could get some feedbacks and advice from our members of DEV community, and then move forward again.

Your advice and comments are the power of my moving forward. Thank you for your reading.


***Don't know how good you will be if you don't push yourself.***
Ricky Ruan:

E-mail: yruan@umass.edu
