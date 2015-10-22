# Building Web Services with Java EE Tutorial Notes

## Introduction
* We will be learning:
    1. Variable assignment and manipulation
    2. Defining and delineating a method
    3. Calling methods and functions
    4. Creating, editing and reading XML (Extensible Markup Language) files
    5. Ports, messages, and other ways in which computers communicate over the internet

## Chapter 1. About Web Services
* What are web services?
    * Important difference between web services and a website
        * A **website** can be thought of as a communication between 2 humans where the content is arranged such that each human can understand it.
        * A **webservice** is a communication between 2 computers. Instead of text and graphics, it transmits code requests that interact directly with another computer, often without any human intervention.
            * External server is a "black box" - do not need to know implemention/code
            * Accepts A, B, C -> Outputs data in XML format
* Working with XML Files
    * **XML (eXtensible Markup Language)**
    * Light universal method of transferring data from computer to comptuer or program to program
    * Self-Descriptive
        * Tags are defined by the author
    * Principles of XML
        * Tags are placed inside `<message>` like this and is closed like `</message>`
        * Key difference between XML and HTML: XML files **DO NOT** have preset tags
* Setting up a Runtime Architecture
    * Installing Eclipse on Ubuntu 14.04 - [http://ubuntuhandbook.org/index.php/2014/06/install-latest-eclipse-ubuntu-14-04/](http://ubuntuhandbook.org/index.php/2014/06/install-latest-eclipse-ubuntu-14-04/)
        1. Install Java from:  
         [http://www.oracle.com/technetwork/java/javase/downloads/index.html](http://www.oracle.com/technetwork/java/javase/downloads/index.html)
        2. Download Eclipse for Java EE from:   
         [http://www.eclipse.org/downloads/packages/eclipse-ide-java-ee-developers/mars1](http://www.eclipse.org/downloads/packages/eclipse-ide-java-ee-developers/mars1) 
        3. Extract Eclipse to /opt/ for Global Use  
         `cd /opt/ && sudo tar -zxvf ~/Downloads/eclipse-*.tar.gz`
        4. Create a launcher shortcut for Eclipse (this might not be necessary as extracting it might already do this so check before running this command!)
         `sudo gedit /usr/share/applications/eclipse.desktop`
        5. Make sure that the file you just created has the following:   
         ***[Desktop Entry]  
         Name=Eclipse 4  
         Type=Application   
         Exec=/opt/eclipse/eclipse   
         Terminal=false   
         Icon=/opt/eclipse/icon.xpm   
         Comment=Integrated Development Environment   
         NoDisplay=false   
         Categories=Development;IDE;   
         Name[en]=Eclipse***
        6. Run Eclipse from the Unity Dash search or go to the /opt/eclipse to perform the following:   
         `./eclipse`
    * Eclipse Environment Layout
        * Central Panel (or Code Panel)
        * Left Pane (Project Explorer)
        * Right Pane (Outline and Task List)
        * Bottom Panel - where output will show as well as options for how and where the program will run
    * Install Glassfish Tools and Starting a Server
        * Recommend downloading and unzipping to C:\Glassfish from [https://glassfish.java.net/download.html](https://glassfish.java.net/download.html)
        * Will need to point Mars Eclipse to correct installation of JDK and Glassfish 
* Creating a Simple 
    * File -> New ->
        * JAXB is a project set up for web services 
        * To build web service from scratch go to Web -> Dynamic Web Project
    * In the newly created Dynamic Web Project
        * JAX-WS - folder where any web services we have created would reside, but is blank for our basic project so far
        * First thing to do in creating a web service is to create a **Java Server Page (JSP)**
            * JSP is a simple web page used to display the web services created in our project
            * Written in HTML
        * Creating Packages and Classes of Code
            * Code must contain 3 essential elements
                1. Designate it as a webservice by `@WebService`
                2. Public constructor class that takes no inputs
                3. The actual code
* Building, Packaging, and Deploying your Service
    * A web service must run on a service and accessed by a client
    * Restart the server by right-clicking and hitting "Publish"
    * Glassfish has a built-in test server - **MAKE SURE SERVER IS SYNCHRONIZED AND STARTED**
* Challenge: Build a Simple Web Service
    * Add a fibonacci function
* Solution: Build a Simple Web Service
    * Created a fibonacci package in the src folder
    * It's important to create a package rather than the default package for web services. **If you use the default package you will get a Invocation Target Exception during testing!**
    * Can choose add/remove when deploying to make sure you are deploying what you want

## Chapter 2. Web Services Description Language (WSDL)
* What is WSDL?
    * WSDL is an XML based language used by web services to describe the functionality they offer
    * Provides all the information that a computer needs in order to kinow how to call the web service, what parameters to pass, and what data structures they expect to get back
    * Info Required:
        * Programming language
        * Method location
        * Data types of the inputs
        * Data types of the outputs
    * WSDL Message Parts
        * Service
            * Contains direct references to endpoints, their bindings, and their locations
        * Binding
            * Specifies the interface and tells the reader what type of SOAP binding style and transport will be used
        * Interface 
            * Meat of the message
            * Defines the web service itself, including all of the methods
        * Types
* Understanding the Basic Syntax
* Exploring WSDL
* Implementing a Web Service
* Adding Multiple Parts to WSDL
* Challenge: Create a One-Way WSDL Message
* Solution: Create a One-Way WSDL Message

## Chapter 3. Simple Object Access Protocol (SOAP)
* Introducing SOAP and SOAP Toolkits
* Exploring the Syntax and Design of SOAP
* Comparing SOAP 1.1 to SOAP 1.2
* Challange: Add a SOAP Binding
* Solution: Add a SOAP Binding

## Chapter 4. Representational State Transfer (REST)
* What is REST?
* Exploring the Syntax and Design of REST
* Creating a REST Root Resource Class
* Using MIME types with RESTful Messages
* Challenge: Create a REST Root Resource Class
* Solution: Create a REST Root Resource Class

## Chapter 5. Programming a Web Service in Java EE
* Specifying the Methods and Structure Needed for the Web Service
* Creating the Web Service Endpoint
* Testing a Web Service Without a Client
* Creating an Application Client
* Challenge: Expand the RESTful Web Service
* Solution: Expand the RESTful Web Service

## Chapter 6. Improving Your Java EE Code
* Debugging your Web Services
* Optimizing your Code
* Sending Different Data Types
* Enabling Security and Encryption
* Challenge: Debug and Optimize a Sample Web Service
* Solution: Debug and Optimize a Sample Web Service

## Chapter 7. Extensions
* Web Services Distributed Management (WSDM)
* Web Services Invocation Framework (WSIF)
* Bus-Enabled Web Services

## Conclusion
* Where to go from here...
