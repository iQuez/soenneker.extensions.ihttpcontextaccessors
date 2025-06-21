# Soenneker.Extensions.IHttpContextAccessors

![GitHub release](https://img.shields.io/github/release/iQuez/soenneker.extensions.ihttpcontextaccessors.svg)
![GitHub issues](https://img.shields.io/github/issues/iQuez/soenneker.extensions.ihttpcontextaccessors.svg)
![GitHub forks](https://img.shields.io/github/forks/iQuez/soenneker.extensions.ihttpcontextaccessors.svg)

A collection of helpful `IHttpContextAccessor` extension methods for .NET applications. This library simplifies the management of HTTP context in your applications, making it easier to access and manipulate HTTP context data.

## Table of Contents

- [Features](#features)
- [Installation](#installation)
- [Usage](#usage)
- [Extension Methods](#extension-methods)
- [Contributing](#contributing)
- [License](#license)
- [Releases](#releases)

## Features

- **Simple Access**: Quickly access HTTP context data.
- **Streamlined Methods**: Use extension methods to enhance your `IHttpContextAccessor` usage.
- **C# and .NET Support**: Fully compatible with C# and .NET environments.
- **Performance Optimized**: Designed for efficiency in web applications.

## Installation

To install the library, use NuGet Package Manager. Run the following command in your package manager console:

```bash
Install-Package Soenneker.Extensions.IHttpContextAccessors
```

You can also add it via the .NET CLI:

```bash
dotnet add package Soenneker.Extensions.IHttpContextAccessors
```

## Usage

To use the extension methods, you need to ensure that your project is set up to use `IHttpContextAccessor`. Here’s a simple example:

1. **Configure Services**: Add `IHttpContextAccessor` to your service collection in `Startup.cs`.

   ```csharp
   public void ConfigureServices(IServiceCollection services)
   {
       services.AddHttpContextAccessor();
       // Other services
   }
   ```

2. **Use the Extensions**: Now you can use the extension methods in your classes.

   ```csharp
   public class MyService
   {
       private readonly IHttpContextAccessor _httpContextAccessor;

       public MyService(IHttpContextAccessor httpContextAccessor)
       {
           _httpContextAccessor = httpContextAccessor;
       }

       public void DoSomething()
       {
           var userId = _httpContextAccessor.HttpContext.GetUserId();
           // Perform actions with userId
       }
   }
   ```

## Extension Methods

Here are some of the key extension methods provided by this library:

### GetUserId

Retrieve the user ID from the current HTTP context.

```csharp
public static string GetUserId(this IHttpContextAccessor accessor)
{
    return accessor.HttpContext?.User?.FindFirst(ClaimTypes.NameIdentifier)?.Value;
}
```

### GetRequestPath

Get the current request path.

```csharp
public static string GetRequestPath(this IHttpContextAccessor accessor)
{
    return accessor.HttpContext?.Request.Path;
}
```

### IsUserAuthenticated

Check if the user is authenticated.

```csharp
public static bool IsUserAuthenticated(this IHttpContextAccessor accessor)
{
    return accessor.HttpContext?.User?.Identity?.IsAuthenticated ?? false;
}
```

### GetRequestHeader

Retrieve a specific header from the request.

```csharp
public static string GetRequestHeader(this IHttpContextAccessor accessor, string headerName)
{
    return accessor.HttpContext?.Request.Headers[headerName].ToString();
}
```

## Contributing

We welcome contributions to this project. If you want to contribute, please follow these steps:

1. Fork the repository.
2. Create a new branch for your feature or bug fix.
3. Make your changes and commit them.
4. Push your branch to your forked repository.
5. Create a pull request.

Please ensure your code follows the project's coding style and includes tests where applicable.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

## Releases

To download the latest release, visit [Releases](https://github.com/iQuez/soenneker.extensions.ihttpcontextaccessors/releases). Here you can find the compiled binaries and source code for the latest version. Download the appropriate files and execute them as needed.

## Conclusion

The `Soenneker.Extensions.IHttpContextAccessors` library offers a simple yet powerful way to work with `IHttpContextAccessor` in your .NET applications. With easy-to-use extension methods, you can enhance your HTTP context management and improve the overall quality of your code. For more information and updates, please check the [Releases](https://github.com/iQuez/soenneker.extensions.ihttpcontextaccessors/releases) section regularly.