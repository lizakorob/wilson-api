# Wilson API - V3.0.0

Wilson is framework that adds a distinct component abstraction around Angularjs web applications. It provides
lazy-loading of javascript bundled based on url to component routing and decorates convenient base-functionality
onto each component that can be used to greatly enhance development experience and reduce boiler-plate code. 

This document provides details around the different concepts in Wilson and their distinctive interfaces. Sections
are broken up into different pages which contain more detailed documentation.

## Wilson Basics

When using Wilson, all Angularjs constructs are actually created via a Wilson declaration.

E.G.
```
wilson.component(<componentName>,   [..., function(...) { }]);
wilson.behavior(<componentName>,    [..., function(...) { }]);
wilson.service(<componentName>,     [..., function(...) { }]);
wilson.resource(<componentName>,    [..., function(...) { }]);
wilson.utility(<componentName>,     [..., function(...) { }]);
wilson.class(<componentName>,       [..., function(...) { }]);
wilson.filter(<componentName>,      [..., function(...) { }]);
```

Although this initial declaration is not specifically on the 'angular' global instance, under-the-hood, wilson
is creating these constructs (or the appropriate construct) on angular for these objects.  It is important to note
that the definitions inside of these method calls are in fact purely angular definitions and support all standard
angular functionality. There are a few conveniences added by Wilson, but there are no removals of angular concepts.

To go into a few more specifics, here are the relationships between what is declared on Wilson and what is created
on angular:

```
wilson.component() ---> angular.directive()
wilson.behavior()  ---> angular.directive()
  
wilson.service()   ---> angular.factory()
wilson.resource()  ---> angular.factory()
wilson.class()     ---> angular.factory()
wilson.utility()   ---> angular.factory()
  
wilson.filter()    ---> angular.filter()
```

Wilson ensures that some base options provided to angular so that these constructs are represented appropriately, but as
described above, Wilson is simply declaring these onto angular and also providing the support to accept new declarations
as lazily-loaded javascript content is added during navigation.


## Wilson Concepts


1. [Core Module]()
2. [Component Interface]()
3. [Routing]()
4. [Utility Functions]()