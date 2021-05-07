# String
## 1) Given string “Algorithms”, return  “go” and “Algo” using substring
```java
class Main {  
  public static void main(String args[]) { 
    String s = "Algorithms";
    String s1 = s.substring(2, 4);
    String s2 = s.substring(0, 4);
    System.out.println(s1);
    System.out.println(s2);
  } 
}
```

## 2) Given two strings, compare if these two two strings are equal by comparing each character
```java
class Main {  
  public static void main(String args[]) { 
    String s1 = "Algorithms";
    String s2 = "Algorithms";
    System.out.println(s1.equals(s2));
  } 
}
```

## 3) Given string “https://www.amazon.com/demo?test=abc”, return [“https”,”www”,”amazon”,”com”,”demo”,”test”,”abc”]
```java
class Main {  
  public static void main(String args[]) { 
    String webSite = "https://www.amazon.com/demo?test=abc";
    String[] arr = webSite.split("[:/.?=]+");
    for (var ele: arr) {
      System.out.println(ele);
    }
    
  } 
}
```

## 4) Given a list of string array, combine them into one string sentence, return the string sentence
```java
class Main {  
  public static void main(String args[]) { 
    String[] arr = {"a", "b", "c", "d"};
    StringBuilder sb = new StringBuilder("");
    for(var ele: arr) {
      sb.append(ele);
    }
    System.out.println(sb);
  } 
}
```

# final
## 1) define a final class and final method and final variable, modify the value of the variable in final method
```java
class Main {  
  public static void main(String args[]) { 
    
  }
  public final class Person {
    public final String name = "Bob";
    public final void setName(String name) {
      this.name = name;
    }
  }
}
```

# Static
## 1) Given a database table “Book” with columns (id, isbn, name, author, publish date), define a java class that matches this table and then use a static block to initialize this table with some records
```java
class Main {  
  public static void main(String args[]) { 
    
  }
  public class Book {
    private String id;
    private String isbn;
    private String name;
    private String author;
    private String publish_date;
    public static void initBook(String id, String isbn, String name, String author, String publish_date) {
      this.id = id;
      this.isbn = isbn;
      this.name = name;
      this.author = author;
      this.publish_date = publish_date;
    }
  }
} // will get an error because static method cannot reference non-static variables
```

## 2) Define a Java class “BookSeller” and then define a static inner class “Book”, and use a static method “sellBooks” to initialize several books, and in the main method display all the books by calling the “sellBooks” method
```java
class Main {  
  public static void main(String args[]) { 
    Book[] books = BookSeller.sellBooks();
  }

  public static class BookSeller {
    public static class Book {
      private String name;
      private String author;
      public Book(String name, String author) {
        this.name = name;
        this.author = author;
      }
    }
    public static Book[] sellBooks() {
      Book[] books = new Book[2];
      books.add(new Book("a", "Alice"));
      books.add(new Book("b", "Bob"));
      return books;
    }
  }

}
```
# OOP
## 1) Define an interface “DatabaseConnection” and then define class “OracleConnection”, “MySqlConnection”, “SqlServerConnection”. They should all implements the “getConnection” method from the interface. The method should initialize data source and return a database connection.
```java
public interface DatabaseConnection {
    public Connection getConnection();
}

public class OracleConnection implements DatabaseConnection {
    public Connection getConnection() {
        DataSource oracleDS = new OracleDataSourcce();
        Connection conn = driver.getConnection(oracleDS);
        return conn;
    }
}
public class MySqlConnection implements DatabaseConnection {
    public Connection getConnection() {
        DataSource mysqlDS = new OracleDataSourcce();
        Connection conn = driver.getConnection(mysqlDS);
        return conn;
    }
}
public class SqlServerConnection implements DatabaseConnection {
    public Connection getConnection() {
        DataSource sqlServerDS = new OracleDataSourcce();
        Connection conn = driver.getConnection(sqlServerDS);
        return conn;
    }
}
```
## 2) Define an abstract class “CreditCard” which contains fields (holderName, cardNumber, accountBalance, cardType), and not-implemented method “isCardAcceptable” with argument cardType, and implemented method “payBill(double bill)”. Define two classes “VisaCard” and “MasterCard” both should inherit this “CreditCard” class and you should define constructor for both classes and implement the “isCardAcceptable” method.
```java
public abstract class CreditCard {
    String holderName;
    String cardNumber;
    double accountBalance;
    String cardType;

    public abstract boolean isCardAcceptable(String cardType);

    public void payBill(double bill) {
        this.accountBalance -= bill;
    }
}

public class VisaCard extends CreditCard {
    public VisaCard(String holderName, String cardNumber, double accountBalance, String cardType) {
        this.holderName = holderName;
        this.cardNumber = cardNumber;
        this.accountBalance = accountBalance;
        this.cardType = cardType;
    }
    public boolean isCardAcceptable(String cardType) {
        if(this.cardType.equals(cardType)) {
            return true;
        }
        return false;
    }
}
```

## 3) Implement static and dynamic polymorphism.
```java
public class Person {
    String name;
    double height;
    public Person(String name, double height) {
        this.name = name;
        this.height = height;
    }
    public speak() {
        System.out.println("Hello!");
    }
    // overload / static polymorphism
    public speak(String day) {
        System.out.println("Today is "+ day);
    }
}
public class Dave extends Person {
    @Override  // dynamic polymorphism
    public speak() {
        System.out.println("How are you!");
    }
}
```
# Serializable
## 1) Define a “Employee” POJO class and make it serializable
```java
public class Employee implements Serializable {
    private static final long serialVersionUID = 1L;
    private String name;
    private int salary;

    public String getName() {
        return this.name;
    }
    public void setName(String name) {
        this.name = name;
    }
    public int getSalary() {
        return this.salary;
    }
    public void setSalary(int salary) {
        this.salary = salary;
    }
}
```

# Design Pattern
## 1) Create a singleton class called “AppleDesignerFactory”
```java
public class AppleDesignerFactory {
    private static AppleDesignerFactory instance;
    private AppleDesignerFactory () {}
    public static synchronized AppleDesignerFactory getInstance() {
        if (instance != null) {
            instance = new AppleDesignerFactory();
        }
        return instance;
    }

    @Override
    protected AppleDesignerFactory clone() throws CloneNotSupportedException {
        throw new CloneNotSupportedException();
    } 

    protected AppleDesignerFactory readResolve() {
        return getInstance()
    }
}
```

## 2) Create a factory pattern called “CurrencyExchange” which takes in the country name and return the currency object for that country.
```java
public abstract class Currency {
    double amount;
    String symbol;
    public void setAmount(double amount) {
        this.amount = amount;
    }
    public abstract void setCurrency();
}

public class Dollar extends Currency {
    public void setCurrency() {
        this.symbol = "$";
    }
}
public class RMB extends Currency {
    public void setCurrency() {
        this.symbol = "¥";
    }
}

public class CurrencyExchange{
    public static getCurrency(String country) {
        if(country.equals("US")) {
            return new Dollar();
        }
        if(country.equals("China")) {
            return new RMB();
        }
    }
}
```

# Collection

## 1) (Set)Find true friends: Given two arraylists containing friend names, find the true friends that appear in both list.
```java
import java.util.*;
import java.util.stream.Collectors;
class Main {  
  public static void main(String args[]) { 
    List<String> friends1 = Arrays.asList("Jack", "Pony", "Elon", "Bill", "Jeff");
    List<String> friends2 = Arrays.asList("Tom", "Jack", "Alice", "Bob", "Jeff");
    List<String> common = friends1.stream().filter(f -> friends2.contains(f)).collect(Collectors.toList());
    for (var ele: common) {
        System.out.println(ele);
    }
  } 
}
```

## 2) (Map)Given a string, output duplicate characters and their counts
```java
import java.util.*;
import java.lang.*;
import java.io.*;
import java.util.stream.Collectors;


class Main {  
  public static void main(String args[]) { 
    String chars = "sdflkjsdlkszkijc";
    Map<String, Integer> map = Arrays.asList(chars.split("")).stream().collect(Collectors.groupingBy(e -> e, Collectors.summingInt(e -> 1)));
    for (Map.Entry<String, Integer> ele: map.entrySet()) {
        System.out.print(ele.getKey());
        System.out.print(": ");
        System.out.println(ele.getValue());
    }
  } 
}
```

# Exception Handling

## 1) Define two exceptions “CardTypeException” and “AddressException”. Create a separate class “ExceptionHandler” which contains one method “handleException”. The method takes input of cardType and address. If cardType is “AMEX”, throw CardTypeException. If address is outside US, return AddressException, for other errors, just return generic exception. Your exception should be caught and you should display message to tell which exception is returned.

```java
import java.util.*;
import java.lang.*;
import java.io.*;
import java.util.stream.Collectors;


class CardTypeException extends Exception {
  CardTypeException(String msg) {
    super(msg);
  }
}

class AddressException extends Exception {
  AddressException(String msg) {
    super(msg);
  }
}

class ExceptionHandler {
  public static void handleException(String cardType, String address) {
    try {
      if (cardType == "AMEX") {
        throw new CardTypeException("Amex card is not allowed...");
      }
      if (address != "US") {
        throw new AddressException("Addresses out side of US is not allowed...");
      }
      System.out.println("Executed without error.");
    } catch (CardTypeException e) {
      System.out.println(e);
    } catch (AddressException e) {
      System.out.println(e);
    }
  }
}

class Main {  
  public static void main(String args[]) { 
    ExceptionHandler.handleException("AMEX", "AA");
  } 
}
```

# ExecutorService

## 1) Define a inner class A has method “getMethod()” which return string “A.getMethod” and another inner class B has method “getMethod()” which return string “B.getMethod”. write another method “runSameTime()” which should let A and B getMethod to run at the same time, but the “runSameTime()” method should return a string “B.getMethod A.getMethod”

```java
import java.util.*;
import java.lang.*;
import java.io.*;
import java.util.stream.Collectors;
import java.util.concurrent.ExecutorService;
import java.util.concurrent.Future<V>;


class Main { 
  public class A {
    public String getMethod() {
      return "A.getMethod";
    }
  } 

  public class B {
    public String getMethod() {
      return "B.getMethod";
    }
  } 

  public static String runSameTime() {
    ExecutorService es = Executors.newCachedThreadPool(2);
    try {
      Future<String> futureA = es.submit(() -> new A().getMethod());
      Future<String> futureB = es.submit(() -> new B().getMethod());

      boolean isAllDone = false;
      while (!isAllDone) {
        if (futureA.isDone() && futureB.isDone()) {
          return futureB.get() + futureA.get();
          isAllDone = true;
        }
      }
    } catch (Exception e) {
      System.out.println(e);
    } finally {
      es.shutdown();
    }
  }

  public static void main(String args[]) { 
    String r = runSameTime();
    System.out.println(r);
  } 
}
```

# Java 8

## 1) Define an interface “CreditCard” which contains fields (holderName, cardNumber, accountBalance, cardType), and not-implemented method “isCardAcceptable” with argument cardType. Define two classes “VisaCard” and “MasterCard” both should inherit this “CreditCard” interface and you should define constructor for both classes and implement the “isCardAcceptable” method. Now Add a default method “payBill(double bill)” and static method “refund(double amount)” to the interface. Verify that VisaCard and MasterCard class can read these two methods (use Main method to verify).
```java
import java.util.*;
import java.lang.*;
import java.io.*;
import java.util.stream.Collectors;

interface CreditCard {
  public boolean isCardAcceptable(String cardType);
  public default payBill()
}

class VisaCard implements CreditCard {
  String holderName;
  String cardNumber;
  String accountBalance;
  String cardType = "visa";
  CreditCard(String holderName, String cardNumber, String accountBalance) {
    this.holderName = holderName;
    this.cardNumber = cardNumber;
    this.accountBalance = accountBalance;
  }
  @Override
  public boolean isCardAcceptable(String cardType) {
    if(this.cardType == cardType) {
      return true;
    } else {
      return false;
    }
  }
}

class MasterCard implements CreditCard {
  String holderName;
  String cardNumber;
  String accountBalance;
  String cardType = "master";
  CreditCard(String holderName, String cardNumber, String accountBalance) {
    this.holderName = holderName;
    this.cardNumber = cardNumber;
    this.accountBalance = accountBalance;
  }
  @Override
  public boolean isCardAcceptable(String cardType) {
    if(this.cardType == cardType) {
      return true;
    } else {
      return false;
    }
  }
}

class Main {  
  public static void main(String args[]) { 
    ExceptionHandler.handleException("AMEX", "AA");
  } 
}
```

## 2) "walabcwalexywalxzsfwalmx”  -- replace "wal" with "sams"
```java
import java.util.*;
import java.lang.*;
import java.io.*;
import java.util.stream.Collectors;


class Main {  
  public static void main(String args[]) { 
    String chars = "walabcwalexywalxzsfwalmx";
    String repl = Arrays.asList(chars.split("(?i)wal")).stream().collect(Collectors.joining("sam"));
    System.out.println(repl);
  } 
}
```

## 3) "Eclipse eclipse Eclipse eclipse amc clip ECLIPSE" – count the occurrence of each unique word (ignore case), return result as a map. For example (eclipse->5, amc->1, clip->1)

```java
import java.util.*;
import java.lang.*;
import java.io.*;
import java.util.stream.Collectors;


class Main {  
  public static void main(String args[]) { 
    String chars = "Eclipse eclipse Eclipse eclipse amc clip ECLIPSE";
    Map<String, Integer> map = Arrays.asList(chars.toLowerCase().split(" ")).stream().collect(Collectors.groupingBy(e -> e, Collectors.summingInt(e -> 1)));
    for (Map.Entry<String, Integer> ele : map.entrySet()) {
      System.out.print(ele.getKey());
      System.out.print(" -> ");
      System.out.println(ele.getValue());
    }
  } 
}
```

