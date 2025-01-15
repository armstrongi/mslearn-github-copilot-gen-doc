# Parallel Asynchronous Example

This project is a WPF (Windows Presentation Foundation) application designed to demonstrate parallel asynchronous programming in C#. The application downloads content from multiple URLs in parallel and displays the results in a text box. The primary goal is to showcase how to perform asynchronous operations efficiently while maintaining a responsive user interface.

## Features

- **Parallel Asynchronous Downloads**: Perform parallel downloads of content from a predefined list of URLs using asynchronous programming techniques (`async` and `await`).
- **Responsive UI**: Maintain a responsive user interface during the download process using the `Dispatcher` to update the UI from background threads.
- **Error Handling**: Robust error handling to manage exceptions that may occur during the download process, with error messages displayed in the results text box.
- **User Feedback**: Display the size of the downloaded content, total bytes returned, and elapsed time in the results text box.

## Project Structure

The project consists of the following key files:

- **[APL2007M2Sample1.csproj](APL2007M2Sample1.csproj)**: Project configuration file.
- **[App.xaml](App.xaml)**: Application definition file.
- **[App.xaml.cs](App.xaml.cs)**: Code-behind for `App.xaml`.
- **[MainWindow.xaml](MainWindow.xaml)**: Main window definition.
- **[MainWindow.xaml.cs](MainWindow.xaml.cs)**: Code-behind for `MainWindow.xaml`.

## Key Components

1. **MainWindow.xaml**:
   - Defines the user interface of the main window, including a `Button` (`_startButton`) to start the asynchronous process and a `TextBox` (`_resultsTextBox`) to display the results.

2. **MainWindow.xaml.cs**:
   - Contains the code-behind logic for the main window.
   - Defines the `MainWindow` class, which inherits from `Window`.
   - Initializes an `HttpClient` instance for making web requests.
   - Defines a list of URLs (`_urlList`) to be processed.
   - Handles the button click event to start the asynchronous process.
   - Implements asynchronous methods for downloading content and updating the UI.

## Asynchronous Methods

- **`OnStartButtonClick`**:
  - Handles the click event of the `_startButton`. Disables the button, clears the `_resultsTextBox`, and starts the asynchronous process by calling `StartSumPageSizesAsync`.

- **`StartSumPageSizesAsync`**:
  - Initiates the process of summing page sizes by calling `SumPageSizesAsync`. Once the operation is complete, it updates the UI to re-enable the `_startButton` and display a message indicating that control has returned to the `OnStartButtonClick` method.

- **`SumPageSizesAsync`**:
  - Performs the main task of downloading content from multiple URLs in parallel. Uses LINQ to create a collection of tasks, each representing an asynchronous download operation. The tasks are awaited using `Task.WhenAll`, and the total size of the downloaded content is calculated and displayed in the `_resultsTextBox`.

- **`ProcessUrlAsync`**:
  - Handles the download of content from a single URL. Includes exception handling to manage errors during the download process. If an error occurs, an appropriate message is displayed in the `_resultsTextBox`, and the method returns `0` to indicate failure.

- **`DisplayResultsAsync`**:
  - Updates the `_resultsTextBox` with the results of each URL download. Called from `ProcessUrlAsync` to display the size of the downloaded content.

## Deployment

To deploy the application, build it in `Release` configuration, publish the application and its dependencies, and distribute the deployment package to target machines. Ensure that the target machines have the .NET 6.0 runtime installed and are running a compatible version of Windows.

## Requirements

- **.NET 6.0 SDK**: Ensure that the .NET 6.0 SDK is installed on your development machine. You can download it from the [.NET download page](https://dotnet.microsoft.com/download/dotnet/6.0).
- **Visual Studio 2022 or Visual Studio Code**: For development, you can use Visual Studio 2022 or Visual Studio Code. Both IDEs support .NET 6.0 and WPF development.
- **NuGet Package Manager**: The project uses NuGet for managing dependencies. Ensure that the NuGet package manager is configured in your development environment.

## Building and Running the Project

1. **Clone the Repository**:
   - Clone the project repository to your local machine.

2. **Open the Project**:
   - Open the project in Visual Studio 2022 or Visual Studio Code.

3. **Restore NuGet Packages**:
   - Restore the NuGet packages by running the following command in the terminal:
     ```sh
     dotnet restore
     ```

4. **Build the Project**:
   - Build the project by running the following command in the terminal:
     ```sh
     dotnet build
     ```

5. **Run the Application**:
   - Run the application by pressing `F5` in Visual Studio or by running the following command in the terminal:
     ```sh
     dotnet run
     ```

## Summary

This WPF application demonstrates how to perform parallel asynchronous operations efficiently while maintaining a responsive user interface. The project showcases key features such as parallel downloads, error handling, and user feedback, making it a valuable example for learning and implementing asynchronous programming in C#.