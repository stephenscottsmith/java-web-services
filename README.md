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
    * Written in XML format
    * To access the Glassfish WSDL:
        * Reopen the admin console at the url -> Applications -> HelloWorld (or your package) -> View Endpoints -> WSDL link -> first http link because we don't have security enabled
        * Root Tag: `<definitions>`
            * Contains info where and how each of the main components are defined
        * `<types>` - contains the schema foor this web service
        * import schemaLocation should be port 8080
        * `<message>` tags define one possible transfer of data
            * 2 per method: 1 for the input, 1 for the response
        * `<portType>` constructs an HTTP URL of the package class and method identifiers for each method to be used by the accessing program
        * `<binding>` lists the methods with their SOAP 
        * `<service>` gives the actual URL where the service resides
* Exploring WSDL
    * If we want to customize a WSDL file first write a simple throwaway method and let GlassFish automatically generate a WSDL file. 
        * This takes care of the complicated definitions, URLs, port numbers, etc. 
        * Now you can customize the WSDL file by only changing the parts that aren't already needed
    * Things that can be customized:
        * `@WebService` can have a name, portName, service URL, or the package containing the service
            * `@WebService(name="newname")`
        * `@WebMethod()`
            * Can set an action - plain text string interpreted by the WSDL as an action in the operation
            * Can customize operation name
            * Can exclude to designate certain methods not displayed in the WSDL
            * `@WebMethod(action="sample", operationName="name", exclude)`
* Implementing a Web Service
    * Duplicate all the entries of an existing method in the XML file
    * Need 2 message tags (1 for input, 1 for output)
    * Can copy 1 of the operation tags and designate their message attributes
    * **Common to customize the WSDL with all of your methods and classes first, then write the code for them**
* Adding Multiple Parts to WSDL
    * Allows a single request to return multiple pieces of data
    * Delineates different parts of a single message
        * metadata
        * headers and footers
    * Complex Type Element
        * Allows you to define a more complicated message
        * Basic Syntax
            * `<xs:element name="name"></xs:element>`
            * Inisde: `<xs:complexType></xs:complexType>`
                * Has several attributes
                    * The ID and Name attributes create separate identifiers for ease of reference
                    * Abstract - if true, then it cannot be used as part of an instance document
                    * Block, Final
                        * Extension
                        * Restriction
                        * All
                    * Mixed
                * Inside: `<xs:sequence></xs:sequence>`
                    * Inside: `<xs:element name="name" type="type"/>`
* Challenge: Create a One-Way WSDL Message
    * Create a WSDL file for StockData
    * Methods: 
        1. Get price of a stock
        2. Update or change stock price
        3. Add a new stock to the database
* Solution: Create a One-Way WSDL Message
    * 3 Pieces for Each Method
        1. Should have 2 entries in the message section, one for the method itself and one for the response
        2. Operation Name listed under the port type tab
        3. Specify the bindings and encodings for the message

## Chapter 3. Simple Object Access Protocol (SOAP)
* Introducing SOAP and SOAP Toolkits
    * XML based protocol that allows user to exchange info via other protocols such as HTTP
    * Binding used with WSDL documents
    * Location and Metadata
    * SOAP vs. RPC
        * SOAP
            * Designed for remote communication
            * Platform independent and universally recognized
            * Language-independent
            * Popular SOAP Toolkit: Java API for XML Web Services (JAX-WS)
        * RPC
            * Designed for computesr within a small network
            * Blocked by some firewalls
            * Language-dependent
* Exploring the Syntax and Design of SOAP
    * SOAP Elements
        * In order for XML document to be used as a SOAP message, it must contain 4 elements:
            1. Envelope - a container for the document that identifies it as a SOAP message
                * Required in order to inform recipient of how to use the document
            2. Header (optional) - contains descriptive metadata for the main document
                * Official to aid in searching and/or modifying large SOAP messages
            3. Body - contains all of the calls and their responses
            4. Error-Checking - makes it possible for the sender to see if anything went wrong during the transfer of the SOAP message
        * Sample SOAP Message:   
        ***  
        <?xml version='1.0' ?>  
        <env:Envelope xmlns:env=http://w3.org/2003/05/soap-envelope>  
        <env:Header>
        <env:EncodingStyle>  
        <env:role http://w3.org/2003/05/soap-envelope/ultimateReceiver>  
        <env:mustUnderstand="false">  
        <env:relay>  

        <env:body> // Message to transfer 
        ***
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
