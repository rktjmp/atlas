Atlas
=====

Atlas is a naive AngularJS service that allows you to access your application routes
by a given name and inject any url parameters.

Usage
-----

In your routes, you have to define a the route name by adding the key "atlasName",
as shown below:

    $routeProvider.when('/my-albums/:album/:photoid/comments, {
      atlasName: "album-photo-comments",
      controller: 'AlbumController',
    }).when("/home", {
      atlasName: "home",
      controller: "HomeController"
    })

In your main app definition, add Atlas as a dependency:

    window.app = angular.module('myApp', [Atlas']).config(...)

Now in your controllers you can use use Atlas like so:

Go to a route with no parameters:

    $scope.goHome = () -> Atlas.goto('home')

Go to a route with parameters, the object keys must match the route param keys:

    $scope.gotoAlbumPhotoComments = (album, photo) -> Atlas.goto('album-photo-comments', {
      album: album,
      photoid: photo 
    })
