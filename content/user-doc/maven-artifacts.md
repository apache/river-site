Title: Maven Artifacts
license: https://www.apache.org/licenses/LICENSE-2.0


### Maven Artifacts
Project artifacts are uploaded to [River maven repository](https://maven-repository.com/artifact/org.apache.river)
(can also be found [here](https://mvnrepository.com/artifact/org.apache.river))
and [Jini maven repository](https://maven-repository.com/artifact/net.jini)

The following is from Brian Murphy's post (not available any more) on the developer mailing list highlight
some of the history behind the River/Jini JAR artifacts.

<blockquote>
<small>
<p>
... For those who might be wondering about artifacts like jini-core.jar, jini-ext.jar, sun-util.jar, etc., although
there have been previous postings discussing how they are no longer needed, it might help some of the new folks on the
list to hear a repeat of the history of those artifacts; and why they should not be used, and why they should probably
be removed from the build.
</p>
<p>
Back in the old jini 2.x release time frame, there was quite a bit of time and thought put into how the distribution
should be re-packaged to address deployment issues; for example, better modularity, supporting overlays when upgrading,
 etc. That work resulted in the current artifact structure we now see;
 jsk-platform/jsk-lib/jsk-resources/jsk-dl/<service>/<service>-dl.
</p>
<p>
But because the team did not want to break existing deployments that relied on the old jar structure, they decided to
 also include the old artifacts in the release; along with a detailed release note explaining the new philosophy and
 encouraging folks to move to the new model, and be prepared for the removal of those old jar files down the road.
 Unfortunately, due to unforeseen events, the removal of the old unnecessary jar files never occurred, and people
 seem to still be using them (at least, based on postings on the various user lists out there).
...
</p>
</small>
</blockquote>


To see how these are used,
[download](https://www.apache.org/dyn/closer.cgi/river/river-examples-1.0/river-examples-1.0-source-release.zip)
and have a look at the river-examples source.

    <properties>
        <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
        <jsk.version>2.2.3</jsk.version>
    </properties>

    <dependencyManagement>
        <dependencies>
            <dependency>
                <groupId>net.jini</groupId>
                <artifactId>jsk-platform</artifactId>
                <version>$  {jsk.version}</version>
            </dependency>
            <dependency>
                <groupId>net.jini</groupId>
                <artifactId>jsk-dl</artifactId>
                <version>$  {jsk.version}</version>
            </dependency>
            <dependency>
                <groupId>net.jini</groupId>
                <artifactId>jsk-lib</artifactId>
                <version>$  {jsk.version}</version>
            </dependency>
            <dependency>
                <groupId>net.jini</groupId>
                <artifactId>jsk-resources</artifactId>
                <version>$  {jsk.version}</version>
            </dependency>
            <dependency>
                <groupId>net.jini</groupId>
                <artifactId>jsk-policy</artifactId>
                <version>$  {jsk.version}</version>
            </dependency>
            <dependency>
                <groupId>org.apache.river</groupId>
                <artifactId>reggie</artifactId>
                <version>$  {jsk.version}</version>
            </dependency>
            <dependency>
                <groupId>org.apache.river</groupId>
                <artifactId>reggie-dl</artifactId>
                <version>$  {jsk.version}</version>
            </dependency> 
            <dependency>
                <groupId>org.apache.river</groupId>
                <artifactId>outrigger-dl</artifactId>
                <version>$  {jsk.version}</version>
            </dependency>
            <dependency>
                <groupId>org.apache.river</groupId>
                <artifactId>start</artifactId>
                <version>$  {jsk.version}</version>
            </dependency>
            <dependency>
                <groupId>org.apache.river</groupId>
                <artifactId>tools</artifactId>
                <version>$  {jsk.version}</version>
            </dependency>
        </dependencies>
    </dependencyManagement>
    

