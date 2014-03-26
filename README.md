## JS SensorWeb Client Customization Example
This project aims to give an example project for customizations around the [52°North JS SensorWeb Client](https://github.com/52North/js-sensorweb-client). The actual goal is to show how the client code base can be used within a customized context. By [using Git submodules](http://git-scm.com/book/en/Git-Tools-Submodules) one can put the customized project in a separate repository without leaving track of further improvements, features and bugfixes on the current root project.

### How it Works
If you want to perform customizations on the [52°North JS SensorWeb Client](https://github.com/52North/js-sensorweb-client) you either could [clone this repository](https://github.com/ridoo/js-scw-custom) and start from there or you start from scratch in an empty project. For both you will need [Maven to be installed](http://maven.apache.org).
```
$ mkdir custom-project ; cd custom-project
$ git init ; git add submodule git@github.com:52North/js-sensorweb-client js-sensorweb-client 
$ cp js-sensorweb-client/pom.xml .
```
From here you do

1. make changes to the `pom.xml` so that the path relevant properties reference the file under `js-sensorweb-client`. The sample `pom.xml` makes use of a [`${_basedir}` property](https://github.com/ridoo/js-scw-custom/blob/master/pom.xml#L19) which is not present in the current version of the [JS SensorWeb Client](https://github.com/52North/js-sensorweb-client). However, this may change as we will see, if this approach makes sense.
1. test if everything builds as normal by doing `mvn clean install -P minify`
1. to make changes, copy those files to some place under `custom-project`, for example 

```
$ mkdir js/models
$ cp js-sensorweb-client/WebContent/js/models/settings.js js/models
```

1. now adjust the reference in the `pom.xml` (keep in mind that [the minify plugin](http://samaxes.github.io/minify-maven-plugin/) appends `js` and `css` per default), for example

```
<!-- get from ${basedir}/js-sensorweb-client/WebContent/css/../../../css/models/ -->
<cssSourceFile>../../../css/mainstyles.css</cssSourceFile>
```


### Build the client

To build the client as war file:
```
mvn clean install
```
To build a minified version, use the profile 'minify'
```
mvn clean install -P minify
```

### Contacts

For questions and comments please contact [Henning Bredel](https://github.com/ridoo)
