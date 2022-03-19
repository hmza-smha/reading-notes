[Reference](https://docs.microsoft.com/en-us/dotnet/standard/io/) <br>

[How to: Write text to a file](./WriteTextToFile.md) <br>

[How to: Create file](./CreateFile.md) <br>

# File and Stream I/O
File and stream I/O (input/output) refers to the transfer of data either to or from a storage medium.

In **.NET**, the ```System.IO``` namespaces contain types that enable reading and writing, both synchronously and asynchronously, on data streams and files.

<br>

## File VS Stream

A **file** is an ordered and named collection of bytes that has persistent storage. When you work with files, you work with directory paths, disk storage, and file and directory names.

A **stream** is a sequence of bytes that you can use to read from and write to a backing store, which can be one of several storage mediums (for example, disks or memory). Just as there are several backing stores other than disks, there are several kinds of streams other than file streams, such as network, memory, and pipe streams.

<br>

## Files and directories
You can use the types in the System.IO namespace to interact with files and directories.

Here are some commonly used file and directory classes:

```File``` - provides static methods for creating, copying, deleting, moving, and opening files, and helps create a ```FileStream``` object.

```FileInfo``` - provides instance methods for creating, copying, deleting, moving, and opening files, and helps create a FileStream object.

```Directory``` - provides static methods for creating, moving, and enumerating through directories and subdirectories.

```DirectoryInfo``` - provides instance methods for creating, moving, and enumerating through directories and subdirectories.

```Path``` - provides methods and properties for processing directory strings in a cross-platform manner.

> You should always provide robust exception handling when calling filesystem methods.see [Handling I/O errors.](https://docs.microsoft.com/en-us/dotnet/standard/io/handling-io-errors)

<br>

## Streams
The abstract base class ```Stream``` supports reading and writing bytes. All classes that represent streams inherit from the ```Stream``` class. The ```Stream``` class and its derived classes provide a common view of data sources and repositories, and isolate the programmer from the specific details of the operating system and underlying devices.

Streams involve three fundamental operations:

**Reading** - transferring data from a stream into a data structure, such as an array of bytes.

**Writing** - transferring data to a stream from a data source.

**Seeking** - querying and modifying the current position within a stream.

Here are some commonly used stream classes:

```FileStream``` – for reading and writing to a file.

```IsolatedStorageFileStream``` – for reading and writing to a file in isolated storage.

```MemoryStream``` – for reading and writing to memory as the backing store.

```BufferedStream``` – for improving performance of read and write operations.

```NetworkStream``` – for reading and writing over network sockets.

```PipeStream``` – for reading and writing over anonymous and named pipes.

```CryptoStream``` – for linking data streams to cryptographic transformations.

For an example of working with streams asynchronously, see [Asynchronous File I/O](https://docs.microsoft.com/en-us/dotnet/standard/io/asynchronous-file-i-o).

<br>

## Readers and writers
The ``System.IO`` namespace also provides types for reading encoded characters from streams and writing them to streams. Typically, streams are designed for byte input and output. The reader and writer types handle the conversion of the encoded characters to and from bytes so the stream can complete the operation. Each reader and writer class is associated with a stream, which can be retrieved through the class's ```BaseStream``` property.

Here are some commonly used reader and writer classes:

```BinaryReader``` and ```BinaryWriter``` – for reading and writing primitive data types as binary values.

```StreamReader``` and ```StreamWriter``` – for reading and writing characters by using an encoding value to convert the characters to and from bytes.

```StringReader``` and ```StringWriter``` – for reading and writing characters to and from strings.

```TextReader``` and ```TextWriter``` – serve as the abstract base classes for other readers and writers that read and write characters and strings, but not binary data.

<br>

## Asynchronous I/O operations
Reading or writing a large amount of data can be resource-intensive. You should perform these tasks asynchronously if your application needs to remain responsive to the user. With synchronous I/O operations, the UI thread is blocked until the resource-intensive operation has completed.

For more information, see [Asynchronous File I/O](https://docs.microsoft.com/en-us/dotnet/standard/io/asynchronous-file-i-o).

<br>

## Compression
Compression refers to the process of reducing the size of a file for storage. Decompression is the process of extracting the contents of a compressed file so they are in a usable format. The [System.IO.Compression](https://docs.microsoft.com/en-us/dotnet/api/system.io.compression?view=net-6.0) namespace contains types for compressing and decompressing files and streams.