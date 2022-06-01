## How to: Write text to exist file

The following classes and methods are typically used to write text to a file:

```StreamWriter``` contains methods to write to a file synchronously (Write and WriteLine) or asynchronously (```WriteAsync``` and ```WriteLineAsync```).

```File``` provides static methods to write text to a file, such as ```WriteAllLines``` and ```WriteAllText```, or to append text to a file, such as ```AppendAllLines```, ```AppendAllText```, and ```AppendText```.

```Path``` is for strings that have file or directory path information. It contains the ```Combine``` method and, in .NET Core 2.1 and later, the ```Join``` and ```TryJoin``` methods, which allow concatenation of strings to build a file or directory path.


### Example

- The following example shows how to use the ```StreamWriter``` class to synchronously write text to a new file one line at a time. Because the ```StreamWriter``` object is declared and instantiated in a using statement, the ```Dispose``` method is invoked, which automatically flushes and closes the stream.

- The example creates a file named "WriteLines.txt" with the following contents:
First line
Second line
Third line

```c#
using System;
using System.IO;

class Program
{
    static void Main(string[] args)
    {

        // Create a string array with the lines of text
        string[] lines = { "First line", "Second line", "Third line" };

        // Set a variable to the Documents path.
        string docPath =
          Environment.GetFolderPath(Environment.SpecialFolder.MyDocuments);

        // Write the string array to a new file named "WriteLines.txt".
        using (StreamWriter outputFile = new StreamWriter(Path.Combine(docPath, "WriteLines.txt")))
        {
            foreach (string line in lines)
                outputFile.WriteLine(line);
        }
    }
}
```

***

[Reference](https://docs.microsoft.com/en-us/dotnet/standard/io/how-to-write-text-to-a-file)
