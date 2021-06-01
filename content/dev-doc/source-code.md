Title: Source Code
license: https://www.apache.org/licenses/LICENSE-2.0


### River source code


River uses [Subversion](http://subversion.tigris.org/) to manage its source code. Instructions on Subversion use can be found [here](http://svnbook.red-bean.com).

The source code for the various deliverables of Apache River can be freely browsed at <http://svn.apache.org/viewvc/river/>. 

####
#### Anonymous access


The Apache River source can be checked out anonymously with this command (for the jtsk deliverable):

    svn checkout http://svn.apache.org/repos/asf/river/jtsk/trunk river

The above is the 'trunk' or development branch.  As of April 2014, the latest
release was in the 2.2 branch.

    svn checkout http://svn.apache.org/repos/asf/river/jtsk/branches/2.2


####
#### Access from behind a firewall


For those users who are stuck behind a corporate firewall which is blocking http access to the Subversion repository,
you can try to access it via HTTPS:

    svn checkout https://svn.apache.org/repos/asf/river/jtsk/trunk river


####
#### Access through a proxy


The Subversion client can go through a proxy, if you configure it to do so. First, edit your "servers" configuration
file to indicate which proxy to use. The files location depends on your operating system. On Linux or Unix it is
located in the directory "~/.subversion". On Windows it is in "%APPDATA%\Subversion". (Try "echo %APPDATA%", note
this is a hidden directory.)

There are comments in the file explaining what to do. If you don't have that file, get the latest Subversion client
and run any command; this will cause the configuration directory and template files to be created.

Example : Edit the 'servers' file and add something like :


    [global]
    http-proxy-host = your.proxy.name
    http-proxy-port = 3128


####
#### Submitting a Patch

If you make changes to River, and would like to contribute the to the project, you should create a patch and post it
to the [River JIRA issue tracker](http://issues.apache.org/jira/browse/RIVER). To create a patch, simply execute the
following command:

    svn diff > your-changes.patch


If you've added new files, remember to "svn add" them so they get included in the diff.


####
#### Developer Access

Everyone can access the River Subversion repository via HTTPS, but River Committers must checkout the Subversion
repository via HTTPS.

    svn checkout https://svn.apache.org/repos/asf/river/jtsk/trunk river

To commit changes to the repository, you must set your password on the Apache Subversion server. To set your password,
 use ssh to connect to svn.apache.org, and enter the command *svnpasswd*. This will prompt you to enter a svn password
 of your choice (pick a safe password). Now, now your are ready to commit changes using your username/password.
 Execute the following command to commit your changes (svn will prompt you for your password)


    svn commit --username your-username
    Authentication realm: <https://svn.apache.org:443> ASF Committers
    Password for 'your-username': your-password


You can also pass your password on the command line directly, but this is a security problem on multiuser unix
computers (the command line arguments are available via the ps command). Here is the command if you are Windows or
a single user unix computer:

    svn commit --username your-username --password your-password

Remember to replace 'your-username' and 'your-password' with your actual username and password on svn.apache.org.
