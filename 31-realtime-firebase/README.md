# Using Firebase references for real-time updates

Install the Firebase library via Bower.

```
bower install firebase --save
```

Add the RequireJS config entry for it.

```js
"firebase": "../lib/bower_components/firebase/firebase"
```

Add the following shim.

```js
"firebase": {
  exports: "Firebase"
}
```

We've been using the `populate-songs` module to make an XHR call to get our songs up until this point, for the Firebase API allows us to create a direct reference to a Firebase URL and attach an event handler that will execute code whenever anything changes at that location.

Let's see how this works.

```js
// Create a reference to your Firebase database
var myFirebaseRef = new Firebase("https://nss-demo-instructor.firebaseio.com");

// Listen for when anything changes on the "songs" key
myFirebaseRef.child("songs").on("value", function(snapshot) {

  // Store the entire songs key in a local variable
  var allSongsObject = snapshot.val();

  // Bind the allSongsObject to the song list Handlebar template
  
  // Bind the unique artists to the artists template

  // Bind the unique albums to the albums template

});
```

Once you get this working, click on one of the delete buttons, or add a new song, and the `on("value")` event will trigger immediately and your view of songs updates.
