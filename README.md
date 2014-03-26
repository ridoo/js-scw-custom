## JS SensorWeb Client Customization Example
This project aims to give an example project for customizations around the [52°North JS SensorWeb Client](https://github.com/52North/js-sensorweb-client). The actual goal is to show how the client code base can be used within a customized context. By using submodules one can put the customized project in a separate repository without leaving track of further improvements, features and bugfixes on the current root project.


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

For questions and comments please contact [Jan Schulte](mailto:j.schulte@52north.org)
