# weather.balloon.statistics - Weather balloon traversing the globe

There is a weather balloon traversing the globe, periodically taking observations. At each observation, the balloon records the temperature and its current location. When possible, the balloon relays this data back to observation posts on the ground.

## Getting Started

* The file generator is generating quality information, so information is generated as described in requirement.
* The total distance is being calculated using the distance between two points formula but then I did not adjust the distance to any distance unit presented in the requirement, I do not understand how to apply this rule since requirement does not describe how to perform this transformation.
* All the tests are disabled since the main route for the files are not known.
* Validations for arguments are not being performed.

### Prerequisites

* Java 8
* [Maven](https://maven.apache.org/)
* [Git](https://git-scm.com/)


### Installing

Steps to follow

Clone

```
git clone https://github.com/GeekFlu/weather.balloon.statistics.git
```

CD to main directory

```
cd weather.balloon.statistics

ls

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----    20/11/2018  03:19 a. m.                src
-a----    20/11/2018  03:19 a. m.           3531 pom.xml
-a----    20/11/2018  03:19 a. m.          21990 README.md

```

Cleaning project

```
$ mvn clean
[INFO] Scanning for projects...
[INFO]
[INFO] -------------< mx.com.geekflu:weather.balloon.statistics >--------------
[INFO] Building weather.balloon.statistics 1.0-SNAPSHOT
[INFO] --------------------------------[ jar ]---------------------------------
[INFO]
[INFO] --- maven-clean-plugin:3.0.0:clean (default-clean) @ weather.balloon.statistics ---
[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] ------------------------------------------------------------------------
[INFO] Total time: 0.329 s
[INFO] Finished at: 2018-11-20T03:21:26-06:00
[INFO] ------------------------------------------------------------------------
```

Build and package

```
mvn install
[INFO] Scanning for projects...
[INFO]
[INFO] -------------< mx.com.geekflu:weather.balloon.statistics >--------------
[INFO] Building weather.balloon.statistics 1.0-SNAPSHOT
[INFO] --------------------------------[ jar ]---------------------------------
[INFO]
[INFO] --- maven-resources-plugin:3.0.2:resources (default-resources) @ weather.balloon.statistics ---
[INFO] Using 'UTF-8' encoding to copy filtered resources.
[INFO] skip non existing resourceDirectory C:\Users\luisgonz\Documents\workspaces\weather.balloon.statistics\src\main\resources
[INFO]
[INFO] --- maven-compiler-plugin:2.3.2:compile (default-compile) @ weather.balloon.statistics ---
[INFO] Compiling 10 source files to C:\Users\luisgonz\Documents\workspaces\weather.balloon.statistics\target\classes
[INFO]
[INFO] --- maven-resources-plugin:3.0.2:testResources (default-testResources) @ weather.balloon.statistics ---
[INFO] Using 'UTF-8' encoding to copy filtered resources.
[INFO] skip non existing resourceDirectory C:\Users\luisgonz\Documents\workspaces\weather.balloon.statistics\src\test\resources
[INFO]
[INFO] --- maven-compiler-plugin:2.3.2:testCompile (default-testCompile) @ weather.balloon.statistics ---
[INFO] Compiling 1 source file to C:\Users\luisgonz\Documents\workspaces\weather.balloon.statistics\target\test-classes
[INFO]
[INFO] --- maven-surefire-plugin:2.20.1:test (default-test) @ weather.balloon.statistics ---
[INFO]
[INFO] -------------------------------------------------------
[INFO]  T E S T S
[INFO] -------------------------------------------------------
[INFO] Running mx.com.geekflu.AppTest
[WARNING] Tests run: 2, Failures: 0, Errors: 0, Skipped: 2, Time elapsed: 0.032 s - in mx.com.geekflu.AppTest
[INFO]
[INFO] Results:
[INFO]
[WARNING] Tests run: 2, Failures: 0, Errors: 0, Skipped: 2
[INFO]
[INFO]
[INFO] --- maven-jar-plugin:3.0.2:jar (default-jar) @ weather.balloon.statistics ---
[INFO] Building jar: C:\Users\luisgonz\Documents\workspaces\weather.balloon.statistics\target\weather.ballon.statistics.jar
[INFO]
[INFO] --- maven-install-plugin:2.5.2:install (default-install) @ weather.balloon.statistics ---
[INFO] Installing C:\Users\luisgonz\Documents\workspaces\weather.balloon.statistics\target\weather.ballon.statistics.jar to C:\Users\luisgonz\.m2\repository\mx\com\geekflu\weather.balloon.statistics\1.0-SNAPSHOT\weather.balloon.statistics-1.0-SNAPSHOT.jar
[INFO] Installing C:\Users\luisgonz\Documents\workspaces\weather.balloon.statistics\pom.xml to C:\Users\luisgonz\.m2\repository\mx\com\geekflu\weather.balloon.statistics\1.0-SNAPSHOT\weather.balloon.statistics-1.0-SNAPSHOT.pom
[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] ------------------------------------------------------------------------
[INFO] Total time: 3.013 s
[INFO] Finished at: 2018-11-20T03:24:37-06:00
[INFO] ------------------------------------------------------------------------

```

And that's it.

## How to use this tool

This is a command line arguments:

```java
java -jar target/parser-jar-with-dependencies.jar
          --command=[meanTemp],[maxTemp],[minTemp],[observations],[totalDistance]
          	--temperature-unit=celsius or kelvin default is Farenheit
          --generate-data=/path/to/file
          --balloonWeatherInfoFile=/path/to/file
          --ballonNormalizedOutputFile=/path/to/file
```
          
* **--command** are the operations performed on data
* **--generate-data** is the file generated with the dummy data
* **--balloonWeatherInfoFile** is the file where the tool is reading balloon data
* **--ballonNormalizedOutputFile** is the file generated with normalized data
* **--temperature-unit** is the unit to make convertions

### Generated dummy data, 500000 rows with data

```java
java -jar .\target\weather.ballon.statistics.jar --generate-data=C:\Users\luisgonz\Documents\balloon_data.generated33.txt
Generating data file...
Data file has been generated...
Bye BYe
```

### Get statistics from file generated in previous step default is Farenheit

```java
java -jar .\target\weather.ballon.statistics.jar --command=meanTemp,maxTemp,observations --balloonWeatherInfoFile=C:\Users\luisgonz\Documents\balloon_data.generated33.txt --ballonNormalizedOutputFile=C:\Users\luisgonz\Documents\balloon_data.out.txt
Statistics Generation....
Observatios: {OTHERS=83371, AU=83465, FR=166576, US=166588}
Mean Temperature in [fahrenheit] : -216.75674
MAX Temperature in [fahrenheit] : 140.0
Bye BYe
```

### Get statistics from file generated in previous step using celsius as temperature metric

```java
java -jar .\target\weather.ballon.statistics.jar --command=meanTemp,maxTemp,observations --temperature-unit=celsius --balloonWeatherInfoFile=C:\Users\luisgonz\Documents\balloon_data.generated33.txt --ballonNormalizedOutputFile=C:\Users\luisgonz\Documents\balloon_data.out01.txt
Default temperature unit: celsius
Statistics Generation....
Observatios: {OTHERS=83371, AU=83465, FR=166576, US=166588}
Mean Temperature in [celsius] : -138.19818
MAX Temperature in [celsius] : 60.0
Bye BYe
```
As required the statistics requested and file is generated.

## Built With

* [Maven](https://maven.apache.org/) - Dependency Management

## Authors

* **Luis Enrique Gonzalez** - *Initial work* - [PurpleBooth](https://github.com/darklatiz)

## License

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details

## Acknowledgments

* Hat tip to anyone whose code was used
* Inspiration
* etc

