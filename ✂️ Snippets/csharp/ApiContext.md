## ApiContext
#csharp

```c#
using System.Net.Http.Headers;

namespace <Project>.System.Web

{
    /// <summary>
    /// Singleton ApiContext and requests
    /// </summary>

    internal sealed class ApiContext
    {
        private static ApiContext? instance = null;
        public static HttpClient httpClient = new();
        private static readonly object padlock = new();

        ApiContext()
        {
            httpClient.BaseAddress = new Uri("<api_base_url");
            httpClient.DefaultRequestHeaders.Accept.Clear();
            httpClient.DefaultRequestHeaders.Accept.Add(
                new MediaTypeWithQualityHeaderValue("application/json"));
        }

        public static ApiContext Instance
        {
            get
            {
                lock (padlock)
                {
                    if (instance == null)
                    {
                        instance = new ApiContext();
                    }
                    return instance;
                }
            }
        }

        // Add API requests as needed
        public async Task<HttpResponseMessage> ExamplePostAsync(Form f)
        {
            HttpResponseMessage response = await httpClient.PostAsJsonAsync("Account/Register", f);
            return response;
        }
    }
}
```

## Usage
```c#
using <project>.System.Web;

namespace <project>.Controllers
{
	public class ExampleController : Controller
	{
        private static readonly ApiContext Api = ApiContext.Instance;

        [HttpPost]
        public async Task<IActionResult> Register(ExampleViewModel viewModel)
        {
            HttpResponseMessage response = await Api.ExamplePostAsync(viewModel.Form);
           
           // ...
        }
	}
}
```