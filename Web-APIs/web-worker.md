##### Web Worker
___
###### At the end of this module you will be able to learn about web worker i.e. Dedicated, Shared and Service web workers.

##### What is a web worker
Web Workers makes it possible to run a script operation in a background thread separate from the main execution thread of a web application.
Workers run in another global context that is different from the current window. Data is sent between workers and the main thread via a system of messages — both sides send their messages using the postMessage() method, and respond to messages via the onmessage event handler (the message is contained within the Message event's data property). The data is copied rather than shared.
___

##### Advantages
- You can run whatever code you like inside the worker thread. 
- You can use a large number of items available under window, including WebSockets, and data storage mechanisms like IndexedDB.

___
##### Limitations 
- You can't directly manipulate the DOM from inside a worker, or use some default methods and properties of the window object.
___

##### Types of Worker
- **Dedicated Workers** are workers that can be utilized by a single script. See [DedicatedWorker](https://github.com/mdn/simple-web-worker) example.
- **Shared Workers** are workers that can be utilized by multiple scripts running in different windows, IFrames, etc., as long as they are in the same domain as the worker. They are a little more complex than dedicated workers — scripts must communicate via an active port. See [SharedWorker](https://github.com/mdn/simple-shared-worker) Example.
- **ServiceWorkers** essentially act as proxy servers that sit between web applications, the browser, and the network (when available). They are intended, among other things, to enable the creation of effective offline experiences, intercept network requests and take appropriate action based on whether the network is available, and update assets residing on the server. They will also allow access to push notifications and background sync APIs. [More Details](https://developer.mozilla.org/en-US/docs/Web/API/Service_Worker_API/Using_Service_Workers)
