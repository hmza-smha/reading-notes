# JSON in c#

## JavaScript Object Notaion

### The power of JSON is we can convert objects to strings and vise versa.

#### Exapmle 

```json
{
    name:"dog1",
    age:"3"
}
```
This JSON can be represented in c# like this 
```c#
class Dog{
    public string Name {get; set;}
    public string Age {get; set;}
}

// for best practice 
class Dog{
    [JsonProperty("name")]
    public string Name {get; set;}
    [JsonProperty("age")]
    public string Age {get; set;}
}
```

> Use always [json2csharp](https://json2csharp.com/) to create json classes.

> Use always [codebeautify](https://codebeautify.org/) to beautify code.

### Reading JSON files
#### Read About **newtonjson** library in c#
