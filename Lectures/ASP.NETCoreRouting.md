# ASP.NET Core Routing

Routing is responsible for matching incoming HTTP requests and dispatching those requests to the app's executable endpoints. Endpoints are the app's units of executable request-handling code. Endpoints are defined in the app and configured when the app starts. The endpoint matching process can extract values from the request's URL and provide those values for request processing. Using endpoint information from the app, routing is also able to generate URLs that map to endpoints. 

## Routing basics
All ASP.NET Core templates include routing in the generated code. Routing is registered in the middleware pipeline in Startup.Configure.

### Routing uses a pair of middleware, registered by UseRouting and UseEndpoints:

- UseRouting adds route matching to the middleware pipeline. This middleware looks at the set of endpoints defined in the app, and selects the best match based on the request.
- UseEndpoints adds endpoint execution to the middleware pipeline. It runs the delegate associated with the selected endpoint.

The preceding example includes a single route to code endpoint using the MapGet method:

- When an HTTP GET request is sent to the root URL /:
    - The request delegate shown executes.
    - Hello World! is written to the HTTP response. By default, the root URL / is https://localhost:5001/
- If the request method is not GET or the root URL is not /, no route matches and an HTTP 404 is returned.


## Endpoint

The MapGet method is used to define an endpoint. An endpoint is something that can be:

Selected, by matching the URL and HTTP method.
Executed, by running the delegate.
Endpoints that can be matched and executed by the app are configured in UseEndpoints.