## Modular samples for NetBeans

JavaFX 12 samples to run from NetBeans with different options and build tools

Version NetBeans [11.0](https://netbeans.apache.org/download/nb110/nb110.html)

Download an appropriate [JDK 12](https://jdk.java.net/12/) for your operating system. Make sure `JAVA_HOME` 
is properly set to the Java 12 installation directory. 

The samples assume NetBeans 11 runs on JDK 12 (this can be set editing the `etc/netbeans.conf` file
and setting `netbeans_jdkhome="/path/to/jdk12"`).

Download [JavaFX jmods](https://gluonhq.com/products/javafx/) for your operating 
system and unzip to a desired location.

### Maven

Clone the sample, open it with NetBeans, and make sure the paths for Java 12 and 
JavaFX 12 match those on your machine.

Clean, build and run from the NetBeans usual buttons, or from command line:

    mvn clean compile package exec:java

As well, this will work from the terminal on Linux or Mac:

    java --module-path $PATH_TO_FX:target/hellofx-1.0-SNAPSHOT.jar -m hellofx/org.openjfx.MainApp

or on Windows:
    
    java --module-path %PATH_TO_FX%:target\hellofx-1.0-SNAPSHOT.jar -m hellofx/org.openjfx.MainApp

To create and run a custom JRE, from terminal:

On Linux or Mac run:

    cd IDE/NetBeans/Modular/Maven/hellofx
    export PATH_TO_FX_MODS=path/to/javafx-jmods-12
    $JAVA_HOME/bin/jlink --module-path $PATH_TO_FX_MODS:target/hellofx-1.0-SNAPSHOT.jar --add-modules=hellofx --output jre
    jre/bin/java -m hellofx/org.openjfx.MainApp

On Windows run:

    cd IDE\NetBeans\Modular\Maven\hellofx
    set PATH_TO_FX_MODS="path\to\javafx-jmods-12"
    %JAVA_HOME%\bin\jlink --module-path "%PATH_TO_FX_MODS%;target\hellofx-1.0-SNAPSHOT.jar" --add-modules=hellofx --output jre
    jre\bin\java -m hellofx/org.openjfx.MainApp