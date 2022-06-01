# Data Transfer Objects *(Re-Shape Object)*
### Senario:
The client receives data that maps directly to your database tables. However, that's not always a good idea. Sometimes you want to change the shape of the data that you send to client. For example, you might want to:

1. Remove circular references.
2. Hide particular properties that clients are not supposed to view
3. Omit some properties in order to reduce payload size.

...

### To accomplish this, you can define a data transfer object (DTO). A DTO is an object that defines how the data will be sent over the network.

```c#
public class BookDto
{
    public int Id { get; set; }
    public string Title { get; set; }
    public string AuthorName { get; set; }
}

public class BookDetailDto
{
    public int Id { get; set; }
    public string Title { get; set; }
    public int Year { get; set; }
    public decimal Price { get; set; }
    public string AuthorName { get; set; }
    public string Genre { get; set; }
}
```
Next, replace the two GET methods in the BooksController class, with versions that return DTOs. We'll use the LINQ Select statement to convert from Book entities into DTOs.