Title:     Building a release
license: https://www.apache.org/licenses/LICENSE-2.0


## Building a release major release

**n**.**m** **n** = major release number, **m** = minor release number


<div class="space-mn"></div>
### KEYS file

Add your key to the KEYS file in the repo


<div class="space-mn"></div>
### Checkout The Source

    svn checkout https://svn.apache.org/repos/asf/river/jtsk/trunk river


<div class="space-mn"></div>
### Pre release checks

 * River-trunk should run successful.
 * River-verify should run successful. (not yet?)


<div class="space-mn"></div>
### Gather Release Notes From Jira

First [manage the versions][5] of River using Jira.  Make sure there is an appropriate release that Jira issues are have been assigned to.  You can then view the [Roadmap][4] screen in Jira to create the release and make sure that the correct Jira issues are associated to it.

Move the Jira issues around appropriately, especially if you're releasing before all the issues have been resolves.  In this case, you need to postpone the remaining issues until a later release.

You can then use Jira to generate the release notes.  This is done Road Map --> Release --> Summary --> Release Notes (next to "Filters").

The release notes need to be pasted into;

    river/trunk/src-doc/static/release-notes/index.html


<div class="space-mn"></div>
### Update Version Numbers

There are version numbers in the following places that need to be updated with the new release number/name.

  - com.sun.jini.constants.VersionConstants.java (SERVER_VERSION)
  - river/trunk/src-doc/static/release-notes/index.html (version number)

In the above HTML page, there is also a section on "changes by component" which should also be updated.  This should be easy to do by referring to the Jira-generated release notes.


<div class="space-mn"></div>
### Branch the repository

    svn cp https://svn.apache.org/repos/asf/river/jtsk/trunk https://svn.apache.org/repos/asf/river/jtsk/branches/$VERSION


<div class="space-mn"></div>
### Tag the repository

    svn cp https://svn.apache.org/repos/asf/river/jtsk/trunk https://svn.apache.org/repos/asf/river/jtsk/tags/$VERSION


<div class="space-mn"></div>
### Build the release products

    ant -Dversion=$VERSION clean release


<div class="space-mn"></div>
### Rat Reports

    ./rat_reports.sh


<div class="space-mn"></div>
### Sign the release

  - [General Apache Signing Details][1]
  - [Release Signing Instructions][2] *See code below, link has a typo in it
  - [Checksum Instructions][3]

    cd dist
    for f in $( ls ); do
    	gpg --armor --output $f.asc --detach-sign $f
    	gpg --print-md SHA512 $f > $f.sha
    done;


<div class="space-mn"></div>
### Test the release

    cp dist/apache-river-$VERSION.tar.gz $SOMEWHERE_ELSE
    cd $SOMEWHERE_ELSE
    tar xvf apache-river-$VERSION.tar.gz
    cd apache-river-$VERSION
    ant build


<div class="space-mn"></div>
### Upload the release

    scp RAT* username@people.apache.org:~/public_html/river/
    cd dist
    scp * username@people.apache.org:~/public_html/river/


<div class="space-mn"></div>
### Allow the community to evaluate the release products

    * announce availability of candidate on river-dev.
    * start [VOTE] thread. 


<div class="space-mn"></div>
### Publish release on website
 * checkout the site 
 * Extract the javadocs from the release archive into ...
 * commit
 * go to the CMS webclient, and publish the site.


  [1]: http://www.apache.org/dev/release-signing.htm
  [2]: http://www.apache.org/dev/release-signing.html#sign-release
  [3]: http://www.apache.org/dev/release-signing.html#sha-checksum
  [4]: https://issues.apache.org/jira/browse/RIVER#selectedTab=com.atlassian.jira.plugin.system.project%3Aroadmap-panel
  [5]: https://issues.apache.org/jira/secure/project/ViewProject.jspa?pid=12310600
