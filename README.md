# Window-Events-in-JavaScript

Short description or tagline of your project.

## Table of Contents

- [Frames and windows](#Frames-and-windows)
- [Cross-window Communication](#Cross-window Communication)
- [Contributing](#contributing)
- [License](#license)


## Frames-and-windows

Popups and window methods 
A popup window is one of the oldest methods to show the additional documents to the user. 
Popups exist from ancient times. The initial idea was to show another content without closing the main window. 
A popup is a separate window with its own independent JavaScript environment. So opening a popup with a third-party non-trusted site is safe. 
A popup can navigate (change URL) and send messages to the opener window. 

JavaScript has three kind of popup boxes: 
Alert box. 
Confirm box. 
Prompt box. 

Alert Box 
An alert box is often used if you want to make sure information comes through to the user. 
When an alert box pops up, the user will have to click "OK" to proceed. 
window.alert("sometext"); 

Confirm Box 
A confirm box is often used if you want the user to verify or accept something. 
When a confirm box pops up, the user will have to click either "OK" or "Cancel" to proceed. 
If the user clicks "OK", the box returns true. If the user clicks "Cancel", the box returns false. 
window.confirm("sometext"); 

Prompt Box 
A prompt box is often used if you want the user to input a value before entering a page. 
When a prompt box pops up, the user will have to click either "OK" or "Cancel" to proceed after entering an input value. 
If the user clicks "OK" the box returns the input value. If the user clicks "Cancel" the box returns null. 
window.prompt("sometext","defaultText"); 

Popup Blocking 
Most browsers block popups if they are called outside of user-triggered event handlers like onclick. 
For example: 
// popup blocked 
window.open('https://javascript.info'); 
// popup allowed 
button.onclick = () => { 
  window.open('https://javascript.info'); 
}; 
This way users are somewhat protected from unwanted popups, but the functionality is not disabled totally. 

window.open 
The open() method opens a new browser window, or a new tab, depending on your browser settings and the parameter values. 
The syntax to open a popup is: window.open(url, name, params): 

An URL to load into the new window. 
A name of the new window. Each window has a window.name, and here we can specify which window to use for the popup. 
The configuration string for the new window. It contains settings, delimited by a comma. There must be no spaces in params, for instance: width:200,height=100. 

A minimalistic Window 
1. Let’s open a window with minimal set of features just to see which of them browser allows to disable: 
let params = `scrollbars=no,resizable=no,status=no,location=no,toolbar=no,menubar=no, 
width=0,height=0,left=-1000,top=-1000`; 

open('/', 'test', params); 
Rules for omitted settings: 
If there is no 3rd argument in the open call, or it is empty, then the default window parameters are used. 
If there is a string of params, but some yes/no features are omitted, then the omitted features assumed to have no value. So if you specify params, make sure you explicitly set all required features to yes. 
If there is no left/top in params, then the browser tries to open a new window near the last opened window. 
If there is no width/height, then the new window will be the same size as the last opened. 

Accessing popup from window 
To access a popup from a window in JavaScript, you can use the window.open() method to open the popup. 
Steps: 
Open a New Window/Popup: You can open a new window or popup using the window.open() method. 
Access Elements in the Popup: Once you have a reference to the popup window, you can interact with it using JavaScript 
Communicate Between Parent and Popup: You can pass data between the parent window and the popup using methods like window.opener. 
Close the Popup: You can close the popup using the window.close() method. 

Accessing window from popup 
To access the parent window from a popup, you can use the window.opener property. This property allows the popup window to reference the window that opened it. Here's how you can do it: 
Accessing Parent Window Elements: In the popup window, you can access elements in the parent window  
Modifying Parent Window Elements: Once you have a reference to an element in the parent window, you can modify its properties or content. 
Calling Functions in Parent Window:You can also call functions defined in the parent window from the popup, In the parent window. 

Closing a popup 
Using window.close(): To close a popup window, you can call the close() method on the popup window object. 
Closing from an Event Handler: You often trigger the closing action from an event handler like a button click. 
Closing from Parent Window: You can also close a popup window from the parent window using the window.opener property. In the parent window. 
Dealing with Pop-up Blockers: Be aware that modern browsers often have pop-up blockers. If a user has pop-ups blocked, your window.close() call might be ignored. 
Security Considerations: Due to security restrictions, you can usually only close a window that was opened with window.open() in the first place. Trying to close a window not opened by the script may result in a security error. 

Scrolling and resizing 
Moving and resizing a window using JavaScript involves using the window.moveTo(), window.moveBy(), window.resizeTo(), and window.resizeBy() methods. 
win.moveBy(x,y) - Move the window relative to current position x pixels to the right and y pixels down. Negative values are allowed (to move left/up). 
win.moveTo(x,y) - Move the window to coordinates (x,y) on the screen. 
win.resizeBy(width,height) - Resize the window by given width/height relative to the current size. Negative values are allowed. 
win.resizeTo(width,height) - Resize the window to the given size. 

Scrolling a window 
Scrolling a window in JavaScript can be achieved using the scrollTo() and scrollBy() methods. These methods allow you to control the scroll position of the window. 
win.scrollBy(x,y) - Scroll the window x pixels right and y down relative the current scroll. Negative values are allowed. 
win.scrollTo(x,y) - Scroll the window to the given coordinates (x,y). 
elem.scrollIntoView(top = true) - Scroll the window to make elem show up at the top (the default) or at the bottom for elem.scrollIntoView(false). 

Focus/Blur on a window 
There are window.focus() and window.blur() methods to focus/unfocus on a window. 
1. Focusing a Window: 
To bring focus to a window, you can use the focus() method. This is typically used when you have multiple windows or tabs open and you want to ensure a specific one is active. 
2. Blurring a Window: 
Blurring a window removes focus from it. This can be useful if you want to shift focus away from a specific window or element. 
3. Focusing an Element: 
You can also use the focus() method on HTML elements to bring focus to them. For example, on an input field. 
4. Blurring an Element: 
Similarly, you can use the blur() method on elements to remove focus. 

These methods work in the context of the currently active window/tab. 
If a window or element is already focused, calling focus() on it again won't have any effect. 
Blurring a window can be used to simulate a loss of focus, which may trigger certain events or behaviors in your application. 
Blurring an element (e.g., an input field) can be useful for triggering form validation or other events when a user navigates away from the element. 

Coding Popups 
To create a popup window in JavaScript, you can use the window.open() method. 
Remember to be cautious with popups, as they can be intrusive and disrupt the user experience. It's generally recommended to use more modern UI patterns like modal dialogs for user interactions. 


## Cross-window Communication

Same Origin 
"Same-origin policy" is a fundamental security concept in web browsers. It dictates that a web page can only make requests to resources (like scripts, images, or data) from the same origin (meaning the same protocol, domain, and port) as the page itself. This is designed to prevent a malicious website from making requests to another website on the user's behalf. 
However, there are scenarios where you might want to make requests to a different origin, and this is where "Cross-Origin Resource Sharing" (CORS) comes into play. CORS is a mechanism that allows many resources (e.g., fonts, JavaScript, etc.) on a web page to be requested from another domain outside the domain from which the resource originated. 

To enable cross-origin requests, the server needs to include specific headers in its response. These headers specify which domains are allowed to access the resource. For example, a server might include an Access-Control-Allow-Origin header with a value of * to allow any domain to access the resource, or it might specify specific domains. 

In JavaScript, if you're making requests from a web page, you can use XMLHttpRequest or Fetch API to interact with resources on a different domain, provided that CORS headers are correctly set on the server. 

 

In action: iframe 

An <iframe> is an HTML element that allows you to embed one webpage (the "child" page) within another (the "parent" page). This is a powerful feature that enables you to display content from different sources on the same page. 

 

An <iframe> tag hosts a separate embedded window, with its own separate document and window objects. 

We can access them using properties: 

iframe.contentWindow to get the window inside the <iframe>. 

iframe.contentDocument to get the document inside the <iframe>, короткий аналог iframe.contentWindow.document. 

When we access something inside the embedded window, the browser checks if the iframe has the same origin. If that’s not so then the access is denied (writing to location is an exception, it’s still permitted). 

 

 

Windows on subdomains: document.domain 

document.domain is a property in JavaScript that allows scripts from different subdomains of the same domain to communicate with each other, bypassing the same-origin policy. This can be useful in scenarios where you have multiple subdomains and need to share data or interact with scripts across them. 

Setting document.domain: In order to enable communication between subdomains, you need to set document.domain to the same value on both the parent and child pages. 

Using document.domain for Communication: After setting document.domain to the same value on both pages, you can now access properties and methods from one frame or window to another, even if they are on different subdomains. 

Security Considerations: Be cautious when using document.domain. It can introduce security risks if not used carefully. Make sure you trust the content from different subdomains before enabling cross-subdomain communication. 

Limitations: Keep in mind that this approach only works if the pages are from the same top-level domain (e.g., example.com). It won't work if the pages are from completely different domains (e.g., example.com and otherdomain.com). 

 

 

Using iframes in web development can be powerful, but it's important to be aware of potential pitfalls and challenges. One common pitfall is the "Wrong Document" error, which occurs when you attempt to access or manipulate elements within an iframe that is still loading or when you reference the wrong document context. Here's a closer look at this pitfall and how to avoid it: 

Accessing Elements Too Soon: 

When you load a web page with an iframe, the content inside the iframe is loaded asynchronously. If you try to access elements inside the iframe too soon, before the iframe has finished loading, you may encounter a "Wrong Document" error. For example: 

javascriptCopy code 

// This can cause a "Wrong Document" error if the iframe is not fully loaded yet. const iframe = document.getElementById('myIframe'); const iframeDocument = iframe.contentDocument; // May be null if not loaded yet. const iframeElement = iframeDocument.getElementById('myElement');  

To avoid this, you should ensure that the iframe has fully loaded before trying to access its content. 

Waiting for the load Event: 

The most reliable way to avoid the "Wrong Document" error is to wait for the iframe's load event to fire before interacting with its content. This event indicates that the iframe has finished loading, and its document is accessible. Here's an example of how to do this: 

javascriptCopy code 

const iframe = document.getElementById('myIframe'); iframe.addEventListener('load', function() { const iframeDocument = iframe.contentDocument; const iframeElement = iframeDocument.getElementById('myElement'); // Now you can safely interact with the iframe content. });  

By waiting for the load event, you ensure that you're working with the correct document context. 

Cross-Origin Considerations: 

If the iframe contains content from a different origin, you may run into cross-origin security restrictions. In such cases, you'll need to ensure that the server hosting the iframe content includes the appropriate CORS headers to allow access from the parent page's domain. 

In summary, when working with iframes in JavaScript, it's crucial to wait for the load event to ensure that the iframe's content is fully loaded and accessible. Additionally, be aware of potential cross-origin issues if the iframe contains content from a different domain. 

 

 

Collection: window.frames 

An alternative way to get a window object for <iframe>– is to get it from the named collectionwindow.frames: 

By number: window.frames[0] – the window object for the first frame in the document. 

By name: window.frames.iframeName – the window object for the frame withname="iframeName". 

 

The window.frames property in JavaScript is an array-like object that represents all the frames (or iframes) contained within a window. It provides access to the individual frames using their numerical indices or their names. 

 

An iframe may have other iframes inside. The corresponding window objects form a hierarchy. 

Navigation links are: 

window.frames – the collection of “children” windows (for nested frames). 

window.parent – the reference to the “parent” (outer) window. 

window.top – the reference to the topmost parent window. 

 

Keep in mind that frames are a somewhat older and less commonly used feature in modern web development. Nowadays, iframes are more commonly used to embed content from one website into another. Iframes can be accessed in a similar way using window.frames. 

 

 

The “sandbox” iframe attribute 

The sandbox attribute is an HTML attribute that can be applied to an <iframe> element. It provides a way to restrict the behavior of the embedded content within the iframe, enhancing security and preventing potential malicious activities. 
When you use the sandbox attribute, you're essentially creating a "sandboxed" environment for the content within the iframe. This means that the content inside the iframe is subject to certain restrictions and cannot perform certain actions by default. 
The sandbox attribute allows for the exclusion of certain actions inside an <iframe> in order to prevent it from executing untrusted code. It “sandboxes” the iframe by treating it as coming from another origin and/or applying other limitations. 
There’s a “default set” of restrictions applied for <iframe sandbox src="...">. But it can be relaxed if we provide a space-separated list of restrictions that should not be applied as a value of the attribute, like this: <iframe sandbox="allow-forms allow-popups">. 

Here are some of the restrictions imposed by the sandbox attribute: 
No JavaScript Execution: JavaScript is disabled by default. You can re-enable it by including the allow-scripts attribute. 
No Form Submission: Form submission is disabled. You can re-enable it by including the allow-forms attribute. 
No Content Navigation: Links will not cause the iframe to navigate. You can re-enable it by including the allow-same-origin attribute. 
No Popups: The iframe cannot open new windows or pop-ups. You can re-enable it by including the allow-popups attribute. 
No Plugins or Media Autoplay: This is controlled by the allow-plugins and allow-autoplay attributes, respectively. 
No Access to Parent Document: The content in the iframe cannot access the properties or methods of the parent document. 
No Access to Cookies or Storage: The content in the iframe cannot access cookies or local storage. 
No Access to Sensors or Device APIs: This includes things like the camera, microphone, geolocation, etc. 

Here’s a list of limitations: 
allow-same-origin - By default "sandbox" forces the “different origin” policy for the iframe. In other words, it makes the browser to treat the iframe as coming from another origin, even if its src points to the same site. With all implied restrictions for scripts. This option removes that feature. 
allow-top-navigation - Allows the iframe to change parent.location. 
allow-forms - Allows to submit forms from iframe. 
allow-scripts - Allows to run scripts from the iframe. 
allow-popups - Allows to window.open popups from the iframe 

Cross Window Messaging 
Cross-window messaging is a technique in web development that allows scripts in one window or iframe to communicate with scripts in another window or iframe, even if they come from different origins (i.e., different domains, protocols, or ports). This enables seamless interaction between different components of a web application, facilitating tasks like sharing data, coordinating actions, or updating UI elements. 
The window.postMessage() method is the primary mechanism for achieving cross-window messaging. It allows scripts to send messages between windows or iframes securely. 

Key points to consider when using cross-window messaging: 
Security: Always specify the target origin in the postMessage call. This ensures that messages are only sent to the intended recipient. 
Origin Validation: In the receiving window, validate the event.origin property to ensure that messages are only accepted from trusted sources. 
Message Validation: Be cautious when processing received messages. Ensure that they are in the expected format before using them to prevent potential security issues. 
Window References: To send a message to a specific window, you need a reference to that window. This can be obtained via methods like window.open() or by accessing frames using window.frames. 
Cross-Domain Communication: Cross-window messaging allows communication between different domains, but both parties must explicitly allow it. The receiving window must set up an event listener for message events. 
Cross-window messaging is a powerful feature that enables advanced interactions in web applications, but it should be used carefully to prevent security vulnerabilities. Always validate and sanitize messages, and be mindful of potential cross-site scripting (XSS) attacks. 



## Contributing

Explain how others can contribute to your project. This could include information on how to report bugs, suggest features, or submit pull requests.
