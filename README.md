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
        * Sample SOAP Message in tutorial
* Comparing SOAP 1.1 to SOAP 1.2
    * SOAP 1.1
        * Released May 2000
        * Based on XML 1.0
        * Only supports HTTP
        * Supported by JAX-WS
        * Not compatible with SOAP 1.2
        * Error Checking
            * Available tags: faultcode, faultstring, faultactor, detail
    * SOAP 1.2
        * Released June 2003
        * Based on XML Info Set
        * Supports any protocol that confirms to its framework
        * Supported by JAX-WS
        * Compatible with SOAP 1.1
        * Error Checking
            * Available tags: code, reason, node, detail, Role
* Challange: Add a SOAP Binding
    * Create messages for the Chapter 2 exercise
* Solution: Add a SOAP Binding
    * See tutorial

## Chapter 4. Representational State Transfer (REST)
* What is REST?
    * Set of architectural principles that guide the development of web services
    * Developed in 2000
    * Advantage over SOAP: much easier to use
    * Architectural Style, not a standard - no specific format or syntax, "Best Practices"
    * SOAP and WSDL focus on the methods whereas REST focuses on the system's resources
    * 4 Basic Design Principeles:
        1. Uses HTTP methods explicitely (POST, GET, etc.)
        2. Stateless - allows for parallelization
        3. System URI Formats
        4. Format via XML messages or JSON
* Exploring the Syntax and Design of REST
    * REST uses a different 
    * 4 Main HTTP Methods:
        1. GET
            * Example: `GET /users/name HTTP/1.1`
                * `GET`: specifies what the server should do with the URI
                * `/users/name`: URI which uses directory structure to specify where to look for information
                * `HTTP/1.1`: tells the server what format you're sending your request in
            * Can have the following lines under the above example:
                * `HOST: servername`: specifies the server
                * `Accept: text/xml`: specifies the return data or `application/json` to return a json file
        2. PUT
        3. POST
        4. DELETE
    * Best Practices
        * Requests should be Idempotent: running the request again with the same parameters should cause no further change
* Creating a REST Root Resource Class
    1. Create a class
    2. Designate class's path via: `@Path(value="restful path")`
    3. Inside the class will be the methods that can operate on this path   
        `@GET`   
        `@Produces("text/xml")`  
* Using MIME types with RESTful Messages
    * @Consumes and @Produces control what type of data you can accept and send out
    * Multipurpose Internet Mail Extension (MIME)
    * Consider the general format of your messages
    * Consult the Internet Assigned Numbers Authority 
    * XML Specification
        * `Application/XML`
            * Has more stringent requirements for translating the message from Java to MIME type and is primarily suited for messages that are intended for computers
        * `text/xml`
            * Meant to be human-readable with simple strings of data
    * Converting Data Types
        * Java.lang.String supports all text media types
        * java.xml.transform.Source type supports all XML media types
        * Java's byte arrays, input streams, readers, and files support all media types
* Challenge: Create a REST Root Resource Class
    * Create a simple class with GET, PUT, DELETE
* Solution: Create a REST Root Resource Class
    * Do not forget that a GET in this requires a @Consumes and @Produces

## Chapter 5. Programming a Web Service in Java EE
* Specifying the Methods and Structure Needed for the Web Service
    * Method to receive data
    * Back-end database
    * Method to check data with database
    * Method to return the results
* Creating the Web Service Endpoint
    1. New -> Dynamic Web Project -> MeetingScheduler
    2. Java Resources -> src folder -> Create new package to hold code "scheduler"
    3. Create new class "root"
    4. @POST method both @Consumes and @Produces "text/plain"
* Testing a Web Service Without a Client
    * Create new class part of the Scheduler package called "RestTest"
    * Before even running the application on a server, test by creating a Test class and right-clicking the Test.class -> Run as -> Java Application
* Creating an Application Client
    * 4 Basic Steps to Creating a Client Request using the JAX RS API
        1. `Client c = ClientBuilder.newClient()` - javax.ws.rs.client.Client interface
        2. `c.target(URI)` - construct and give it a target
        3. `c.request(MediaType.type)` - create a request 
        4. `c.get(String.class)` - invoke the request 
* Challenge: Expand the RESTful Web Service
    * Add GET method in root class that takes in a date, return a string indicating whether the date is filled
* Solution: Expand the RESTful Web Service

## Chapter 6. Improving Your Java EE Code
* Debugging your Web Services
    * Eclipse Debugger
        * Click on the +View icon in top right corrner -> Debug perspective
    * Admin Console for GlassFish
        * Monitoring Data -> Instance of your Server -> View log files
* Optimizing your Code
    * Should be based on: understandability, flexibility, compatibility
    * Supporting more data types will make server slower
    * 10% of the code takes 90% of the time
    * Never repeat work! - Database accesses are slow!
    * Structure data in usable form
* Sending Different Data Types
    * Only things you have to change in order to support other MIME types is the @produces and @consumes annotations
    * `@MTOM` - denotes that other media types will be used
* Enabling Security and Encryption
    * By default no security is enabled
    * Can be done by going into the GlashFish server Configuration -> server-config -> Security
    * Security Manager enabled checked on
    * Security -> Message Security
        * HTTPServlet
            * Default Provider: GFConsoleAuthModule will encrypt data and control access
            * Default Client Provider: XWS_ServerProvider has additional features
    * Most important concept in Security and Encryption:
        * Authentication - who is accessing the service
        * Authorization - who can access the service?
        * Confidentiality - who can see messages to and from the service?
            * Public and private keys
* Challenge: Debug and Optimize a Sample Web Service
    * Improve code for data checking service
* Solution: Debug and Optimize a Sample Web Service
    * Data that will be accessed a lot should be sorted

## Chapter 7. Extensions
* Web Services Distributed Management (WSDM)
    * a system created to help manage other web services or network enabled hardware devices
    * Interface with other devices - printers, servers, fax machines
    * Compatible with many different devices
    * 2 Standards:
        1. MUWS (management using web services) - works with servers on other devices
        2. MOWS (management of web services) - allow you to manage web services remotely
* Web Services Invocation Framework (WSIF)
    * Java API for web services description language, that serves as an alternative for SOAP API's
    * Alternative to SOAP
    * Interact with representations of services
    * Even more compatible than SOAP
        * Multiple bindings
        * Dynamic Invocation
    * Adheres to "Black Box"
        * API calls are technology independent
* Bus-Enabled Web Services
    * Service Integration Bus - a single architecture that acts as a communication network for multiple servers and other devices
    * Advantages 
        * Compatibility - any type of web service
        * Flexibility - asynchronous messaging
        * Control - convert between internal applications and web services

## Conclusion
* Where to go from here...
