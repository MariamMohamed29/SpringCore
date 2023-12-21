# SpringCore

## Introduction to Spring Framework

### What is Spring?

Spring Framework is a Java platform that provides comprehensive infrastructure support for developing Java applications. Spring handles the infrastructure so you can focus on your application.
Spring enables you to build applications from “plain old Java objects” (POJOs) and to apply enterprise services non-invasively to POJOs. This capability applies to the Java SE programming model and to full and partial Java EE.

#### Examples of how you, as an application developer, can use the Spring platform advantage:

-Make a Java method execute in a database transaction without having to deal with transaction APIs.

-Make a local Java method a remote procedure without having to deal with remote APIs.

-Make a local Java method a management operation without having to deal with JMX APIs.

-Make a local Java method a message handler without having to deal with JMS APIs.
### Reasons to Use Spring Framework in Projects
There are many reasons for which Spring is one of the best choices for developing our project as it is open-source, stable, and many more. It is one of the most trusted frameworks for building projects or developing enterprise applications when working with the Java tech stack and projects written in Java are more secure and robust.
We’ll discuss reasons to use the Spring Framework in the projects in this repository:
1. **Easy, Simple, and Lightweight**
   Let’s admit that we look for easier things first! Spring is easy to learn and implement which is composed of modules where we can write spring applications normally with interfaces 
    and abstract classes just like java applications.
   Spring helps in coupling and wiring the components which make working with Spring easier and simpler as we can focus more on our application rather than its implementation.
   It is lightweight as we can inject dependencies as per our need without having to include each of them thus saving the project from unnecessary memory utilization.
2. **Builds Secure Web Applications**
   Spring provides security if Spring Security is on the classpath and we can customize the security settings further for basic authentication and prevent vulnerabilities in our project.
3. **MVC Pattern**
   MVC is a pattern and methodology in software design that stands for Model View Controller which helps in separating implementation and business logic so that developers can focus on 
   their code for better performance of the application. In simple words, the view is where requests are received first which are taken by the controller to the corresponding model for 
   results which are then taken to view to show at the front side of the application. This systematic receiving and resolving of requests make MVC-based frameworks a good deal to work 
   with. Spring supports the MVC pattern for developing projects which promotes separation of concerns, and loose coupling which is one of the key features of potential software.
4. **Easy Communication with Databases**
   Databases are an important part of an application as without smooth and easy communication with the database, our application can become plain. Spring ensures easy and effective 
   communication with databases as it has DAO (Data Access Object) functionality which is meant to read and write data to a database. With the support of DAO in Spring, data access 
   related technologies such as Hibernate, JDBC, and JPA make it easier to communicate with databases.
5. **Can be Integrated with Other Frameworks**
   Having a good network of people is considered one of the key points of success in today’s world. Our spring is successful as it has a good network and can be used with other 
   frameworks such as Struts, and Hibernate. This makes it more in demand as one can ease out CRUD operations for databases when Hibernate is integrated with Spring.
6. **Dependency Injection** 
   Dependency is neither good for human beings nor the classes in projects. Dependency Injection helps in decreasing coupling and dependency between classes in Spring projects so that 
   the program becomes maintainable and reusable. Modules of one project can be used effectively in another project like a login page, and registration page which not only saves them 
   time but also promotes code reusability which is one of the important aspects of software development.
7. **Follows Aspect-Oriented Programming** 
   Aspect-Oriented Programming allows us to think differently about the structure of the program by enabling the modularization of concerns. It helps in breaking down the logic into 
   parts known as concerns and the concerns help in dividing the business logic of an application and in increasing the modularity.
8. **Testing becomes easy**
   The feature of dependency injection makes frameworks more testable and this is one of the reasons that Spring is good for testing purposes. Loose coupling also helps in unit testing 
   as this way classes can be tested independently without having to depend on one another. It is not good to test complex projects in one go hence, Spring plays as a good option to 
   develop projects as it is easy to test their functionality.
10. **Handle external resources easily** 
    Spring handles not only internal resources but also external resources efficiently such as property files, image files, and XML files. Resource and ResourceLoader are the interfaces 
    present in Spring to handle external resources.

## Understanding Inversion of Control with Example
Spring IoC (Inversion of Control) Container is the core of Spring Framework. It creates the objects, configures and assembles their dependencies, manages their entire life cycle. The Container uses Dependency Injection(DI) to manage the components that make up the application. It gets the information about the objects from a configuration file(XML) or Java Code or Java Annotations and Java POJO class. These objects are called Beans. Since the Controlling of Java objects and their lifecycle is not done by the developers, hence the name Inversion Of Control.

#### There are 2 types of IoC containers:
-BeanFactory 

-ApplicationContext 

#### The BeanFactory is the most basic version of IoC containers, and the ApplicationContext extends the features of BeanFactory. The followings are some of the main features of Spring IoC,

-Creating Object for us,

-Managing our objects,

-Helping our application to be configurable,

-Managing dependencies

**Implementation:** So now let’s understand what is IoC in Spring with an example. Suppose we have one interface named Sim and it has some abstract methods calling() and data().

```java
// Java Program to Illustrate Sim Interface
public interface Sim 
{
    void calling();
    void data();
}
```
Now we have created another two classes Airtel and Jio which implement the Sim interface and override the interface methods.

```java
// Java Program to Illustrate Airtel Class
 
// Class
// Implementing Sim interface
public class Airtel implements Sim {
 
    @Override public void calling()
    {
        System.out.println("Airtel Calling");
    }
 
    @Override public void data()
    {
        System.out.println("Airtel Data");
    }
}
```
```java
// Java Program to Illustrate Jio Class
 
// Class
// Implementing Sim interface
public class Jio implements Sim{
    @Override
    public void calling() {
        System.out.println("Jio Calling");
    }
 
    @Override
    public void data() {
        System.out.println("Jio Data");
    }
}
```

So let’s now call these methods inside the main method

```java
// Java Program to Illustrate Mobile Class
 
// Class
public class Mobile {
 
    // Main driver method
    public static void main(String[] args)
    {
 
        // Creating instance of Sim interface
        // inside main() method
        // with reference to Jio class constructor
        // invocation
        Sim sim = new Jio();
 
        // Sim sim = new Airtel();
 
        sim.calling();
        sim.data();
    }
}
```

But what happens if in the future another new Sim Vodafone came and we need to change again to the child class name in the code,So we have to do our configuration in the source code. So how to make it configurable? We don’t want to touch the source code of this. The source code should be constant. And how can we make it? Here Spring IoC comes into the picture. So in this example, we are going to use ApplicationContext to implement an IoC container. First, we have to create an XML file and name the file as “beans.xml“.

```java
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xsi:schemaLocation="http://www.springframework.org/schema/beans
       https://www.springframework.org/schema/beans/spring-beans.xsd">
 
  <bean id="sim" class="Jio"></bean>
 
</beans>
```


