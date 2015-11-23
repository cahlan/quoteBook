<img src="https://devmounta.in/img/logowhiteblue.png" width="250" align="right">

quoteBook
=========

##Objective
Use Angular and services to create an application that manages famous quotes

###Step 1: Set up your Structure
The first step as you're getting started with setting up Angular apps is to create your foundation, then check to make sure your controller is tied to the view as it should be.
* Create an index.html and a style.css file
* Create a folder called js
* In the js folder, create an app.js, dataService.js, and a mainCtrl.js file
* Link your style.css sheet to your index.html page
* In your index.html file create the basic structure of your html, be sure to include ng-app="quoteBook" and ng-controller="mainCtrl" to the appropriate places
* In your app.js file set up the main module for your Angular app like you have previously. 
* Now in your mainCtrl.js, file set up your first controller (mainCtrl).

Remember, we're 'getting' the quoteBook module rather than 'creating' (`[]`) it. It's really important to remember that whenever you add a new js file, you need to include that new file in your index.html file in a script tag.
* In your index.html file before the body tag closes, include script tags which link to all your Angular files in the 'js' folder.
* Now that your app and controller are set up and they're linked in your html page, add a test property to your scope object in your controller then verify that it works `{{test}}` in your html page.
* If you see the text you entered into $scope.test in your view, continue to the next step. If not, check your console for any errors.

###Step 2: Set up your Angular Service
The whole point of this repo is to get used to having your main data originating from a service and not a controller. Head over to your dataService.js file and create the dataService. 

```javascript
angular.module('quoteBook').service('dataService', function(){
    //...
})
```

* After you've created the service (and made sure you included the file in your index.html file), add the following array in your service.

```javascript
  var quotes = [
    { text: 'Life isn\'t about getting and having, it\'s about giving and being.', author: 'Kevin Kruse'},
    { text: 'Whatever the mind of man can conceive and believe, it can achieve', author: 'Napoleon Hill'},
    { text: 'Strive not to be a success, but rather to be of value.', author: 'Albert Einstein'},
    { text: 'Two roads diverged in a wood, and I took the one less traveled by, And that has made all the difference.', author: 'Robert Frost'},
    { text: 'The most difficult thing is the decision to act, the rest is merely tenacity.', author: 'Amelia Earhart'},
    { text: 'Life is what happens to you while you\'re busy making other plans.', author: 'John Lennon'},
    { text: 'What even is a jQuery?', author: 'Tyler S. McGinnis'}
  ];
```

Notice we didn't put our quotes array directly on `this` or the object we're going to return. That's because we don't want this data to be directly accessed from outside of this service. Instead, we're going to create 'getter' and 'setter' methods in order to get, add to, or remove parts of the quotes array making the quotes array 'private' to this service.

* Now that we have our data, let's set up the methods to access that data.
* Create three methods on your `this` (service): one called `getData`, one called `addData`, and one called `removeData`
* `getData` simply returns the quotes array
* `addData` takes in a data object, verifies that data object has the proper keys (just text and author), then adds that object to the end of the quotes array
* `removeData` takes in the text of a quote, loops through the quotes array, then removes the matching quote from the array.

Once you finish those methods, this service should be complete. Notice how all the heavy logic is contained in this one service which we can inject into any controller we create. This makes things very modular and testable.

##Step 3: Add Data from your Service to your Controller and Display it
Now that your service is set up, let's inject your service in to your controller then add that data to the scope of your controller, then display it in your view
* Inject your dataService into your mainCtrl
* Use the proper method on your dataService object to get the quotes array then add it to your $scope object in your mainCtrl
* Once the quotes data is on your scope, use ng-repeat to loop over that data in  your index.html page and display it.

##Step 4: Add Options to Filter, Add, and Remove Items from your Quotes Array
* Create three buttons, "Add Quote," "Remove Quote," and "Filter Quotes."
* Using ng-click and the methods we set up on our dataService object earlier, make those three buttons do the appropriate action.
* Once you're finished, add some ng-shows to 'toggle' the input boxes for add, remove, and filter making sure you only show one at a time.

##Black Diamond: Persist your Quotes using your browser's local storage
* Store the quotes object in your browser's local storage.

You can do this with one of a few ways. You could use [`localStorage`](https://developer.mozilla.org/en-US/docs/Web/API/Window/localStorage), which you can learn more about at [MDN](https://developer.mozilla.org/en-US/docs/Web/API/Web_Storage_API/Using_the_Web_Storage_API). Recognize that values will need to be stored as a string, so you may need to convert your data to and from a string with [`JSON.stringify`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/JSON/stringify) and [`JSON.parse`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/JSON/parse).

Or, you could use Angular's [$cookie service](https://docs.angularjs.org/api/ngCookies/service/$cookies) to store your quotes object. Be mindful to use the documentation version that correlates with the correct Angular version you are using. Angular's $cookie has had some changes between different Angular versions.

## Contributions
If you see a problem or a typo, please fork, make the necessary changes, and create a pull request so we can review your changes and merge them into the master repo and branch.

## Copyright

© DevMountain LLC, 2015. Unauthorized use and/or duplication of this material without express and written permission from DevMountain, LLC is strictly prohibited. Excerpts and links may be used, provided that full and clear credit is given to DevMountain with appropriate and specific direction to the original content.

<img src="https://devmounta.in/img/logowhiteblue.png" width="250">
