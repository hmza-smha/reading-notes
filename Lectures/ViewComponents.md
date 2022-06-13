# View Components

### View components are similar to partial views, but they're much more powerful. View components don't use model binding, they depend on the data passed when calling the view component.

- Renders a chunk rather than a whole response.
- Includes the same separation-of-concerns and testability benefits found between a controller and view.
- Can have parameters and business logic.
- Is typically invoked from a layout page.

A view component consists of two parts:

- The class, typically derived from ViewComponent
- The result it returns, typically a view.

## The view component class
A view component class can be created by any of the following:

- Deriving from ViewComponent
- Decorating a class with the ```[ViewComponent]``` attribute, or deriving from a class with the ```[ViewComponent]``` attribute
- Creating a class where the name ends with the suffix ```ViewComponent```
- Like controllers, view components must be public, non-nested, and non-abstract classes.

## Writing A Simple View Component 
[Reference](https://mariusschulz.com/blog/view-components-in-asp-net-core-mvc)

```c#
public class Navigation : ViewComponent
{

}
```

also add a special Invoke method that returns an IViewComponentResult to be rendered. Similar to MVC controllers, the Content helper method handed down from the ViewComponent base class accepts a string and simply returns its value:

```c#
public IViewComponentResult Invoke()
{
    return Content("Navigation");
}
```

Within our Razor views, we can use the Component helper and its Invoke method to render view components. The first argument (which is required) represents the name of the component, "Navigation" in our case. The remaining arguments (which are optional) represent parameters that our component's Invoke method might accept. In this case, we don't pass any further arguments because our Navigation component doesn't accept any:
```c#
@Component.Invoke("Navigation")
```
However, we're passing a magic string here. We can get more compile-time safety by replacing the hardcoded string literal with a nameof() expression that references our view component's class name:
```c#
@Component.Invoke(nameof(Navigation))
```

