[![Build Status](https://api.travis-ci.org/ralscha/embeddedtc.png)](https://travis-ci.org/ralscha/embeddedtc)

Helper class to simplify starting an embedded Tomcat  for a Maven web application project in a integrated development environment (e.g. Eclipse) .

Add this dependency to your project.

```
		<dependency>
			<groupId>ch.rasc</groupId>
			<artifactId>embeddedtc</artifactId>
			<version>2.16</version>
			<scope>provided</scope>
		</dependency>
```
		
and start the embedded Tomcat with the main class ch.rasc.embeddedtc.EmbeddedTomcat.	
This starts a Tomcat on port 8080 with a context path "" and a context directory
that points to current_dir + /src/main/webapp

If you need more control create a class in your project (e.g. StartTomcat),
create an instance of EmbeddedTomcat, call the configure methods and start the server
with startAndWait()

```
public class StartTomcat {
  public static void main(String[] args) throwsException {
    EmbeddedTomcat etc = new EmbeddedTomcat(9999);
    etc.setContextDirectory("/home/mywebapp");
    etc.setTempDirectoryName("tmp");
    etc.addContextEnvironmentString("key", "value");
    etc.startAndWait();
  }
}
```

or with method chaining

```
public class StartTomcat {
  public static void main(String[] args) throwsException {
    EmbeddedTomcat.create()
		          .setPort(9999)
		          .setContextDirectory("/home/mywebapp")
		          .setTempDirectoryName("tmp")
		          .addContextEnvironmentString("key", "value")
		          .startAndWait();
	}
}
```

It's also possible to configure the embedded Tomcat with a context xml file. This examples starts a Tomcat on port 8080 with a 
web application deployed to the ROOT context ("") and the context directory points to ./src/main/webapp

```
public class StartTomcat {
  public static void main(String[] args) throwsException {
    EmbeddedTomcat.create()
		          .setContextFile("./src/main/config/tomcat.xml")
		          .startAndWait();
	}
}
```


## CHANGELOG

### 2.16     December 3, 2017
  * Tomcat 8.0.47

### 2.15     July 18, 2017
  * Tomcat 8.0.45

### 2.14     April 23, 2016
  * Tomcat 8.0.33

### 2.13     February 18, 2016
  * Tomcat 8.0.32

### 2.12     December 8, 2015
  * Tomcat 8.0.30

### 2.11     November 25, 2015
  * Tomcat 8.0.29

### 2.10     October 13, 2015
  * Tomcat 8.0.28

### 2.9     October 2, 2015
  * Tomcat 8.0.27

### 2.8     August 22, 2015
  * Tomcat 8.0.26

### 2.7     July 7, 2015
  * Tomcat 8.0.24

### 2.6     May 23, 2015
  * Tomcat 8.0.23

### 2.5     May 18, 2015
  * Tomcat 8.0.22

### 2.4     March 27, 2015
  * Tomcat 8.0.21

### 2.3     February 21, 2015
  * Tomcat 8.0.20

### 2.2     January 27, 2015
  * Tomcat 8.0.18

### 2.1     January 17, 2015
  * Tomcat 8.0.17  

### 2.0     January 15, 2015
  * Initial release with Tomcat 8.0.15  
