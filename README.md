# ionic-help
Some tweaks and helpful resources for developing with the Ionic Framework.

As I came along [that awesome gist](https://gist.github.com/denzildoyle/7ccf10aca191d0e42b7b) from [denzildoyle](https://github.com/denzildoyle), I just thought it would be great to have little repo covering some edge topics of the [Ionic Framework](http://ionicframework.com).

### Start with a ionic starter template

```
ionic start [appName] [template]
```

A list of [starter templates](https://github.com/driftyco?utf8=%E2%9C%93&query=ionic-starter) types: `maps`, `tabs`, `sidemenu`, `blank`, `salesforce`, `tests`, `complex-list`

`[template]` can be one of the types above, [a codepen.io link](http://codepen.io/ionic/pen/GpCst), [a github repo link](https://github.com/driftyco/ionic-starter-sidemenu) or an app your created in the [Creator](http://creator.ionic.io/) (`creator:[appName]`).

**Hint**: You can read more what can be used [in the source here](https://github.com/driftyco/ionic-app-lib/blob/master/lib/start.js#L160).


### External linking

```
cordova plugin add org.apache.cordova.inappbrowser
```

```js
window.open('https://mobile.twitter.com/iamdevloper', '_system', 'location=yes')"
```

Resources:
  - [Cordova InAppBrowser Documentation](https://wiki.apache.org/cordova/InAppBrowser)
  - [Nic Rabody's Launch External URLs with IonicFramework](https://blog.nraboy.com/2014/07/launch-external-urls-ionicframework/)
  - [External Links – Forum IonicFramework](http://forum.ionicframework.com/t/external-links-facebook-twitter-to-load-outside-of-app/977)
  - [Launching external maps applications (Ionic, Google Maps, Apple Maps) on Android and iOS](https://gist.github.com/mrzmyr/977fc7d8bee58db9d96f)
  - URL Schemes: [Apple Maps](https://developer.apple.com/library/ios/featuredarticles/iPhoneURLScheme_Reference/MapLinks/MapLinks.html), [Google Maps iOS](https://developers.google.com/maps/documentation/ios/urlscheme?hl=en), [Twitter](http://wiki.akosma.com/IPhone_URL_Schemes#Twitter), [Facebook](http://wiki.akosma.com/IPhone_URL_Schemes#Facebook)

### Force an orientation

To force an orientation you need to set the orientation preference in `config.xml`.

Lock app's orientation in landscape mode:
```xml
<preference name="orientation" value="landscape" />
```
Lock app's orientation in portrait mode:
```xml
<preference name="orientation" value="portrait" />
```
Set app's orientation to default:
```xml
<preference name="orientation" value="default" />
```

### Postision content at the bottom

First you have to stop the content area from scrolling.
  
```html 
<ion-content scroll="false">
```

Next what you want to do is set the a height of 100% to the scroll class which usually wraps your main content and position your content when you want it.
  
```css
.some-content{
  width: 96%;
  margin: 0 2%;
  position: absolute;
  bottom: 100px;
}
.scroll{
  height:100%;
}
```

### Hide splash screen on device ready

Install the splashscreen plugin

```
ionic plugin add org.apache.cordova.splashscreen
```

Change the defaults.xml in `myapp/platforms/{ios/android}/cordova/`

```xml
<preference name="AutoHideSplashScreen" value="false" />
<preference name="ShowSplashScreenSpinner" value="false" />
```

```js
angular
  .module('app', [])
  .run(function($ionicPlatform, $timeout) {
    $ionicPlatform.ready(function() {
      $timeout(function() {
        navigator.splashscreen.hide();
      }, 100);
   });
  })
```

In case you are using [`ngCordova`](http://ngcordova.com/docs/plugins/splashscreen/):

```js
angular
  .module('app', [])
  .run(function($ionicPlatform, $cordovaSplashscreen, $timeout) {
    $ionicPlatform.ready(function() {
      $timeout(function() {
        $cordovaSplashscreen.hide();
      }, 100);
   });
  })
```

Resources:

- [Customizing the Splash Screen](http://learn.ionicframework.com/formulas/splash-screen/)

### Publish to Google Play Store

Resources:

- [Ionic Publishing Guide](http://ionicframework.com/docs/guide/publishing.html)
- [Steven Iseki – Getting started with Ionic](https://coderwall.com/p/vvkyra/getting-started-with-ionic)


### Publish to Apple App Store

Resources:

  - [Deploy an Ionic App to the iOS App Store – Medium](https://medium.com/@_qzapaia/deploy-an-ionic-app-to-the-ios-app-store-702c79a2dd97)
  - [How to submit iOS app to app store using Xcode – Forum IonicFramework](http://forum.ionicframework.com/t/how-to-submit-ios-app-to-app-store-using-xcode/1795/5)
  - [Steven Iseki – Getting started with Ionic](https://coderwall.com/p/vvkyra/getting-started-with-ionic)

### CLI Shortcuts

```bash
# ionic aliases
alias iba='ionic build android'
alias ibi='ionic build ios'
alias ira='ionic run android'
alias iri='ionic run ios'
alias ibra='iba && ira'
alias ilra='ionic run android -l -c -s'
alias ilri='ionic run ios -l -c -s'
alias ionic-handleit='ionic run android && ionic run ios'
```

### Common Pitfalls / Known Errors

> Error initilizing Cordova: Class not found

```
cordova platform rm android
cordova platform add android
```

### Blogs

- [iLee](http://ilee.co.uk/)
- [Ionic Blog](http://blog.ionic.io/), obviously