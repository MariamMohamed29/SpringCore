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
**Initializing Sets**
```java
 <bean id="company" class="com.geeksforgeeks.org.Company">  
        <property name="companyName" value="Penta-b"></property>  
        <property name="employees">
            <set>
                 <value>"John"</value>
                <value>"Max"</value>
                <value>"Sam"</value>
             </set>
         </property>
    </bean>
```
**Initializing Maps**
```java
 <bean id="company" class="com.geeksforgeeks.org.Company">  
        <property name="companyName" value="Penta-b"></property>  
        <property name="employees">
            <map>
                 <entry key="Key 1" value="John"/>
                 <entry key="Key 2" value="Max"/>
                 <entry key="Key 3" value="Sam"/>
             </map>
         </property>
    </bean>
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
## Autowiring
Spring is an open-source application development framework of Java that allows you to create robust enterprise applications using Plain Old Java Objects (POJO in short). The Spring framework can inject dependencies automatically. The Spring container detects those dependencies specified in the configuration file and @ the relationship between the beans. This is referred to as autowiring in Spring. An autowired application requires fewer lines of code comparatively but at the same time, it provides very little flexibility to the programmer.
### Modes of Autowiring
**1. No**
This mode tells the framework that autowiring is not supposed to be done. It is the default mode used by Spring.
#### Example
```java
<bean id="state" class="sample.State"> 
 <property name="name" value="UP" /> 
</bean> 
<bean id="city" class="sample.City"></bean>
```
**2. byName**
It uses the name of the bean for injecting dependencies. However, it requires that the name of the property and bean must be the same. It invokes the setter method internally for autowiring.
#### Example
```java
<bean id="state" class="sample.State"> 
 <property name="name" value="UP" /> 
</bean> 
<bean id="city" class="sample.City" autowire="byName"></bean>
```
**3. byType**
It injects the dependency according to the type of the bean. It looks up in the configuration file for the class type of the property. If it finds a bean that matches, it injects the property. If not, the program throws an error. The names of the property and bean can be different in this case. It invokes the setter method internally for autowiring.
#### Example
```java
<bean id="state" class="sample.State"> 
 <property name="name" value="UP" /> 
</bean> 
<bean id="city" class="sample.City" autowire="byType"></bean>
```
**4. constructor**
It injects the required dependencies by invoking the constructor. It works similar to the “byType” mode but it looks for the class type of the constructor arguments. If none or more than one bean are detected, then it throws an error, otherwise, it autowires the “byType” on all constructor arguments.
#### Example
```java
<bean id="state" class="sample.State"> 
 <property name="name" value="UP" /> 
</bean> 
<bean id="city" class="sample.City" autowire="constructor"></bean>
```
**5. autodetect**
The autodetect mode uses two other modes for autowiring – constructor and byType. It first tries to autowire via the constructor mode and if it fails, it uses the byType mode for autowiring. It works in Spring 2.0 and 2.5 but is deprecated from Spring 3.0 onwards.
#### Example
```java
<bean id="state" class="sample.State"> 
 <property name="name" value="UP" /> 
</bean> 
<bean id="city" class="sample.City" autowire="autodetect"></bean>
```
## init() and destroy() Methods
During the Spring Application Development, sometimes when the spring beans are created developers are required to execute the initialization operations and the cleanup operations before the bean is destroyed. In the spring framework, we can use the init-method and the destroy-method labels in the bean configuration. 
### init() Method
In the real-world application init() method is the one you will find it everywhere. init-method is the attribute of the spring <bean> tag. It is utilized to declare a custom method for the bean that will act as the bean initialization method. We can define it as follows.
```java
<bean id="student" class="com.amiya.Student" init-method="myPostConstruct">
```
Here myPostConstruct() method is the bean initialization method in the Student class. This initialization method is called after initializing bean properties. We can use such an initialization method to validate the value of bean properties or initialize any task.
### Why init()?
-You can add custom code/logic during bean initialization

-It can be used for setting up resources like database/socket/file etc.
### destroy() Method
The destroy() method will be called before the bean is removed from the container. destroy-method is bean attribute using which we can assign a custom bean method that will be called just before the bean is destroyed. To use the destroy-method attribute, we do as follows.
```java
<bean id="student" class="com.amiya.Student" destroy-method="myPreDestroy">
```
Here myPreDestroy() method will be defined in the Student class. Spring will call this method just before destroying the bean. destroy-method is used to release resources or perform some destruction task. DisposableBean interface in spring performs the same task but it is highly coupled to spring, so we should prefer destroy-method. So let’s understand these two methods with a simple example.
## Inheriting Bean
Constructor arguments, property values, and container-specific information like initialization method, static factory method name, and so on may all be found in a bean definition. A parent definition’s configuration data is passed down to a child bean definition. The child definition has the ability to override or add values as needed.

Although Spring Bean’s definition of inheritance differs from Java class inheritance, the inheritance notion is the same. A parent bean definition can be used as a template, and other child beans can inherit the required configuration from it.
### Implementation:
**Step 1: Creation of ‘Customer’ class**
```java
package com.geeksforgeeks.beans.inheritance;
// Class
public class Customer {
 
    // Class data members
    private String name;
    private String email;
    private String country;
 
    // Getters and setters
    public String getName() { return name; }
    public void setName(String name) { this.name = name; }
 
    public String getEmail() { return email; }
    public void setEmail(String email)
    {
        // this keyword refers to current instance itself
        this.email = email;
    }
 
    // Method
    public String getCountry() { return country; }
 
    // Setter
    public void setCountry(String country)
    {
        this.country = country;
    }
 
    // Method
    // To show message
    @Override public String toString()
    {
        // Print corresponding customer attributes
        return " Name:" + name + "\n Email:" + email
            + "\n Country:" + country;
    }
}
```
**Step 2: Create a spring beans.xml file that demonstrates how to inherit the bean.**
```java
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:context="http://www.springframework.org/schema/context"
    xmlns:p="http://www.springframework.org/schema/p"
    xsi:schemaLocation="http://www.springframework.org/schema/beans
        http://www.springframework.org/schema/beans/spring-beans-3.2.xsd
        http://www.springframework.org/schema/context
          http://www.springframework.org/schema/context/spring-context-3.2.xsd">
 
    <bean id="baseCustomer" abstract="true">
    <property name="country" value="India"/>
    </bean>
     
    <bean id="customer" parent="baseCustomer" class="com.geeksforgeeks.beans.inheritance.Customer">
    <property name="country" value="India"/>
    <property name="name" value="Admin"/>
    <property name="email" value="geeksforgeeks@gmail.com"/>
    </bean>
</beans>
```
We have defined 2 beans in the configuration file

-Bean with the id base.

-The customer is the parent bean, while the second bean with the same id is the child bean. As a result, the country property and its value are inherited by the child bean customer, who then adds two additional properties to it.
**Step 3: Create a class that loads these two beans and displays the output with the inherited value.**
```java

// Java Program to Illustrate Bean Inheritance
 
package com.geeksforgeeks.beans.inheritance;
 
// Importing required classes
import org.springframework.context.support.ClassPathXmlApplicationContext;
 
// Class
public class BeanInheritanceTest {
 
    // Main driver method
    public static void main(String[] args)
    {
 
        // Inheriting Bean by customer
        ClassPathXmlApplicationContext applicationContext
            = new ClassPathXmlApplicationContext(
                "beans.xml");
 
        Customer customer
            = (Customer)applicationContext.getBean(
                "customer");
 
        // Printing the customer info
        System.out.println(customer.toString());
    }
}
```
**Output**

Name:Admin

Email:geeksforgeeks@gmail.com

Country:India

## Spring Annotations
Spring Annotations are a form of metadata that provides data about a program. Annotations are used to provide supplemental information about a program. It does not have a direct effect on the operation of the code they annotate. It does not change the action of the compiled program. 
### Stereotype Annotations
Spring Framework provides us with some special annotations. These annotations are used to create Spring beans automatically in the application context. @Component annotation is the main Stereotype Annotation. There are some Stereotype meta-annotations which is derived from @Component those are

**@Service**
**@Repository**
**@Controller**

**1: @Service:** We specify a class with @Service to indicate that they’re holding the business logic. Besides being used in the service layer, there isn’t any other special use for this annotation. The utility classes can be marked as Service classes.
**2: @Repository:** We specify a class with @Repository to indicate that they’re dealing with CRUD operations, usually, it’s used with DAO (Data Access Object) or Repository implementations that deal with database tables.
**3: @Controller:** We specify a class with @Controller to indicate that they’re front controllers and responsible to handle user requests and return the appropriate response. It is mostly used with REST Web Services.

### @Required Annotation with Example
The @Required annotation in spring is a method-level annotation used in the setter method of a bean property and therefore making the setter-injection compulsory. This annotation suggests that the required bean property must be injected with a value at the configuration time which we will show and explain in the following example. 
#### Example
Consider a class representing a Person with a required property name. We can use the @Required annotation to ensure that the name property is set before the bean is fully initialized.
```java
import org.springframework.beans.factory.annotation.Required;

public class Person {
    private String name;

    @Required
    public void setName(String name) {
        this.name = name;
    }

    public String getName() {
        return name;
    }
}
```
**Main.java**
```java
import org.springframework.beans.factory.BeanInitializationException;
import org.springframework.context.support.AbstractApplicationContext;
import org.springframework.context.support.ClassPathXmlApplicationContext;

public class MainApp {

    public static void main(String[] args) {
        AbstractApplicationContext context = new ClassPathXmlApplicationContext("applicationContext.xml");

        try {
            // Attempt to get the Person bean
            Person person = (Person) context.getBean("person");

            // Display the person's name
            System.out.println("Person's Name: " + person.getName());
        } catch (BeanInitializationException e) {
            System.err.println("Error: " + e.getMessage());
        } finally {
            context.close();
        }
    }
}
```
**applicationContext.xml**
```java
<beans xmlns="http://www.springframework.org/schema/beans"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xsi:schemaLocation="http://www.springframework.org/schema/beans http://www.springframework.org/schema/beans/spring-beans.xsd">

    <!-- Define the Person bean -->
    <bean id="person" class="Person" />

</beans>
```










