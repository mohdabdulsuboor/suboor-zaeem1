### :camel: command based tasks
---
#### Task1: Install Jenkins
* launch the Ubuntu18 server with the url provided by the trainer. On this server you will install Jenkins & nexus
* __DO NOT CLOSE THE SESSION UNTIL THE WORKSHOP IS COMPLETED. ELSE YOU WILL HAVE TO START FROM BEGINNING__
* follow the steps on the launched environment to install java,Jenkins
* once jenkins is installed, launch the Jenkins UI and complete the installation(new user creation/plugins installation)
* Login to Jenkins 
* __run an infinite while loop on `Terminal3` to keep the session alive__
    + click on `Terminal3`
    + run the below script (this script will display `date` every 10 seconds)
    `while true; do date;sleep 10; done`

#### Task2: Install nexus 
* follow the steps to install nexus server on the same Ubuntu server
* Launch nexus interface and change the default password to something new
* DO NOT enable `anonymous access`

#### Task3: Jenkins plugins Installation
* Install the following plugins in jenkins (Jenkins Dashboard -> Manage Jenkins -> Manage Plugins)
    + slack Notification Plugin
    + nexus artifact uploader
    + nexus platform 
    + git parameter plugin
    + pipeline utility steps plugin 
    + disk-usage plugin 
    + Dashboard View 

#### Task4: Install & configure Maven
* `maven` is a tool to build java artifacts. It should be present on the Jenkins server to compile java code during jenkins jobs
```
apt install maven       # install maven
mvn -verion             # check version of maven
echo $JAVA_HOME         # check JAVA_HOME location . 
$JAVA_HOME/bin/java --version   # check java version
```
* go to Jenkins Dashboard -> Manage Jenkins -> Global Tool configuration  -> Add Maven
* give `Name` as `Maven` 
* Unselect `Install automatically`  -> give `MAVEN_HOME` as `/usr/share/maven`
* click `Apply` 

#### Task5: Nexus Repository Configuration on Jenkins
* After installing `nexus artifact uploader` & `nexus platform` plugins , it needs to be configured
* we will provide the details of our nexus server in this plugin
* go to Jenkins Dashboard -> Manage Jenkins -> Configure System -> scrolldown to `Sonatype Nexus`
    + `Add Nexus Manager Server` -> `Nexus Repository Manager 3.x Server`
    + `Display name` -> `nexus3-server`
    + `Server ID`    -> `NEXUS01`
    + `Server URL`   -> `http://<ip-of-your-vm>:8081`
    + `Credentials`  -> click `Add` -> `Jenkins` -> provide `username/password` of nexus server that was created just now
    + `Test Connection` 
    + `Apply`

#### Task6: slack configuration for notifications
* after installing `slack notifications` plugin, configure the settings of this plugin so that jenkins can send notifications to slack
* in our case, we are going to send build notifications to `devops-cloud` channel on our slack 
* go to Jenkins Dashboard -> Manage Jenkins -> Configure System -> scrolldown to `Slack`
    + `Workspace` -> `ncodeit`
    + `Credentials`  -> click `Add` -> `Jenkins` -> under `Kind` select  `Secret text`
        + for `Secret` give as `mVpee4Ly9JRAKwzRj4JSEYiG` 
        + for `ID`  give `slack-id-for-jenkins-alerts`
    + `Test Connection`     -> Make sure its `Success`
    + `Apply`

#### Task7: Free style job configuration
* Lets create the first Jenkins Job , its a simple `Free style` job
* go to Jenkins Dashboard 
    + New Item -> give `01-freestyle-job`
    + under `Source Code Management` select `Git`
    + for `Repository URL` give `https://github.com/betawins/spring3-mvc-maven-xml-hello-world-1.git`
    + for `Branch to Build` give `*/master`
    + under `Build` -> `Invoke Artifactory Maven 3` 
        + for `Maven versio` give `Maven`
        + for `Goals and Options` give `clean package` 
    + under `Nexus Artifact Uploader` 
        + `Nexus Version` give `NEXUS3`
        + `Protocol` give `HTTP`
        + `Nexus Url` give `<ip-of-your-server>:8081`
        + `Credentials`  , select the credentials created earlier for nexus user
        + `GroupId` give `com.ncodeit`
        + `Version` give `${BUILD_NUMBER}`
        + `Repository` give `maven-public`
        + `ArtifactId` give `ncodeit-hello-world`
        + `Type` give `war`
        + `File` give `target/ncodeit-hello-world-$BUILD_NUMBER.war `      
    + under `Post-build Actions`
        + select `Slack Notifications`
            + select all options
    + `Apply`

#### Task8: Run the free style job and check if the Artifact reached nexus repo
* go to Jenkins Dashboard -> click the newly created job `01-freestyle-job`
    + `Build now` 
    + under `Build History` -> click on latest running build 
    + clikc `Console Output` 
    + wait till `Finished: SUCCESS`
* login to nexus repository
    + click `Browse`
    + click `maven-public`
    + 


#### Task9: parameterized job configuration
#### Task10: scripted pipeline configuration
#### Task11: declarative pipeline configuration
#### Task12: 
---
---
### :rocket: scenario based tasks 
#### scenario1: 
#### scenario2: 
#### scenario3: 
#### scenario4: 
#### scenario5: 