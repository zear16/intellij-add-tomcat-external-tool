# intellij-add-tomcat-external-tool
Integrate Tomcat with IntelliJ IDEA Community

* [Install Tomcat](#topic-install-tomcat)
* [Setup external tool](#topic-setup-external-tool)
* [Setup remote debug](#topic-setup-remote-debug)
* [Setup Maven Create WAR and Deploy](#topic-setup-maven-create-war-and-deploy)
* [Start external tool](#topic-start-external-tool)

## Setup external tool <a name="topic-setup-external-tool"></a>

* File > Settings
* Expand Tools and Select External Tools
* Add new tool with
    * Name: tomcat
    * Program: C:\tools\tomcat\apache-tomcat-9.0.12\bin\catalina.bat
    * Argument: jpda run

![](resources/set-external-tool-tomcat.png)

## Setup remote debug <a name="topic-setup-remote-debug"></a>

* Run > Edit Configurations
* Click "+" and select "Remote"
* Add new Remote with
    * Name: tomcat@8000 (We will start remote debug to tomcat with port 8000)
    * Transport: Socket
    * Host: localhost
    * Port: 8000
* In tab Logs Set console out put file to "C:\tools\tomcat\apache-tomcat-9.0.12\logs\*.*"    

![](resources/set-run-remote-tomcat-debug.png)

![](resources/set-run-remote-tomcat-debug-log.png)

## Setup Maven create WAR and deploy <a name="topic-setup-maven-create-war-and-deploy"></a>

* Run > Edit Configurations
* Click "+" and select "Maven"
* Add new Maven with
    * Command line: war:war org.codehaus.mojo:wagon-maven-plugin:upload-single -Dwagon.fromFile=C:\work\ptvn-ep-mtl\web\target\ebd.war -Dwagon.url=file://C:\tools\tomcat\apache-tomcat-9.0.12\webapps\

![](resources/set-maven-create-and-deploy-war.png)

## Start external tool <a name="topic-start-external-tool"></a>

* Tools > Externals Tools and click "tomcat"
