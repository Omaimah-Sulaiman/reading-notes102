# LOCAL STORAGE

>localStorage is a property that allows JavaScript sites and apps to save key-value pairs in a web browser with no expiration date. This means the data stored in the browser will persist even after the browser window is closed.


## Where is localStorage stored?

>In Google Chrome, web storage data is saved in an SQLite file in a subfolder in the user’s profile. The subfolder is located at \AppData\Local\Google\Chrome\User Data\Default\Local Storage on Windows machines and ~/Library/Application Support/Google/Chrome/Default/Local Storage on macOS

>Firefox saves storage objects in an SQLite file called webappsstore.sqlite, which is also located in the user’s profile folder.


## What is Window.localStorage?
>The localStorage mechanism is available via the Window.localStorage property. Window.localStorage is part of the Window interface in JavaScript, which represents a window containing a DOM document.

>The Window interface features a wide range of functions, constructors, objects, and namespaces. Window.localStorage is a read-only property that returns a reference to the local storage object used to store data that is only accessible to the origin that created it.

## How does localStorage work?

>To use localStorage in your web applications, there are five methods to choose from:

 - setItem(): Add key and value to localStorage
 - getItem(): This is how you get items from localStorage
 - removeItem(): Remove an item by key from localStorage
 - clear(): Clear all localStorage
 - key(): Passed a number to retrieve the key of a localStorage
 - setItem(): How to store values in localStorage
  

>It takes two parameters: a key and a value. The key can be referenced later to fetch the value attached to it.

   window.localStorage.setItem('name', 'Obaseki Nosa');  


>Where name is the key and Obaseki Nosa is the value. Also note that localStorage can only store strings.
  To store arrays or objects, you would have to convert them to strings.
  To do this, we use the JSON.stringify() method before passing to setItem().
  
```
onst person = {
    name: "Obaseki Nosa",
    location: "Lagos",
}

window.localStorage.setItem('user', JSON.stringify(person));
```  