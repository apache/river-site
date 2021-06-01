Title: Building River
license: https://www.apache.org/licenses/LICENSE-2.0


## Building River

<div class="space-sm"></div>
### Prerequisites
In order to build River, you need the following tools:

  * Oracle JDK 1.6+
  * Apache ANT 1.8+

The rest is included in the source archive, and in the SVN.

This article also describes how to setup your IDE to compile River.

<div class="space-mn"></div>
### Spaces in paths
<span class="label label-warning">Warning</span>

The build process does not play nicely if you have spaces in your path names.  This includes the install path of the JDK.  

This can be circumvented, at least on a Windows/Cygwin by using the first 6 characters of the name with a space in, and postfixing a tilde and the number 1.

For example; `C:\Program Files` would become; `C:\Progra~1`

If the first six characters of your path name are not a unique name, for example if you have the two paths "C:\Program Files" and "C:\Program Something Else" then the number after the tilde may well be different.  It is suggested that you experiment using the Windows command shell to establish the correct 'tilde plus number' name for your path.

So Windows users please be particular aware.  

If you are running on Windows, it is also advisable to use a forward slash '/' are the path separator.  This is acceptable to both Java and Ant, and has the added benefit that the paths will be correct if you decide to run the JTREG tests (some of which require a Unix-like/Cygwin environment to run scripts in).  This is particularly important for the `river.home` property which is inherited from in the `qa/build.xml` file and subsequently passed onto the various classes which make up the jtreg tests.


<div class="space-mn"></div>
### Check out the code

See [this page](source-code.html) on how to check out the source code.

<div class="space-mn"></div>
### Build the distribution

River can be built simply by running Ant from where you checked the code out from.

Assume "$RIVER_HOME" is where you have checked out the code to.

    cd $RIVER_HOME
    ant

Will build all the River JARs required.  You will then find them in the $  {RIVER_HOME}/lib* directories.

<div class="space-mn"></div>
### Setting up the IDE
<div class="space-mn"></div>
#### Eclipse

Create your new IDE project using your prefered method (e.g. "Import from SVN" or create a new project using existing source, etc).  

First you will need to create a new JDK system library.  The normal JDK libraries that come in Eclipse have restrictions place on the `rt.jar` file which prevents the import of some proprietary Sun classes.  

Since River is built with Ant this isn't strictly necessary, but it is if you don't want the compiler error warnings flashing up.  
Currently, River should be built with JDK 6 (-source 5), so please ensure that you have this installed and your new library uses it.

Then you need to add the JARs in `$RIVER_HOME/extlibs` to your classpath.  

That should everything that Eclipse needs to be happy with the River code.
<div class="space-mn"></div>
#### NetBeans
  * Checkout the trunk.
  * In Netbeans 7.2 do: 
     * Open Project 
     * Navigate to the `netbeans` directory within the checked out files 
     * Open the `onebigjar` project.
     * Click on build.


<div class="space-lg"></div>
## Testing River

This build process runs the (limited) suite of unit tests that comes with River.  River is tested predominantly by using [jtreg](http://openjdk.java.net/jtreg/) and the QA test suite.

<div class="space-mn"></div>
### The JUnit tests

The JUnit tests can be found in `$RIVER_HOME/test/src` you must also add the JARs found in `$RIVER_HOME/test/lib` onto the classpath for your tests.

It's easiest to run these tests from your IDE.  In Eclipse, for example, once `$RIVER_HOME/test/src` is set at the test source directory, right-clicking the project and hitting "Run as JUnit test" is all that is required.

<div class="space-mn"></div>
### The QA Test Suite
The QA tests can also be run from the Ant script.  You must make sure the Ant you are using is using the correct JDK.  You can run "ant diagnostics" in the project directory to find out which JVM Ant is using.

Make sure that you have the following in your build.properties file which you will need to create in `$RIVER_HOME`.

    river.home=$RIVER_HOME
    jtreg.home=/path/to/jtreg/install
    jdk1.5.home=/path/to/java1.5 
    jtreg.dir=$RIVER_HOME/jtsk/qa/jtreg

<div class="alert alert-info">
Please note the remark above about using paths which contains spaces and the use of '/' over '\'.
</div>

Execute the following:

    cd $RIVER_HOME
    cd qa.run

<div class="space-mn"></div>
#### Running just a few tests
Running the entire QA suite tasks a significant portion of time; currently around the 17 hour mark.  It is therefore useful to be able to specify a subset of categories or even specific tests to run. 

<div class="space-mn"></div>
##### By settings in the properties file
When running the QA tests with Ant, this is done by including the following in the Ant build.properties file.

    # runs a specified category
    # e.g. run.categories=lookupservice
    run.categories=name_of_category

    # runs a specified test
    # e.g. run.tests=com/sun/jini/test/spec/constraint/coreconstraint/PrincipalElementsTest.td
    run.tests=path/to/test/TestName.td

<div class="space-mn"></div>
##### By specifying on the commandline
From the qa directory:
    
    ant -Drun.tests=com/sun/jini/test/spec/constraint/coreconstraint/PrincipalElementsTest.td run-tests

Existing QA tests can be found in the following path; `$RIVER_HOME/qa/src/com/sun/jini/test/**"`

<div class="space-mn"></div>
#### Categories
You can find the test categories on [Test categories](testing-categories.html)

<div class="space-mn"></div>
### JTREG tests

You must first download and install jtreg following the instructions on their site.

Some of these tests are run as BASH scripts, therefore, if running the jtreg tests on Windows a Cygwin (or similar) environment is necessary.

The JTREG tests can then be run by execute the following:

    cd $RIVER_HOME/qa
    ant harness-runtime
    ant jtreg

  - If you should cancel a test run, you must run the following before you can start the run again.

    ant jtreg-teardown

  - The `harness-runtime` target need only be run once, unless you have changed the core River code and wish to re-run the jtreg tests on the modified code

JTREG will create the directory `$RIVER_HOME/qa/jtreg/JTreport` which contains a report of the test run.

<div class="space-mn"></div>
#### Running specific JTREG tests

_todo_

<div class="space-mn"></div>
#### Known Problems
There are the following known problems with the jtreg tests:

 1. Running the tests in a Windows/Cygwin environment is not 100% working yet
 1. Some of the tests require a Kerberos environment, so these will obviously fail when no such setup is available
 1. It is known that test `net/jini/url/httpmd/TestEqual.java` fails.  Please see [Jira issue River-375](https://issues.apache.org/jira/browse/RIVER-375) for details.
