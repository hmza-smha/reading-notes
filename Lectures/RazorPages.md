# Razor Pages

### Razor Pages can make coding page-focused scenarios easier and more productive than using controllers and views.

- With Razor Pages, when you make a request ```(e.g. /contact)``` the default ASP.NET Routing configuration will attempt to locate a Razor Page for that request in the Pages folder.

- It simply looks for a page with the name used in the request (for a request to ```/contact``` that would be ```Contact.cshtml```) and routes directly to it.

- The Razor Page then acts as though it were a controller action.

- For a ```.cshtml``` file to qualify as a Razor Page, it must live in the Pages folder (using default conventions) and include ```@page``` in its markup.

- Every Razor Page can have a corresponding Page Model.

- If we stick to the default conventions, ASP.NET will expect that model to have the same name as the corresponding Razor page but with a ```.cs``` appended.
    - With Razor Pages your application code lives in these models, specifically in methods for the different HTTP verbs (e.g. GET, POST).

- Because the request was routed directly to the specific razor page that can handle it, there’s no need to go off locating a view, the view is the one the request was routed to e.g. ```1Contact.cshtml```.

- The default routing for Razor Pages is simple enough and respects subfolders, so ```\Pages\Staff\Profile.cshtml``` would be accessible via a request to ```/staff/profile```.

    - index.cshtml
    - index.cshtml.cs


## Create a Razor Pages project

1. in ```Program.cs```

- var builder = WebApplication.CreateBuilder(args); builder.Services.AddRazorPages();
- app.MapRazorPages(); // adds endpoints for Razor Pages to the IEndpointRouteBuilder.

2. Consider a basic page:

```c#
@page

<h1>Hello, world!</h1>
<h2>The time on the server is @DateTime.Now</h2>
```

What makes it different is the @page directive. @page makes the file into an MVC action, which means that it handles requests directly, without going through a controller. @page must be the first Razor directive on a page. @page affects the behavior of other Razor constructs. Razor Pages file names have a .cshtml suffix.

3. Create The ```Pages/Index2.cshtml.cs``` page model:

```c#
using Microsoft.AspNetCore.Mvc.RazorPages;
using Microsoft.Extensions.Logging;
using System;

namespace RazorPagesIntro.Pages
{
    public class Index2Model : PageModel
    {
        public string Message { get; private set; } = "PageModel in C#";

        public void OnGet()
        {
            Message += $" Server time is { DateTime.Now }";
        }
    }
}   
```
By convention, the PageModel class file has the same name as the Razor Page file with .cs appended. For example, the previous Razor Page is Pages/Index2.cshtml. The file containing the PageModel class is named Pages/Index2.cshtml.cs.

4. Hit ```~/Index2```

#### Notes:

- The runtime looks for Razor Pages files in the Pages folder by default.
- Index is the default page when a URL doesn't include a page.

