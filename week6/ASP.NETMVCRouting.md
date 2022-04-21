# ASP.NET MVC Routing

## Routing module is responsible for mapping incoming browser requests to particular MVC controller actions

## The Default Route Table
When you create a new ASP.NET MVC application, the application is already configured to use ASP.NET Routing. ASP.NET Routing is setup in two places.

First, ASP.NET Routing is enabled in your application's Web configuration file (Web.config file). There are four sections in the configuration file that are relevant to routing:

Second, and more importantly, a route table is created in the application's Global.asax file. The Global.asax file is a special file that contains event handlers for ASP.NET application lifecycle events. The route table is created during the Application Start event.

### When an MVC application first starts, the Application_Start() method is called. This method, in turn, calls the RegisterRoutes() method. The RegisterRoutes() method creates the route table.

## Example
/Home/Index/3

The Default route maps this URL to the following parameters:

- controller = Home

- action = Index

- id = 3

When you request the URL /Home/Index/3, the following code is executed:

**HomeController.Index(3)**

The Default route includes defaults for all three parameters. If you don't supply a controller, then the controller parameter defaults to the value Home. If you don't supply an action, the action parameter defaults to the value Index. Finally, if you don't supply an id, the id parameter defaults to an empty string.