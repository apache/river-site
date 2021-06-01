Title: Continuous Integration
license: https://www.apache.org/licenses/LICENSE-2.0


### Continuous Integration

In order to find problems early, river uses [Continuous Integration](http://en.wikipedia.org/wiki/Continuous_integration). 

After changes the builds are scheduled on the [Apache build server](https://builds.apache.org/).

The following jobs are used:

Job | Role
- | -
River-trunk-* | Builds the trunk, and check for compilation errors only
River-QA-* | Builds the trunk and run QA tests 
River-verify |
River-verify-generics |
River-QA-Runtime |

For their current status, see: <https://builds.apache.org/view/M-R/view/River/>

<div class="space-mn"></div>
### River-trunk jobs
The River trunk build is only run on Ubuntu. The naming scheme is:
River-trunk-[jdkid]


<div class="space-mn"></div>
### River-QA- jobs
The River QA jobs naming scheme used is: River-QA-[platformid]-[jdkid] optional [-branchid]

The River-trunk-QA-* jobs, build the river-runtime and the river-qa, 
and tests the river-runtime with the river-qa framework.


<div class="space-mn"></div>
### Platforms and Jdks
The current platforms are: Solaris, Ubuntu, Windows

The current jdk ids are: jdk6 jdk7

The ant version used is: version 1.7

