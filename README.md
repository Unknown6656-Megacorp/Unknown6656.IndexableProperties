[![](https://img.shields.io/github/downloads/Unknown6656-Megacorp/Unknown6656.IndexableProperties/total)](https://github.com/Unknown6656-Megacorp/Unknown6656.IndexableProperties/releases)
[![](https://img.shields.io/nuget/vpre/Unknown6656.IndexableProperties)](https://www.nuget.org/packages/Unknown6656.IndexableProperties/)
[![](https://img.shields.io/nuget/dt/Unknown6656.IndexableProperties)](https://www.nuget.org/packages/Unknown6656.IndexableProperties/)


# Unknown6656.IndexableProperties

This library aims to bring indexable properties to C#.<br/>


[TODO]


## Installation

Use one of the follwing methods to install and use this library:

- **Package Manager:**

    ```batch
    PM> Install-Package Unknown6656.IndexableProperties
    ```

- **.NET CLI:**

    ```batch
    > dotnet add package Unknown6656.IndexableProperties
    ```

- **Package reference** (e.g. in a `.csproj`/`.vbproj`/`.fsproj` project file):

    ```xml
    <PackageReference Include="Unknown6656.IndexableProperties" Version="*" />
    ```

- **Paket CLI:**

    ```batch
    > paket add Unknown6656.IndexableProperties
    ```

- **F# Interactive:**

    ```fsharp
    #r "nuget: Unknown6656.IndexableProperties, *"
    ```

## Documentation and Usage

To use the indexable properties, simply include the namespace `Unknown6656`:

```csharp
using Unknown6656;
```

The library defines the following indexer types:
 1. Readable/Writable indexers (`Unknown6656.Indexer<...>`)
 2. Read-only indexers (`Unknown6656.ReadOnlyIndexer<...>`)
 3. Write-only indexers (`Unknown6656.WriteOnlyIndexer<...>`)
 4. By-reference indexers (`Unknown6656.RedIndexer<...>`)

Each indexer defines a set of index types (`Index1` through `IndexN`) and a input/return value type (`Value`).
An Indexer may be declared as follows:

```csharp
public class MyClass
{
    public Indexer<int, string> MyIndex { get; } = new(...);
}
```
The code sample above declares a 1-dimensional indexer which takes an `int` as its only index and accepts/returns a `string`-value.


[TODO]


### Code samples

```csharp
public class MyClass
{
    public Indexer<int, double> Items { get; }
    public Indexer<int, double> SquaredItems { get; }


    public MyClass(double[] array)
    {
        Items = new(
            index => array[index],
            (index, value) => array[index] = value
        );
        SquaredItems = new(
            index => array[index] * array[index],
            (index, value) => array[index] = Math.Sqrt(value)
        );
    }
}


MyClass c = new(new double [] { 1, 2, 3, 4, 5 });

double original = c.Items[3];
double squared = c.SquaredItems[3];

c.SquaredItems[3] = 42;

double newvalue = c.Items[3];

Console.WriteLine("original item at index 3:    " + original);
Console.WriteLine("original squared at index 3: " + squared);
Console.WriteLine("new item at index 3:         " + newvalue);
```

[TODO]
