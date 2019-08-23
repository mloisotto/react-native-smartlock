# react-native-smartlock

A simple wrapper for Smart Lock authentication of Google for React Native. Only for Android.

#Installation

$ npm install react-native-smartlock --save

### <a id="installation_android"> Android

##### **android/app/build.gradle**
Add the project to your dependencies
```gradle
dependencies {
...
compile project(':react-native-smartlock')
}
```

##### **android/settings.gradle**

Add the project

```gradle
include ':react-native-smartlock'
project(':react-native-smartlock').projectDir = new File(rootProject.projectDir, '../node_modules/react-native-smartlock/android')
```

##### **MainApplication.java**
Add:


1. `import com.google.smartlock.smartlockrn.SmartLockPackager;`

2.  In the `getPackages()` method register the module:
`new SmartLockPackager()`

So `getPackages()` should look like:

```java
@Override
protected List<ReactPackage> getPackages() {
    return Arrays.<ReactPackage>asList(
    new MainReactPackage(),
    new SmartLockPackager(),
    //.....
  );
}
```

# Usage

```javascript
import smartLock from 'react-native-smartlock';
```

```javascript
smartLock.getCredentials()
  .then(credentials => {
      console.log(credentials);
      // user has permissions
  })
  .catch(err => {
      console.log(err);
      // user doesn't have permissions or cancelled login
  });

```

```javascript
smartLock.saveCredentials(username, JSON.stringify({'password': password}))
  .then(() => {
       console.warn('saved');
  })
  .catch(err => {
       console.warn(err);
  });

```


