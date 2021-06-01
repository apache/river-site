Title: Development Process
license: https://www.apache.org/licenses/LICENSE-2.0


[TOC]

### River Development Process
<div class="space-lg"></div>

#### River build server

River is built on the Apache Hudson server.  The projects can be found [here](https://hudson.apache.org/hudson/view/M-R/view/River/). More on this process: [Continuous Integration](ci.html)

<div class="space-mn"></div>
#### Tracking issues and changes

* A JIRA issue is required for any substantive change.
In order to keep the list of JIRA issues under control, it is expected that any controversial issue or user request for a feature or design change be discussed on the dev list prior to entering it into JIRA.

* JIRA issues are not needed for small (e.g., typos) changes.

* Issue discussions
The preferred place of discussion on issues is the river-dev mail list. A link to the beginning of the mail thread on the issue should be placed in the JIRA issue so that users looking through JIRA can easily view the thread of discussion on an issue. Please keep the Subject line the same so that the email thread hangs together.  It's also recommended that a summary/conclusion on the thread be recorded in the JIRA issue itself.


<div class="space-mn"></div>
#### Handling Security -related Issues

There are three options associated with the "Security Level" field in the JIRA instance:
* "None"
* "Security risk, visible to committers" - only committers have access to the issue with this option set
* "Security risk, visible to anyone" - the issue has a security risk associated with it, and the committers understand the impact. A resolution/fix has been developed.

When a potential security -related issue is identified in the River sourcebase, initial discussion on it should occur on the private PPMC list.  If the person(s) who identified the issue are not on the PPMC, they should be included in the discussion.

If the issue is acknowledged as a valid security issue, a JIRA issue needs to be created with the "Security Level" field marked to "Security risk, visible to committers".

As soon as appropriate (for example, when the impact is understood and/or there is a resolution/fix developed), the "Security Level" should be changed to "Security risk, visible to anyone" and an explanation/discussion should occur in the broader River community on the river-dev list.

<div class="space-mn"></div>
#### Code Reviews

* for public API changes:
[RTC](http://apache.org/foundation/glossary.html#ReviewThenCommit) These changes have potentially broad effects on developers and users, and therefore will require a code review and vote. Since some of these changes will affect the API docs ('specs'), everyone within the Jini/River community is encouraged to review and vote. The Committer votes are binding, but the sentiment of the entire community will be strongly considered.

* for all other changes:
[CTR](http://apache.org/foundation/glossary.html#CommitThenReview) Although CTR is what is specified, developers should feel comfortable requesting the list for peer review before committing.


<div class="space-mn"></div>
#### Testing

Developing test cases and running test suites are desired but not required prior to an integration.  If unit tests are
created for a change, the developer is encouraged to add them to the JIRA issue for sharing. <br>
Here is a list of individually executable
<a href="javascript:void(0);" data-toggle="modal" data-target="#myModal">test categories</a>.

<div id="myModal" class="modal fade" role="dialog">
  <div class="modal-dialog">
    <div class="modal-content">
      <div class="modal-header">
        <button type="button" class="close" data-dismiss="modal" aria-hidden="true">&times;</button>
        <h4 class="modal-title">Test categories</h4>
      </div>

      <div class="modal-body">
        <div class="list-group">
              <a href="#" class="list-group-item">activation</a>
              <a href="#" class="list-group-item">activation_spec</a>
              <a href="#" class="list-group-item">allgroups</a>
<a href="#" class="list-group-item">basicinvocationdispatcher</a>
<a href="#" class="list-group-item">basicinvocationdispatcher_spec</a>
<a href="#" class="list-group-item">basicinvocationhandler</a>
<a href="#" class="list-group-item">basicinvocationhandler_spec</a>
<a href="#" class="list-group-item">basicobjectendpoint</a>
<a href="#" class="list-group-item">basicobjectendpoint_spec</a>
<a href="#" class="list-group-item">config</a>
<a href="#" class="list-group-item">config_spec</a>
<a href="#" class="list-group-item">constraint</a>
<a href="#" class="list-group-item">constraint_spec</a>
<a href="#" class="list-group-item">coreconstraint</a>
<a href="#" class="list-group-item">coreconstraint_spec</a>
<a href="#" class="list-group-item">discardproblem</a>
<a href="#" class="list-group-item">discoverymanager</a>
<a href="#" class="list-group-item">discoverymanager_impl</a>
<a href="#" class="list-group-item">discoverymanager_spec</a>
<a href="#" class="list-group-item">discoveryproviders</a>
<a href="#" class="list-group-item">discoveryproviders_impl</a>
<a href="#" class="list-group-item">discoveryservice</a>
<a href="#" class="list-group-item">discoveryservice_impl</a>
<a href="#" class="list-group-item">discoveryservice_spec</a>
<a href="#" class="list-group-item">discoveryserviceevent</a>
<a href="#" class="list-group-item">discoveryservicelease</a>
<a href="#" class="list-group-item">end2end</a>
<a href="#" class="list-group-item">end2end_impl</a>
<a href="#" class="list-group-item">eventmailbox</a>
<a href="#" class="list-group-item">eventmailbox_impl</a>
<a href="#" class="list-group-item">eventmailbox_spec</a>
<a href="#" class="list-group-item">export</a>
<a href="#" class="list-group-item">export_spec</a>
<a href="#" class="list-group-item">fiddleradmin</a>
<a href="#" class="list-group-item">fiddlerfiddleradmin</a>
<a href="#" class="list-group-item">fiddlerjoinadmin</a>
<a href="#" class="list-group-item">id</a>
<a href="#" class="list-group-item">id_spec</a>
<a href="#" class="list-group-item">iiop</a>
<a href="#" class="list-group-item">iiop_spec</a>
<a href="#" class="list-group-item">impllocatordiscovery</a>
<a href="#" class="list-group-item">impllookupdiscovery</a>
<a href="#" class="list-group-item">implservicediscovery</a>
<a href="#" class="list-group-item">implservicediscoveryevent</a>
<a href="#" class="list-group-item">io</a>
<a href="#" class="list-group-item">io_spec</a>
<a href="#" class="list-group-item">javaspace</a>
<a href="#" class="list-group-item">javaspace05_conformance</a>
<a href="#" class="list-group-item">javaspace_conformance</a>
<a href="#" class="list-group-item">javaspace_impl</a>
<a href="#" class="list-group-item">javaspace_impl_admin</a>
<a href="#" class="list-group-item">javaspace_impl_api</a>
<a href="#" class="list-group-item">javaspace_impl_javaspace05</a>
<a href="#" class="list-group-item">javaspace_impl_leasing</a>
<a href="#" class="list-group-item">javaspace_impl_matching</a>
<a href="#" class="list-group-item">javaspace_impl_notify</a>
<a href="#" class="list-group-item">javaspace_impl_transaction</a>
<a href="#" class="list-group-item">javaspace_spec</a>
<a href="#" class="list-group-item">jeri</a>
<a href="#" class="list-group-item">jeri_spec</a>
<a href="#" class="list-group-item">joinmanager</a>
<a href="#" class="list-group-item">joinmanager_impl</a>
<a href="#" class="list-group-item">joinmanager_spec</a>
<a href="#" class="list-group-item">jrmp</a>
<a href="#" class="list-group-item">jrmp_spec</a>
<a href="#" class="list-group-item">loader</a>
<a href="#" class="list-group-item">loader_spec</a>
<a href="#" class="list-group-item">locatordiscovery</a>
<a href="#" class="list-group-item">locatordiscovery_impl</a>
<a href="#" class="list-group-item">locatordiscovery_spec</a>
<a href="#" class="list-group-item">lookupdiscovery</a>
<a href="#" class="list-group-item">lookupdiscovery_impl</a>
<a href="#" class="list-group-item">lookupdiscovery_spec</a>
<a href="#" class="list-group-item">lookupservice</a>
<a href="#" class="list-group-item">lookupservice_impl</a>
<a href="#" class="list-group-item">lookupservice_spec</a>
<a href="#" class="list-group-item">policyprovider</a>
<a href="#" class="list-group-item">policyprovider_spec</a>
<a href="#" class="list-group-item">proxytrust</a>
<a href="#" class="list-group-item">proxytrust_spec</a>
<a href="#" class="list-group-item">reliability</a>
<a href="#" class="list-group-item">renewalmanager</a>
<a href="#" class="list-group-item">renewalmanager_spec</a>
<a href="#" class="list-group-item">renewalservice</a>
<a href="#" class="list-group-item">renewalservice_impl</a>
<a href="#" class="list-group-item">renewalservice_spec</a>
<a href="#" class="list-group-item">scalability</a>
<a href="#" class="list-group-item">security</a>
<a href="#" class="list-group-item">security_spec</a>
<a href="#" class="list-group-item">servicediscovery</a>
<a href="#" class="list-group-item">servicediscovery_impl</a>
<a href="#" class="list-group-item">servicediscovery_spec</a>
<a href="#" class="list-group-item">servicediscoverycache</a>
<a href="#" class="list-group-item">servicediscoverydiscovery</a>
<a href="#" class="list-group-item">servicediscoveryevent</a>
<a href="#" class="list-group-item">servicediscoverylookup</a>
<a href="#" class="list-group-item">snapshot</a>
<a href="#" class="list-group-item">spec</a>
<a href="#" class="list-group-item">speclocatordiscovery</a>
<a href="#" class="list-group-item">speclookupdiscovery</a>
<a href="#" class="list-group-item">specservicediscovery</a>
<a href="#" class="list-group-item">specservicediscoverycache</a>
<a href="#" class="list-group-item">specservicediscoverydiscovery</a>
<a href="#" class="list-group-item">specservicediscoveryevent</a>
<a href="#" class="list-group-item">specservicediscoverylookup</a>
<a href="#" class="list-group-item">start</a>
<a href="#" class="list-group-item">start_impl</a>
<a href="#" class="list-group-item">stress</a>
<a href="#" class="list-group-item">test_set00</a>
<a href="#" class="list-group-item">test_set01</a>
<a href="#" class="list-group-item">test_set02</a>
<a href="#" class="list-group-item">test_set03</a>
<a href="#" class="list-group-item">test_set04</a>
<a href="#" class="list-group-item">thread</a>
<a href="#" class="list-group-item">thread_impl</a>
<a href="#" class="list-group-item">txnmanager</a>
<a href="#" class="list-group-item">txnmanager_impl</a>
<a href="#" class="list-group-item">txnmanager_spec</a>
<a href="#" class="list-group-item">url</a>
<a href="#" class="list-group-item">url_spec</a>
            </div>
      </div>
      <div class="modal-footer">
        <button type="button" class="btn btn-default" data-dismiss="modal">Close</button>
      </div>
    </div>
  </div>
</div>




<div class="space-mn"></div>
#### Version Numbering

Each Apache River deliverable has a version number of:

  `m.n.r`

 - `m` = major version
 - `n` = minor version
 - `r` = maintenance version

The major version number will in general only be increased in case of major changes that might introduce compatibility problems or represent some fundamental improvements. The minor versions reflect the various feature releases, the last part of the version number reflects the maintenance release.


<div class="space-mn"></div>
#### Branching Policy

Ongoing development for the next release takes place in the `/trunk`. Once feature complete for a (non maintenance) release the trunk is branched into `/branches/<m.n>` which in general also reflects the moment a release candidate is presented to the public in a fairly short period of time. Ongoing development continues in the `/trunk`, issues found against the release candidate will be fixed in `/branches/<m.n>` and likely merged into the `/trunk`.

Once a release candidate is ready for a first customer release `/branches/<m.n>` is branched into `/tags/<m.n>.0`. When support is required for a particular release `m.n`, the development for a fix-release is conducted in `/branches/<m.n>`. When a bug-fix release is ready it is branched into `/tags/<m.n.r>` where `r` is a positive number and increased for each maintenance release.

Although ongoing development should take place in `/trunk`, there is a `/skunk` branch that can be utilized for 'experimental' work that must not disturb the `/trunk`, that needs to be visible to others and/or might require participation of others. In general the lifetime of such branch should be short to give it a chance of successful integration into the `/trunk` when the 'experiment' has been found valuable.

*Summarized*

|branch|description|
|------|-----------|
|`.../river/<product>/trunk`|mainline development|
|`.../river/<product>/branches`|maintenance branches|
|`.../river/<product>/tags`|frozen release tags|
|`.../river/<product>/skunk`|development and 'skunk works' branches|

<pre>
/trunk
   |
   |--------  /branches/2.1/
   |        \
   |         \ -------  /tags/2.1.0/
   |          \
   |           \ -------  /tags/2.1.1/
   |            \
   |
   |--------  /branches/2.2/
   |        \
   |         \ -------  /tags/2.2.0/
   |          \
   |
   |--------  /skunk/<catchy_name>
   |
   |
   |--------  /branches/3.0/
   |        \
   |         \ -------  /tags/3.0.0/
   |          \
   |           \ -------  /tags/3.0.1/
</pre>


<div class="space-sm"></div>
### Coding conventions

<div class="space-mn"></div>
#### Indentation
Tabs are not used. Default indentation is 4 spaces.

<div class="space-mn"></div>
#### Other
Contributors are advised to read the [Code Conventions for the Java](http://www.oracle.com/technetwork/java/codeconvtoc-136057.html)
and try to adhere as much as possible to these conventions.

<div class="space-mn"></div>
#### Reformatting
If the reformatting involves a large part of the code,
a clearly labeled 'reformatting' commit in between is recommended.
Keeping your reformatting changes limited,
reduces the change of merging conflicts by your fellow committers.

<div class="space-mn"></div>
#### Older sources
We do not actively search and reformat source files
that are not formatted according to this convention.

Older sources are best viewed with tab stops at 8 space
intervals.
