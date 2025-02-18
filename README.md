[![Build Status](https://github.com/mpalourdio/SpringBootAngularHTML5/workflows/back/badge.svg?branch=master)](https://github.com/mpalourdio/SpringBootAngularHTML5/actions)
[![Build Status](https://github.com/mpalourdio/SpringBootAngularHTML5/workflows/front/badge.svg?branch=master)](https://github.com/mpalourdio/SpringBootAngularHTML5/actions)

NB: Older Spring Boot and Angular versions are available in [branches](https://github.com/mpalourdio/SpringBootAngularHTML5/branches).  
This project is available in **Kotlin** too. Take a look at [this repository](https://github.com/mpalourdio/SpringBootKotlinAngular).

Spring Boot 2.x and Angular 12.x with HTML 5 router -test
====================================================

This project provides an example of an Angular single page application, served by ``Tomcat``,
configured with the ``html5 router``. Some endpoints have Spring Webflux integration too.

The [SinglePageAppConfig](src/main/java/com/mpalourdio/html5/config/SinglePageAppConfig.java) makes the magic here.

The ``base-href`` in configured by the ResourceResolver. It's generated from the value of the application's [context-path](src/main/resources/application.properties#L11) at runtime when served by tomcat.

It's useful if you want to serve an Angular application with the ``html5 router``, and avoid the dashed URL.

This ``html5 router`` mode makes pretty URL, but has a default : Refreshing pages (or accessing them directly) will give you a 404
HTTP error if no RewriteRule is provided by the HTTP server that serves the application.

Handling the ``base-href`` dynamically can be tricky too. Here it's done once and for all by the ResourceResolver.

This project includes a custom [HTTP interceptor](https://github.com/mpalourdio/ng-http-loader). It's useful to show a [loader](https://github.com/tobiasahlin/SpinKit) during long HTTP requests for example.

To test the fully built project, run [SpringBootAngularHTML5Application](src/main/java/com/mpalourdio/html5/SpringBootAngularHTML5Application.java) after an ``./mvnw clean install -Pfront``, and point your browser to [http://localhost:10000/my-context/path](http://localhost:10000/my-context/path).

If you want to play with the front part, go to the [front folder](front) and run ``yarn start`` or ``npm start``. HTTP requests will be correctly proxyfied to your backend.

The front-end part has been scaffolded with [angular-cli](https://github.com/angular/angular-cli).
