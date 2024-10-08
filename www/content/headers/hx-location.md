+++
title = "HX-Location Response Header"
+++

This response header can be used to trigger a client side redirection without reloading the whole page. Instead of changing the page's location it will act like [`hx-boost`](@/attributes/hx-boost.md) on an anchor tag, creating a new history entry, issuing an ajax request to the value of the header and pushing the path into history.

A sample response would be:

```html
HX-Location: /test
```

Which would push the client to test as if the user had clicked on `<a href="/test" hx-boost="true">`

If you want to redirect to a specific target on the page rather than the default of document.body, you can pass more details along with the event, by using JSON for the value of the header:

```html
HX-Location: {"path":"/test2", "target":"#testdiv"}
```

If you would like the functionality act the way hx-boost works on forms, you can pass the `push` option.
The url will not be pushed, and no history entry will be created.

```html
HX-Location: {"path":"/test2", "target":"#testdiv", "push":false}
```

Path is required and is url to load the response from. The rest of the data mirrors the [`ajax` api](@/api.md#ajax) context, which is:

* `source` - the source element of the request
* `event` - an event that "triggered" the request
* `handler` - a callback that will handle the response HTML
* `target` - the target to swap the response into
* `swap` - how the response will be swapped in relative to the target
* `values` - values to submit with the request
* `headers` - headers to submit with the request
* `select` - allows you to select the content you want swapped from a response

## Notes

Response headers are not processed on 3xx response codes. see [Response Headers](@/docs.md#response-headers)
