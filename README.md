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
