# Authentication with ASP.NET Core

#### First of all, we should clarify the difference between these two dependent facets of security. The simple answer is that Authentication is the process of determining **who you are**, while Authorisation revolves around **what you are allowed to do**, i.e. permissions.

# Claims-based authentication
#### You can think of claims as being a statement about, or a property of, a particular identity. That statement consists of a name and a value. For example you could have a ```DateOfBirth``` claim, ```FirstName claim```, ```EmailAddress``` claim or ```IsVIP``` claim. Note that these statements are about what or who the identity ***is***, not what they can **do**.


For example, you may have a driver's license, issued by a local driving license authority. Your driver's license has your date of birth on it. In this case the claim name would be DateOfBirth, the claim value would be your date of birth, for example 8th June 1970 and the issuer would be the driving license authority. Claims based authorization, at its simplest, checks the value of a claim and allows access to a resource based upon that value.

```c#
...

builder.Services.AddAuthorization(options =>
{
   options.AddPolicy("EmployeeOnly", policy => policy.RequireClaim("EmployeeNumber"));
});

...

app.UseAuthorization();

```

In this case the EmployeeOnly policy checks for the presence of an EmployeeNumber claim on the current identity.

```c#
[Authorize(Policy = "EmployeeOnly")]
public IActionResult VacationBalance()
{
    return View();
}
```