Title: Found a Bug
license: https://www.apache.org/licenses/LICENSE-2.0

### Found a Bug?


If you think you've found a problem with Apache River you can search JIRA, our issue-tracking system, to see if the
problem has already been noted (visit [JIRA](http://issues.apache.org/jira/browse/RIVER)). If the issue is not listed
there, you can add a new JIRA issue describing it, please include detailed steps to reproduce the problem. Often it
is best to raise an issue not yet listed in JIRA first on the River Developer mailing list (see
[Mailing Lists](mailing-lists.html)) before adding it directly in JIRA.

If you have a fix for the issue, you can generate a patch file to send the fix to us. You need to check out the
current source code from Subversion, make the necessary changes, and then do a full build. And, of course, confirm
that the problem is actually fixed. Then, go to the base directory of your RIVER checkout, and to generate a patch file
run a command like:

`svn diff > fix-for-my-bug.patch`


To submit a patch, create an issue in JIRA that describes the problem, and add your patch file as an attachment.
Please include detailed steps to reproduce the problem in the issue description, and a test case in the patch where possible.

Thanks for interest, and working with us to improve Apache River!
