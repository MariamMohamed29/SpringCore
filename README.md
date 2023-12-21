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
**Explanation:** In the beans.xml file, we have created beans. So inside the id, we have to pass the unique id and inside the class, we have to pass the Class name for which you want to create the bean. Later on, inside the main method, we can tweek it out that will be described in the upcoming program.

```java
import org.springframework.context.ApplicationContext;
import org.springframework.context.support.ClassPathXmlApplicationContext;
 
public class Mobile {
    public static void main(String[] args) {
        // Using ApplicationContext tom implement Spring IoC
        ApplicationContext applicationContext = new ClassPathXmlApplicationContext("beans.xml");
         
        // Get the bean
        Sim sim = applicationContext.getBean("sim", Sim.class);
         
        // Calling the methods
        sim.calling();
        sim.data();
    }
}
```
**Output:**

```java
Jio Calling
Jio Data
```
## BeanFactory
The first and foremost thing when we talk about spring is dependency injection which is possible because spring is actually a container and behaves as a factory of Beans. Just like the  BeanFactory interface is the simplest container providing an advanced configuration mechanism to instantiate, configure, and manage the life cycle of beans. Beans are Java objects that are configured at run-time by Spring IoC Container. BeanFactory represents a basic IoC container which is a parent interface of ApplicationContext. BeanFactory uses Beans and their dependencies metadata to create and configure them at run-time. BeanFactory loads the bean definitions and dependency amongst the beans based on a configuration file(XML) or the beans can be directly returned when required using Java Configuration. There are other types of configuration files like LDAP, RDMS, properties files, etc. BeanFactory does not support Annotation-based configuration whereas ApplicationContext does.
### Procedure:
1-Creating a Spring project using start.spring.io.

2-Creating a POJO class.

3-Configure the Student bean in the bean-factory-demo.xml file.

4-Writing it to application class.

### Implementation:

**Step 1:** Bean Definition: Create a Student POJO class.
```java
// Java Program where we are
// creating a POJO class

// POJO class
public class Student {

  // Member variables
  private String name;
  private String age;

  // Constructor 1
  public Student() {
  }

  // Constructor 2
  public Student(String name, String age) {
    this.name = name;
    this.age = age;
  }

  // Method inside POJO class
  @Override
  public String toString() {

    // Print student class attributes
    return "Student{" + "name='" + name + '\'' + ", age='" + age + '\'' + '}';
  }
}
```
**Step 2:** XML Bean Configuration: Configure the Student bean in the bean-factory-demo.xml file.XML
```java
<?xml version = "1.0" encoding="UTF-8"?>
<beans xmlns = "http://www.springframework.org/schema/beans"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xsi:schemaLocation = "http://www.springframework.org/schema/beans
       https://www.springframework.org/schema/beans/spring-beans.xsd">
            
    <bean id="student" class = "com.gfg.demo.domain.Student">
       <constructor-arg name="name" value="Tina"/>
       <constructor-arg name="age" value="21"/>
    </bean>
</beans>
```
**Step 3:** Main Class
```java
// Application class 
@SpringBootApplication

// Main class
public class DemoApplication {

  // Main driver method
  public static void main(String[] args) {

    // Creating object in a spring container (Beans)
    BeanFactory factory = new ClassPathXmlApplicationContext("bean-factory-demo.xml");
    Student student = (Student) factory.getBean("student");

    System.out.println(student);
  }
}
```
**Output:**
```java
Student{name='Tina', age='21'}
```
##  ApplicationContext
ApplicationContext belongs to the Spring framework. Spring IoC container is responsible for instantiating, wiring, configuring, and managing the entire life cycle of beans or objects. BeanFactory and ApplicationContext represent the Spring IoC Containers. ApplicationContext is the sub-interface of BeanFactory. It is used when we are creating an enterprise-level application or web application. ApplicationContext is the superset of BeanFactory, whatever features provided by BeanFactory are also provided by ApplicationContext.
### ApplicationContext Implementation Classes
There are different types of Application containers provided by Spring for different requirements as listed below which later onwards are described alongside with declaration,Containers are as follows:

1-AnnotationConfigApplicationContext container 

2-AnnotationConfigWebApplicationContext

3-XmlWebApplicationContext

4-FileSystemXmlApplicationContext

5-ClassPathXmlApplicationContext

**Example**

Assume you have a Car class with properties:
```java
public class Car {
    private String brand;
    private String model;

    // getters and setters
}
```
Define a bean for this class in an XML configuration file (beans.xml):

```java
<beans xmlns="http://www.springframework.org/schema/beans"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xsi:schemaLocation="http://www.springframework.org/schema/beans http://www.springframework.org/schema/beans/spring-beans.xsd">

    <bean id="myCar" class="com.example.Car">
        <property name="brand" value="Toyota"/>
        <property name="model" value="Camry"/>
    </bean>

</beans>
```
Access the ApplicationContext in a Java application:

```java
import org.springframework.context.ApplicationContext;
import org.springframework.context.support.ClassPathXmlApplicationContext;

public class MainApp {

    public static void main(String[] args) {
        // Load the application context
        ApplicationContext context = new ClassPathXmlApplicationContext("beans.xml");

        // Get the car bean
        Car myCar = (Car) context.getBean("myCar");

        // Use the car
        System.out.println("Brand: " + myCar.getBrand());
        System.out.println("Model: " + myCar.getModel());
    }
}
```


## Dependency Injection with Example
Dependency Injection is the main functionality provided by Spring IOC(Inversion of Control). The Spring-Core module is responsible for injecting dependencies through either Constructor or Setter methods. The design principle of Inversion of Control emphasizes keeping the Java classes independent of each other and the container frees them from object creation and maintenance. These classes, managed by Spring, must adhere to the standard definition of Java-Bean. Dependency Injection in Spring also ensures loose-coupling between the classes.
### Need for Dependency Injection:
Suppose class One needs the object of class Two to instantiate or operate a method, then class One is said to be dependent on class Two. Now though it might appear okay to depend a module on the other but, in the real world, this could lead to a lot of problems, including system failure. Hence such dependencies need to be avoided.

Spring IOC resolves such dependencies with Dependency Injection, which makes the code easier to test and reuse. Loose coupling between classes can be possible by defining interfaces for common functionality and the injector will instantiate the objects of required implementation. The task of instantiating objects is done by the container according to the configurations specified by the developer.
### Types of Spring Dependency Injection:
There are two types of Spring Dependency Injection. They are:

**1-Setter Dependency Injection (SDI):** This is the simpler of the two DI methods. In this, the DI will be injected with the help of setter and/or getter methods. Now to set the DI as SDI in the bean, it is done through the bean-configuration file For this, the property to be set with the SDI is declared under the <property> tag in the bean-config file.

```java
package com.geeksforgeeks.org; 
  
import com.geeksforgeeks.org.IGeek; 
  
public class GFG { 
  
    // The object of the interface IGeek 
    IGeek geek; 
  
    // Setter method for property geek 
    public void setGeek(IGeek geek) 
    { 
        this.geek = geek; 
    } 
}
```
Setting the SDI in the bean-config file:
```java


<beans 
xmlns="http://www.springframework.org/schema/beans"
xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
xsi:schemaLocation="http://www.springframework.org/schema/beans 
http://www.springframework.org/schema/beans/spring-beans-2.5.xsd"> 
  
    <bean id="GFG" class="com.geeksforgeeks.org.GFG"> 
        <property name="geek"> 
            <ref bean="CsvGFG" /> 
        </property> 
    </bean> 
      
<bean id="CsvGFG" class="com.geeksforgeeks.org.impl.CsvGFG" /> 
<bean id="JsonGFG" class="com.geeksforgeeks.org.impl.JsonGFG" /> 
          
</beans>
```
**2-Constructor Dependency Injection (CDI):** In this, the DI will be injected with the help of contructors. Now to set the DI as CDI in bean, it is done through the bean-configuration file For this, the property to be set with the CDI is declared under the <constructor-arg> tag in the bean-config file.
**Let us take the same example as of SDI**
```java
package com.geeksforgeeks.org; 
  
import com.geeksforgeeks.org.IGeek; 
  
public class GFG { 
  
    // The object of the interface IGeek 
    IGeek geek; 
  
    // Constructor to set the CDI 
    GFG(IGeek geek) 
    { 
        this.geek = geek; 
    } 
}
```
Setting the CDI in the bean-config file:

```java
<beans 
xmlns="http://www.springframework.org/schema/beans"
xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
xsi:schemaLocation="http://www.springframework.org/schema/beans 
http://www.springframework.org/schema/beans/spring-beans-2.5.xsd"> 
  
    <bean id="GFG" class="com.geeksforgeeks.org.GFG"> 
        <constructor-arg> 
            <bean class="com.geeksforgeeks.org.impl.CsvGFG" /> 
        </constructor-arg> 
    </bean> 
      
<bean id="CsvGFG" class="com.geeksforgeeks.org.impl.CsvGFG" /> 
<bean id="JsonGFG" class="com.geeksforgeeks.org.impl.JsonGFG" /> 
          
</beans>
```
## Setter Injection with Collection
Dependency Injection is the main functionality provided by Spring IOC(Inversion of Control). The Spring-Core module is responsible for injecting dependencies through either Constructor or Setter methods. In Setter Dependency Injection(SDI) the dependency will be injected with the help of setters and getters methods. A bean-configuration file is used to set DI as SDI in the bean. For this, the property to be set with the SDI is declared under the <property> tag in the bean-config file.

A Collection in java is a group of individual objects. Spring framework provides us facility of Setter injection using the following Collections:

-List
-Map
-Set
### Implementation:
**1. Company.java**
```java

// Java program to Illustrate Company Class
 
package com.geeksforgeeks.org;
 
// Importing required classes
import java.util.*;
 
// Company Class
class Company {
 
    // Class data members
    private String companyName;
    private List<String> employees;
 
    // Setter
    public void setCompanyName(String companyName)
    {
        this.companyName = companyName;
    }
 
    // Setter
    public void setEmployees(List<String> employees)
    {
        this.employees = employees;
    }
 
    // Getter
    public String getCompanyName() { return companyName; }
 
    // Getter
    public List<String> getEmployees() { return employees; }
 
    // Method
    public void display()
    {
        System.out.println("Company: " + companyName);
        System.out.println("Employee list: " + companyName);
 
        // Iterating over using for each loop
        for (String employee : employees) {
            System.out.println("-" + employee);
        }
    }
}
```
**2. applicationContext.xml**
```java

<?xml version="1.0" encoding="UTF-8"?>  
<beans 
    xmlns="http://www.springframework.org/schema/beans" 
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
    xmlns:p="http://www.springframework.org/schema/p" 
    xsi:schemaLocation="http://www.springframework.org/schema/beans  
     http:www.springframework.org/schema/beans/spring-beans-3.0.xsd">  
   
    <bean id="company" class="com.geeksforgeeks.org.Company">  
        <property name="companyName" value="Penta-b"></property>  
        <property name="employees">
            <list>
                 <value>"John"</value>
                <value>"Max"</value>
                <value>"Sam"</value>
             </list>
         </property>
    </bean>  
</beans>
```
**3. Main.java**
```java

// Java Program to Illustrate Application Class
 
package com.geeksforgeeks.org;
 
// Importing required classes
import org.springframework.beans.factory.BeanFactory;
import org.springframework.beans.factory.xml.XmlBeanFactory;
import org.springframework.context.ApplicationContext;
import org.springframework.context.support.ClassPathXmlApplicationContext;
import org.springframework.core.io.ClassPathResource;
import org.springframework.core.io.Resource;
 
// Application (Main) Class
public class Main {
 
    // Main driver method
    public static void main(String[] args)
    {
        // Creating a new class path resource
        Resource resource = new ClassPathResource(
            "applicationContext.xml");
 
        // Creating an object of BeanFactory class
        BeanFactory factory = new XmlBeanFactory(resource);
 
        // Creating an object of Employee class
        Employee e = (Employee)factory.getBean("employee");
 
        // Calling display() method inside main() method
        e.display();
    }
}
```
**Output:**
```java
Company: penta-b
Employee list:
-John
-Max
-Sam
```








