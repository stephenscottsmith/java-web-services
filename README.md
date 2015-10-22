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
        1. Install Java
        2. Download Eclipse for Java EE from [http://www.eclipse.org/downloads/packages/eclipse-ide-java-ee-developers/mars1](http://www.eclipse.org/downloads/packages/eclipse-ide-java-ee-developers/mars1) 
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
    * Eclipse Environment
        * Central Panel (or Code Panel)
        * Left Pane (Project Explorer)
        * Bottom Panel - where output will show as well as options for how and where the program will run


## Chapter 2. Web Services Description Language (WSDL)

## Chapter 3. Simple Object Access Protocol (SOAP)

## Chapter 4. Representational State Transfer (REST)

## Chapter 5. Programming a Web Service in Java EE

## Chapter 6. Improving Your Java EE Code

## Chapter 7. Extensions
