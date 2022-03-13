
# Exceptopn Handling
The Exception Handling is one of the powerful mechanism to handle the runtime errors so that the normal flow of the application can be maintained.

# try/catch block
Place any code statements that might raise or throw an exception in a ```try``` block, and place statements used to handle the exception or exceptions in one or more ```catch``` blocks below the ```try``` block. Each ```catch``` block includes the ```exception``` type and can contain additional statements needed to handle that ```exception``` type.

>[Resource](https://docs.microsoft.com/en-us/dotnet/standard/exceptions/how-to-use-the-try-catch-block-to-catch-exceptions)

```c#
try{
    // write the code which possible throw an exception here
}
catch(Exceptopn e){
    // write the handle code here
    // note: you can use as many as catchs you want
}
finally {
    // write your final code here
}
```
> First try block try to handle it if not then catch block will handle it. Finally block will executed regardless of the outcome


# Debugging
Debugging is the process of finding errors during application execution. It does not mean syntax errors, with which the application cannot be compiled, but on logic errors. Logic errors can only be noticed during application execution.