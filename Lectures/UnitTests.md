# Creating Unit Tests for ASP.NET MVC Applications

Demonstrate how you can write unit tests for the controllers in your ASP.NET MVC applications.


### 1) Imagine that we want to test whether or not the ProductController returns the right view
```c#
using System.Web.Mvc;
using Microsoft.VisualStudio.TestTools.UnitTesting;
using Store.Controllers;

namespace StoreTests.Controllers
{
     [TestClass]
     public class ProductControllerTest
     {
          [TestMethod]
          public void TestDetailsView()
          {
               var controller = new ProductController();
               var result = controller.Details(2) as ViewResult;
               Assert.AreEqual("Details", result.ViewName);

          }
     }
}
```

### 2) An MVC controller passes data to a view by using something called View Data.
#### imagine that you want to display the details for a particular product when you invoke the ProductController Details() action

#### The Controller
```c#
using System;
using System.Web.Mvc;

namespace Store.Controllers
{
     public class ProductController : Controller
     {
          public ActionResult Index()
          {
               // Add action logic here
               throw new NotImplementedException();
          }

          public ActionResult Details(int Id)
          {
               var product = new Product(Id, "Laptop");
               return View("Details", product);
          }
     }
}
```

### Testing 
```c#
using System.Web.Mvc;
using Microsoft.VisualStudio.TestTools.UnitTesting;
using Store.Controllers;

namespace StoreTests.Controllers
{
     [TestClass]
     public class ProductControllerTest
     {

          [TestMethod]
          public void TestDetailsViewData()
          {
               var controller = new ProductController();
               var result = controller.Details(2) as ViewResult;
               var product = (Product) result.ViewData.Model;
               Assert.AreEqual("Laptop", product.Name);
          }
     }
}
```

<br> 
---
<br>

# Unit tests of controller logic
Unit tests involve testing a part of an app in isolation from its infrastructure and dependencies. When unit testing controller logic, only the contents of a single action are tested, not the behavior of its dependencies or of the framework itself.
[Reference](https://docs.microsoft.com/en-us/aspnet/core/mvc/controllers/testing?view=aspnetcore-2.1)