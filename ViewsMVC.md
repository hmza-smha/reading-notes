# Views in ASP.NET Core MVC

In the Model-View-Controller (MVC) pattern, the view handles the app's data presentation and user interaction. A view is an HTML template with embedded Razor markup. Razor markup is code that interacts with HTML markup to produce a webpage that's sent to the client.

In ASP.NET Core MVC, views are .cshtml files that use the C# programming language in Razor markup. Usually, view files are grouped into folders named for each of the app's controllers. The folders are stored in a Views folder at the root of the app.

## Benefits of using views

Views help to establish separation of concerns within an MVC app by separating the user interface markup from other parts of the app. 

- The app is easier to maintain because it's better organized.
- The parts of the app are loosely coupled. You can build and update the app's views separately from the business logic and data access components.
- It's easier to test the user interface parts of the app because the views are separate units.
- It's easier to test the user interface parts of the app because the views are separate units.

## Pass data to views
Pass data to views using several approaches:

- Strongly typed data: viewmodel
- Weakly typed data
- ViewData (ViewDataAttribute)
- ViewBag

### Strongly typed data: viewmodel
The most robust approach is to specify a model type in the view. This model is commonly referred to as a viewmodel. You pass an instance of the viewmodel type to the view from the action.

### ViewData
ViewData is a ViewDataDictionary object accessed through string keys. String data can be stored and used directly without the need for a cast, but you must cast other ViewData object values to specific types when you extract them. You can use ViewData to pass data from controllers to views and within views, including partial views and layouts.

### ViewBag
*ViewBag isn't available by default for use in Razor Pages PageModel classes.*

ViewBag is a Microsoft.AspNetCore.Mvc.ViewFeatures.Internal.DynamicViewData object that provides dynamic access to the objects stored in ViewData. ViewBag can be more convenient to work with, since it doesn't require casting

## Dynamic views
Views that don't declare a model type using @model but that have a model instance passed to them (for example, return View(Address);) can reference the instance's properties dynamically: