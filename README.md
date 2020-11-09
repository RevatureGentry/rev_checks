# Getting Started
* The _Maven Checkstyle Plugin_ is a programmatic means of validating source code style conformity
* The `rev_checks.xml` describes the set of rules which Checkstyle will be enforcing, with [Markdown examples found here](./examples)
* You must apply the _`pom.xml` Setup_
    * The choice is yours to configure your IDE; It can assist with actions such as `auto-formatting`
    
## `pom.xml` Setup
1. Create (or update the existing) `<properties>` (Example found at line 10)
    * Copy the following properties to your `pom.xml`
       ```xml
      <properties>
          <!-- ... other properties -->
          <checkstyle-maven-plugin.version>3.1.1</checkstyle-maven-plugin.version>
          <puppycrawl-checkstyle.version>8.29</puppycrawl-checkstyle.version>
      </properties>
      ``` 
2. Create (or update the existing) `<build>` tags with the following plugin (Example found at line 25)
    ```xml
   <plugins>
       <plugin>
           <groupId>org.apache.maven.plugins</groupId>
           <artifactId>maven-checkstyle-plugin</artifactId>
           <version>${checkstyle-maven-plugin.version}</version> <!-- Note use of property -->
           <configuration>
               <configLocation>rev_checks.xml</configLocation> <!-- Can vary based on the location on your machine -->
               <encoding>UTF-8</encoding>
               <consoleOutput>true</consoleOutput>
               <failsOnError>true</failsOnError>
               <linkXRef>false</linkXRef>
           </configuration>
           <executions>
               <execution>
                   <id>validate</id>
                   <phase>validate</phase>
                   <goals>
                       <goal>check</goal>
                   </goals>
               </execution>
           </executions>
           <dependencies>
               <dependency>
                   <groupId>com.puppycrawl.tools</groupId>
                   <artifactId>checkstyle</artifactId>
                   <version>${puppycrawl-checkstyle.version}</version> <!-- Note use of property -->
               </dependency>
           </dependencies>
       </plugin>
   </plugins>
   ```
3. Create (or update the existing) `<reporting>` tag with the following plugin
    ```xml
    <plugins>
        <plugin>
            <groupId>org.apache.maven.plugins</groupId>
            <artifactId>maven-checkstyle-plugin</artifactId>
            <version>${checkstyle-maven-plugin.version}</version> <!-- Note use of property -->
            <configuration>
                <configLocation>rev_checks.xml</configLocation> <!-- Can vary based on the location on your machine -->
            </configuration>
        </plugin>
    </plugins>
   ```

## IDE Setup
* Eclipse/STS
    1. Download and Install [this plugin](https://marketplace.eclipse.org/content/checkstyle-plug) to your local instance
        * To get to the appropriate menu, navigate to `Help -> Eclipse Marketplace`
        * Restart the IDE as needed
    2. To import our configuration, navigate to `Windows -> Preferences -> Checkstyle`
    3. Create a `New` configuration
        * Supply the name `Revature Checks`
        * Click the _Import_ button to open a wizard to select the filepath
    4. Click on the newly created configuration and then mark `Set as Default`
    5. Apply and Close!
* VS Code
    1. Download and Install [this plugin](https://marketplace.visualstudio.com/items?itemName=shengchen.vscode-checkstyle) to your local instance
    2. Once installed, copy over the `rev_checks.xml` to your project's root directory
        * Right click on the `rev_checks.xml` file and select _Set the Checkstyle Configuration File_
* IntelliJ
    1. Download and Install [this plugin](https://plugins.jetbrains.com/plugin/1065-checkstyle-idea) to your local instance
    2. Navigate to `File -> Settings -> Editor -> Code Style`
        * Find the gear icon, click on it and select _Import Scheme_
    3. (Optional) Choose to apply this setting as the IDE Default or scoped to the current project
   
