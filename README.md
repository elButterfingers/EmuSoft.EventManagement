1.	First, add the "EventManagement.InputManager" namespace to your project using the "using" statement:<br />
<br />
<code>using EventManagement.InputManager.ClientManager; </code><br />
<br />
2.	Next, create a new instance of the "ClientProvider" class:<br />
<br />
<code>ClientProvider provider = new ClientProvider(); </code><br />
This will create a new instance of the "ClientProvider" class using the default error handling strategy.<br />
<br />
<br />
3.  Here is an example being used within a windows form app<br />
<br />
<code>


        private void Form1_Load(object sender, EventArgs e)
        {

            IClientProvider clientProvider = new ClientProvider();
            clientProvider.Mouse.OnMouse(e =>
            {
                //your code to run goes here!!! 
            });

        }
</code>
<br />
This can be usefull because typically you can only get event being driven from the form it self<br />
<code>


        private void Form1_Load(object sender, EventArgs e)
        {
            IClientProvider clientProvider = new ClientProvider();
            clientProvider.Mouse.OnMouse(e =>
            {
                //your code to run goes here!!! 
                this.Invoke((MethodInvoker)delegate
                {
                    this.Text = e.Window.Title;
                });

            });
        }
        
</code><br />
<br />

Not Working with Windows Forms. We can also use this within a Console Application. Basically anything really. as long as your running dot net 6.0 or above

<code>


    internal static class Program
    {
        static void Main()
        {
            IClientProvider clientProvider = new ClientProvider();
            clientProvider.Mouse.OnMouse(e =>
            {
                Console.WriteLine(e);

            });

            //keep the application alive
            while (true)
            {
                Thread.Sleep(1000);
            }
        }
    }
    
</code>
<br />
<br />
Later releases will be to allow this library to integrate with lower versions of the dot net framework.
