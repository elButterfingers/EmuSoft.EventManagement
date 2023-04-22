nuget package installer<br />
<code>dotnet add package EmuSoft.EventManagement --version 1.0.1</code>

Basic Usage Example.

<code>IClientProvider clientProvider = new ClientProvider();
clientProvider.Mouse.OnMouse(e =>
{
    // write a line of text to the file
    File.AppendAllText("date.txt", e.Window.ToString() + "\r\n");

});
</code>

