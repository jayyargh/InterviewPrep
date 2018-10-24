# C# Fundamentals

This is the very first part of my C# section within the `InterviewPrep` repo. This first page is written for the beginner who has experience programming in a language other than C# but who requires a reminder of the basics of C# without too much detail. I suggest using this repo as a primer and then googling or using some other resource as a supplement to learn about the concepts I cover in here or to fill in the gaps between topics.

I will be numbering each markdown file to maintain a distinct understanding of the order. The first 8-10 files will cover the beginner topics such as primitive types/expressions, non-primitive types, control flow, arrays and lists, working with dates, text, files and finally, debugging your application. As these sections are added, I will be updating this first page to link to each specific topic so you can cover what you want as you need.

### C# vs .NET

- C# is a programming language
- .NET is a framework for building applications on Windows.

### .NET

- CLR (Common Language Runtime)
- Class Library

### CLR

Like Java which is compiled into Bytecode from Java to standardize operation on all machines, C# is converted into IL Code (Intermediate Language)

Write code on Windows:

- C/C++: `pCmdUI->Enable(m_clock.GetInterfacePtr() != NULL)`

- IL Code: `.entrypoint .maxstack 1 L_0000: nop L_0001: ldc.i4.s 60`

This process is completed by JIT (Just-in-time Compilation):

- Native Code: `00 2D 31 00 2E 29 73 00 61 6D 2E 67 61 A0 40 65 6C 2D 47 43 3A 63 00 A0`

### Architecture of .NET Applications

- Applications consist of building blocks called "classes".

- What is a class? A class is a container that holds data(attributes) and methods (functions). For example:

  - Think of a `Car` class. The data would be the `Make`, `Model`, and the `Color`. While the methods would look something like `Start()` or `Move()`.

- As an Application grows however, we begin to organize our classes using a container called a `Namespace`.

- On the topic of partitioning our Application, we organize our Namespaces in `Assembly`, which is a file on the disk, and can either be a `.dll` or a `.exe`.

### Get Coding With C# in Visual Studio

- First, create a new Project and use C#'s "Console App" template to scaffold your project. Give it a name, I'll be using `HelloWorld`. This will now create your C# console application, `HelloWorld`.

- Next, let's open the Solution Explorer (`ctrl + alt + L` or `view -> Solution Explorer`) if it's not already opened within your IDE. This will open a panel that displays your solution (`HelloWorld`) and its structure.

  - Go to `Properties` -> and click on `AssemblyInfo.cs`. This is the identification, or Assembly that is produced by this application. When you compile the console application, you will get an executable. Inside this file you'll see its attribute values, such as `AssemblyTitle`, `AssemblyDescription`, `AssemblyConfiguration`, etc. This is all part of Assembly Identification or Assembly Manifest. (This information is important when you plan to distribute the assembly)

  - Moving along, underneath `References`, you'll see all of the references to Assemblies that you'll be using classes inside of. The scaffold automatically pulls them all in.

  - Further down, you have `App.config` which is an XML file that you can use to store connection strings or application settings within.

  - Finally, you should see `Program.cs` which is where we will be writing our code. Clicking this will take you to your `Program` class within the editor. You should see that this class is within a container called a `Namespace` which will either be `HelloWorld` or whatever else you may have named the project.

    - You can reference classes within other namespaces as well by importing them through the `using` statement syntax. You'll see above your namespace that we're using the `System` namespace which is where our utility classes and primitive types are.

      - The next, `System.Collections.Generic` holds lists and collections.
      - `System.Linq` provides classes and interfaces that support queries that use Language-Integrated Query (LINQ).
      - `System.Text` contains classes used for character encoding and string manipulation.
      - Finally you have `System.Threading.Tasks` which provides us the ability to simplify the work of writing concurrent and asynchronous code.

    - This first `HelloWorld` application will not be using the latter four and we'll only need `System`. We'll leave them alone for now but eventually I will show you how to clean them up.

    - Inside of our namespace, by default, we have a `Program` class and inside of that we have our entry point of the application, the method `Main` that is executed by CLR at compile time. You will see that this method is declared as static and its parameter is called `args` and it is of type `string`. Before the name of the method is the return type, which in this case is `void`. This means our method does not return anything. Remember that the method is case sensitive as well, and `Main` must be capitalized. Let's begin writing our first C# program within the brackets in `Main`.

```C#
          static void Main(string[] args)
        {
            Console.WriteLine("Hello World");

            Console.ReadLine();
        }
```

- Update your `Main` function to reflect this code. You should see that in your `using` statements, the top one, `System` is brighter and no longer grayed out. This is because `Console` is a part of `System` and you're using it. The other `using` statements are still grayed out though, so let's just get rid of them. You can do this by highlighting and deleting them manually, or simply by clicking within the line of one, pressing `alt + enter` and selecting `Remove unnecessary usings`. Shortcuts are fun!

- Press `ctrl + f5` now to run your code and a black screen will apear with the text: `Hello World`. Now you see why this project is called a console application. Congrats, you just completed your first C# console application!

> - Think you're ready to move on? Try to answer these three questions:

> - What is a namespace?
>   - A type that contains code for the program
>   - A container for classes
>   - A deployable unit of application

> - What is JIT Compilation?
>   - The compilation of IL code to native machine code at run-time
>   - The compilation of C# code to native code
>   - The compilation of C# to IL code

> - What is an Assembly?
>   - A piece of code that is executable by CLR
>   - Container of one or more classes
>   - A single unit of deployment of .NET applications
