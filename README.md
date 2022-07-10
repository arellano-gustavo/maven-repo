# maven-repo
Para subir un archivo jar de terceros, la forma sería la siguiente:

```
mvn deploy:deploy-file \
    -DgroupId=com.oracle \
    -DartifactId=ojdbc6 \
    -Dversion=11.2.0.4 \
    -Dpackaging=jar \
    -Dfile=ojdbc6-11.2.0.4.jar \
    -DrepositoryId=github \
    -Durl=https://maven.pkg.github.com/arellano-gustavo/maven-repo
```

No olvidar que debe existir un archivo llamado setting.xml con el contenido siguiente:

```
<settings xmlns="http://maven.apache.org/SETTINGS/1.0.0"
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
  xsi:schemaLocation="http://maven.apache.org/SETTINGS/1.0.0
                      http://maven.apache.org/xsd/settings-1.0.0.xsd">

  <activeProfiles>
    <activeProfile>github</activeProfile>
  </activeProfiles>

  <profiles>
    <profile>
      <id>github</id>
      <repositories>
        <repository>
          <id>central</id>
          <url>https://repo1.maven.org/maven2</url>
        </repository>
        <repository>
          <id>github</id>
          <url>https://maven.pkg.github.com/arellano-gustavo/maven-repo</url>
          <snapshots>
            <enabled>true</enabled>
          </snapshots>
        </repository>
      </repositories>
    </profile>
  </profiles>

  <servers>
    <server>
      <id>github</id>
      <username>USERNAME</username>
      <password>TOKEN</password>
    </server>
  </servers>
    
</settings>
```
Obviously, in your pom.xml, the repo that should be included is:

```
<repositories>
    <repository>
        <id>github</id>
        <url>https://maven.pkg.github.com/arellano-gustavo/maven-repo</url>
    </repository>
</repositories>
```
