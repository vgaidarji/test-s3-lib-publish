# Test library publish to AWS S3

Description
-----------

This is a test project which shows how to publish artifact to AWS S3. 
S3 bucket in this case is an artifacts storage for Sonatype Nexus.

Configuration
-------------

1. Make sure your bucket is in supported by Maven Wagon [regions](https://github.com/spring-projects/aws-maven/blob/ce6a4ffbd8a59029ebe147124ac2d7ff1a7afd18/src/main/java/org/springframework/build/aws/maven/Region.java#L19). Otherwise, artifact upload will fail.
2. Specify repository in `gradle.properties`

    ```properties
    # Where "test-mobile-sonatype-nexus.example.com" is a bucket name
    RELEASE_REPOSITORY_URL=s3://test-mobile-sonatype-nexus.example.com/releases/
    SNAPSHOT_REPOSITORY_URL=s3://test-mobile-sonatype-nexus.example.com/snapshots/
    ```
3. Add username and password to `~/.gradle/gradle.properties`
    ```properties
    mavenRepositoryUsername=ACCESS_KEY_ID
    mavenRepositoryPassword=SECRET_ACCESS_KEY
    ````
4. Make sure credentials used in step 3. are from account which has access to bucket from step 2.

Upload
------

Run `./gradlew uploadArchives` to upload artifact to S3.
If everything goes fine, you'll see uploaded artifact in your bucket.

 <img src="/screenshots/test-snapshot-in-s3.png">


Additional references
---------------------

- [Using Amazon S3 as a Private Maven Repository](http://jmchung.github.io/blog/2015/03/01/using-amazon-s3-as-a-private-maven-repository/)
- [Maven Wagon](https://github.com/spring-projects/aws-maven) project

License
-------

    Copyright 2017 Veaceslav Gaidarji

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

       http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.
