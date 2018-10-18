This testing project uses the FitNesse baseline provided by [hsac-fitnesse-fixtures](https://github.com/fhoeben/hsac-fitnesse-fixtures).
It offers a web environment (wiki) to define and run tests. 

## Using this for a new Project

Download the Project as zip, and extract it on local folder\
In all cases: change `example` to `projectname`

Inside Files:
* src\main\java\nl\hsac\fitnesse\example\ExampleTest.java
* wiki\FitNesseRoot\FrontPage\content.txt 
* wiki\FitNesseRoot\Example\SuiteSetUp.wiki
* wiki\FitNesseRoot\Example\DesktopDevice\SetUp.wiki
* wiki\FitNesseRoot\Example\MobileDevice\SetUp.wiki
* pom.xml (Alleen Regel 6, 7)

Change File/Directory-Names:
* src\main\java\nl\hsac\fitnesse\example\ExampleTest.java
* src\main\java\nl\hsac\fitnesse\example
* src\test\java\nl\hsac\fitnesse\example
* wiki\FitNesseRoot\Example
* wiki\FitNesseRoot\Example.wiki

## Running Locally
To start the wiki locally execute: `mvn clean compile exec:exec` or `start.bat`, it can then be accessed at [http://localhost:9090/](http://localhost:9090/).

More details on the features of hsac-fitnesse-fixtures, and example tests, can then be accessed at 
[http://localhost:9090/HsacExamples](http://localhost:9090/HsacExamples).

## Upgrading

To upgrade to newer version of the hsac-fitnesse-fixtures project:

* stop FitNesse
* stop all selenium webdrivers that might be running
* upgrade `hsac.fixtures.version` property in `pom.xml`
* run `mvn clean -Pdelete-hsac-fitnesse-fixtures`
* start as normal

Upgrade FitNesse version used:

* stop FitNesse
* upgrade `fitnesse.version` property in `pom.xml`
* start as normal

## Run from maven

### headless
`mvn test-compile failsafe:integration-test -DseleniumBrowser=chrome "-DseleniumJsonProfile={'args':['headless', 'disable-gpu', 'window-size=1366x768']}" -DfitnesseSuiteToRun=ExampleSuite.Omgevingen.Test.TestScripts.DesktopDevice.ExampleTest`

### Selenium Grid Chrome
`mvn test-compile failsafe:integration-test -DseleniumBrowser=chrome -DseleniumGridUrl=http://<ip>:4444/wb/hub -DfitnesseSuiteToRun=ExampleSuite.Omgevingen.Test.TestScripts.DesktopDevice.ExampleTest`

### Selenium Grid Firefox
`mvn test-compile failsafe:integration-test -DseleniumBrowser=firefox -DseleniumGridUrl=http://<ip>:4444/wb/hub "-DseleniumJsonProfile={'args':['headless', 'disable-gpu', 'window-size=1366x768']}" -DfitnesseSuiteToRun=ExampleSuite.Omgevingen.Test.TestScripts.DesktopDevice.ExampleTest`


## creating allure report

`mvn site -Pallure`