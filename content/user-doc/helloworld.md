Title:
license: https://www.apache.org/licenses/LICENSE-2.0

# Hello World With River

**Experimental**<br/>
Warning!  The following describes how to use code which is currently only contained in a branch of River and has not been formally released yet.

## Introduction
It can be argued that part of the barrier to entry of getting working River services is the complexity and difficulty with configuring services.  The are many things that users, new and old, must remember when trying to set up new environments and tweak the configurations of their services.

The configurations themselves can be temperamental and difficult for new comers to get to grips with.  Largely, they are text files with a Java-esque content which is parsed by the <code>ServiceStarter</code>.  The other problem with the config files is ensuring that you can share configuration for certain services across the djinn.  Encapsulating configuration in Java code, which can be more easily humanly read, verified and shared is possibly a better idea than having many slightly different copies of configuration files which must then be kept in step.  The following describes how to use the "extra" bits of River to get around these issues.

## Extra River
The classes required in this documentation live outside of the main River distribution, in fact they are not part of the core of the library neither are they part of the Jini and JavaSpaces specifications. In a standard River install, they are therefore completely optional.

## Getting Started

### Prerequisites

River Extras require the following additional JARs on their runtime classpath.

* Apache Commons Collections 3.2
* Apache Commons Lang 2.6

From now on, this document will refer to these two exact file system location of these JARs as;

 * <code>$  {COMMONS_COLLECTIONS_JAR}</code>
 * <code>$  {COMMONS_LANG_JAR}</code>

### From Binary Distribution

Download the latest version of River and extract it to some directory.  From now on, this will be known as <code>$  {RIVER_HOME}</code>

See the optional part of "From Source" if you also want to build and experiment with the example service.

### From Source

You must first get the River source.  Since this code is still experimental, that means checking out the code from a trunk.  Ideally, this code will make the next release and so will come packaged as part of the River (source) distribution.

<pre><code>
$  cd ~/projects/river
$  svn co http://svn.apache.org/repos/asf/river/jtsk/skunk/easystart helloworld
$  cd helloworld
$  ant # This will build the River distribution, including the lib/extra.jar
</code></pre>

Additionally, if you want to be able to run the example code which uses this configuration technique, you must also build the JAR which contains it.  This is done by executing the following Ant command.  However, if you are only interested in using the <code>extra.jar</code> then there is no need to complete this step.

<pre><code>
$  cd ../src-extra-examples
$  ant # This will build the lib/extra-examples.jar
</code></pre>

From this point on, we shall refer to the installation of River as <code>$  {RIVER_HOME}</code>.  In this example, it would refer to directory <code>~/projects/river/helloworld</code>.

### Starting the HTTP Server

Jini/River services of course require a HTTP server.  This is easily started in such a way as it will serve all the JAR files from the $  {RIVER_HOME}/lib directory.

Open your IDE of choice, fix any build/setup errors and then setup a run configuration for the HTTP server - I use Eclipse, hence the terminology.

The main class to run is, <code>org.apache.river.extra.examples.easystart.riverservices.StartHttpServer</code> and can be found in the <code>$  {RIVER_HOME}/src-extra-examples</code> source directory.  It will need the following program arguments; 

* ~/projects/river/helloworld
* 8080

Obviously, the first argument is the value of <code>$  {RIVER_HOME}</code> and the second is the HTTP port to use.  This is the default port according to River Extras, if you want to use a different port then this will require changes (in Java code) of the configuration.

Execute this run configuration and leave it running.  You can verify that it's working correctly by using your browser or <code>wget</code> to download a sample JAR, e.g.

<code>$  wget http://localhost:8080/reggie.jar</code>

The rest of this document describes code that can be found in the <code>src-extra</code> and <code>src-extra-examples</code> source directories.

### Running Services

When running River services you will also require the following VM arguments.

<pre><code>
-Djava.security.policy=<em>$  {RIVER_HOME}</em>/src-extra/policy.all 
-Djava.rmi.server.RMIClassLoaderSpi=net.jini.loader.pref.PreferredClassProvider
-DRIVER_HOME=<em>$  {RIVER_HOME}</em>
</code></pre>

<b>Important</b>: The policy file specified above is a "grant all" policy file.  You could consider it a "disable security" security policy.  As such it is unsuitable for real-world use.

### Common Service Configuration Options

We are going to use a <code>ApplicationOptions</code> to describe certain service configuration options that will be common to all the services we're going to start.  From, <code>org.apache.river.extra.examples.easystart.StartServices</code>;

<code>
ApplicationOptions options = new ApplicationOptions();<br/>
options.setJiniPort(4162);<br/>
options.setHttpOptions("localhost", 8080, true);<br/>
options.addLookupGroup("extra").addLookupGroup("example");<br/>
options.setPackageName(ExampleService.PACKAGE);<br/>
</code>

So you can see we are using the non-default Jini port (4162).  We are also setting the configuration package name of our services to some constant as defined in <code>ExampleService.PACKAGE</code>.

We shall describe <code>ExampleService</code> later.

Next we need a factory to build our configuration objects;

<code>
ApplicationConfigurationFactory configFac = new ApplicationConfigurationFactory(options);
</code>

This class extends a River Extra class, <code>org.apache.river.extra.easystart.config.ConfigurationFactory</code>.  This base class knows how to create configuration objects for the standard River services using the djinn specific options as we have described above, the extending class also knows how to create configuration objects for our additional custom services.

### Starting the Lookup Service

Staying with the same <code>StartServices</code> class from above.

First we need to configure the lookup service and then we can start it.  This is easily done;

<pre><code>
LookupServiceConfiguration lusConfig = configFac.lookupServiceConfig();
lusConfig.addMemberGroup("extra").addMemberGroup("example");
ServiceStarter.main(lusConfig.riverConfig());
</code></pre>

Notice that we have set the lookup service's configuration's member groups to be the same as the lookup groups as defined in the <code>ApplicationOptions</code> instance above.

We now have a started lookup service; (but check your console for errors!)

### Starting the Example Service

Next we need a configuration for our example service.

The configuration is described in our extended <code>ApplicationConfigurationFactory</code>, thus;

<pre><code>
public AbstractEasyConfiguration exampleService(Name name)  {
&nbsp;&nbsp;&nbsp;&nbsp;ApplicationOptions exampleOptions = getDefaultOptions();
&nbsp;&nbsp;&nbsp;&nbsp;exampleOptions.setImplementationClass(ExampleServiceImpl.class);
&nbsp;&nbsp;&nbsp;&nbsp;exampleOptions.addInitialLookupAttribute(name);
&nbsp;&nbsp;&nbsp;&nbsp;return new AbstractEasyConfiguration(exampleOptions)  {};
}
</code></pre>

Now we know how the configuration was done.  You should also be able to see how easy it will be to extend this concept of ConfigurationFactory to handle all of your own custom services that make up your own applications.

We can start the example service in exactly the same way as we did the lookup service previously.

<code>
AbstractEasyConfiguration config = configFac.exampleService(new Name("Jeff"));
ServiceStarter.main(config.riverConfig());
</code>

Now we have successfully configured and started our example service, and in all of this we did not have to bother ourselves with any configuration file.

It should be pointed out that the services we have started are using the default policy file which is unsuitable for a live environment, since it is a "grant all" policy file that can be found in <code>$  {RIVER_HOME}/src-extra/policy.all</code>

So by defining and sharing our own implementation of the configuration factory we can be sure that all services started with configurations from that factory will be configured accordingly.  What's more, we no longer have to maintain series of configuration files which potential contain many duplicate data items.
		
## Additional Configuration

You can specify additional configuration data by creating custom <code>org.apache.river.extra.easystart.config.settings.Setting</code> objects and adding them to the <code>org.apache.river.extra.easystart.config.ApplicationOptions</code> instance before creating your configuration factory.  In the same package, there are additional extending classes of <code>Setting</code> that can be used as templates for your own configuration options.
