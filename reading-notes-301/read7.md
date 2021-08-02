# REST

 ![Rest](https://www.freecodecamp.org/news/content/images/2021/07/Screen-Shot-2021-07-10-at-12.21.28-PM.png)

 >Here is a quick example of all of the operations you'll be performing with Axios and your API endpoint — retrieving, creating, updating, and deleting posts:

 ![Rest](https://www.freecodecamp.org/news/content/images/2021/07/axios-react.gif)

# How to Make a GET Request
>To fetch data or retrieve it, make a GET request.

>First, you're going to make a request for individual posts. If you look at the endpoint, you are getting the first post from the /posts endpoint:
```
import axios from "axios";
import React from "react";

const baseURL = "https://jsonplaceholder.typicode.com/posts/1";

export default function App() {
  const [post, setPost] = React.useState(null);

  React.useEffect(() => {
    axios.get(baseURL).then((response) => {
      setPost(response.data);
    });
  }, []);

  if (!post) return null;

  return (
    <div>
      <h1>{post.title}</h1>
      <p>{post.body}</p>
    </div>
  );
}
```
>To perform this request when the component mounts, you use the useEffect hook. This involves importing Axios, using the .get() method to make a GET request to your endpoint, and using a .then() callback to get back all of the response data.

>The response is returned as an object. The data (which is in this case a post with id, title, and body properties) is put in a piece of state called post which is displayed in the component.

>Note that you can always find the requested data from the .data property in the response.

# How to Make a POST Request
>To create new data, make a POST request.
According to the API, this needs to be performed on the /posts endpoint. If you look at the code below, you'll see that there's a button to create a post:
```
import axios from "axios";
import React from "react";

const baseURL = "https://jsonplaceholder.typicode.com/posts";

export default function App() {
  const [post, setPost] = React.useState(null);

  React.useEffect(() => {
    axios.get(`${baseURL}/1`).then((response) => {
      setPost(response.data);
    });
  }, []);

  function createPost() {
    axios
      .post(baseURL, {
        title: "Hello World!",
        body: "This is a new post."
      })
      .then((response) => {
        setPost(response.data);
      });
  }

  if (!post) return "No post!"

  return (
    <div>
      <h1>{post.title}</h1>
      <p>{post.body}</p>
      <button onClick={createPost}>Create Post</button>
    </div>
  );
}
```
>When you click on the button, it calls the createPost function.
To make that POST request with Axios, you use the .post() method. As the second argument, you include an object property that specifies what you want the new post to be.
Once again, use a .then() callback to get back the response data and replace the first post you got with the new post you requested
This is very similar to the .get() method, but the new resource you want to create is provided as the second argument after the API endpoint.

# How to Make a PUT Request
>To update a given resource, make a PUT request.In this case, you'll update the first post.To do so, you'll once again create a button. But this time, the button will call a function to update a post:
```
import axios from "axios";
import React from "react";

const baseURL = "https://jsonplaceholder.typicode.com/posts";

export default function App() {
  const [post, setPost] = React.useState(null);

  React.useEffect(() => {
    axios.get(`${baseURL}/1`).then((response) => {
      setPost(response.data);
    });
  }, []);

  function updatePost() {
    axios
      .put(`${baseURL}/1`, {
        title: "Hello World!",
        body: "This is an updated post."
      })
      .then((response) => {
        setPost(response.data);
      });
  }

  if (!post) return "No post!"

  return (
    <div>
      <h1>{post.title}</h1>
      <p>{post.body}</p>
      <button onClick={updatePost}>Update Post</button>
    </div>
  );
}
```
>In the code above, you use the PUT method from Axios. And like with the POST method, you include the properties that you want to be in the updated resource.Again, using the .then() callback, you update the JSX with the data that is returned.

# How to Make a DELETE Request
>Finally, to delete a resource, use the DELETE method.As an example, we'll delete the first post.Note that you do not need a second argument whatsoever to perform this request:
```
import axios from "axios";
import React from "react";

const baseURL = "https://jsonplaceholder.typicode.com/posts";

export default function App() {
  const [post, setPost] = React.useState(null);

  React.useEffect(() => {
    axios.get(`${baseURL}/1`).then((response) => {
      setPost(response.data);
    });
  }, []);

  function deletePost() {
    axios
      .delete(`${baseURL}/1`)
      .then(() => {
        alert("Post deleted!");
        setPost(null)
      });
  }

  if (!post) return "No post!"

  return (
    <div>
      <h1>{post.title}</h1>
      <p>{post.body}</p>
      <button onClick={deletePost}>Delete Post</button>
    </div>
  );
}
```
>In most cases, you do not need the data that's returned from the .delete() method.But in the code above, the .then() callback is still used to ensure that your request is successfully resolved.In the code above, after a post is deleted, the user is alerted that it was deleted successfully. Then, the post data is cleared out of the state by setting it to its initial value of null.Also, once a post is deleted, the text "No post" is shown immediately after the alert message.

# How to Handle Errors with Axios
## What about handling errors with Axios?

>What if there's an error while making a request? For example, you might pass along the wrong data, make a request to the wrong endpoint, or have a network error.To simulate an error, you'll send a request to an API endpoint that doesn't exist: /posts/asdf.This request will return a 404 status code:
```
import axios from "axios";
import React from "react";

const baseURL = "https://jsonplaceholder.typicode.com/posts";

export default function App() {
  const [post, setPost] = React.useState(null);
  const [error, setError] = React.useState(null);

  React.useEffect(() => {
    // invalid url will trigger an 404 error
    axios.get(`${baseURL}/asdf`).then((response) => {
      setPost(response.data);
    }).catch(error => {
      setError(error);
    });
  }, []);
  
  if (error) return `Error: ${error.message}`;
  if (!post) return "No post!"

  return (
    <div>
      <h1>{post.title}</h1>
      <p>{post.body}</p>
    </div>
  );
}
```
>In this case, instead of executing the .then() callback, Axios will throw an error and run the .catch() callback function.In this function, we are taking the error data and putting it in state to alert our user about the error. So if we have an error, we will display that error message.In this function, the error data is put in state and used to alert users about the error. So if there's an error, an error message is displayed.When you run this code code, you'll see the text, "Error: Request failed with status code 404".

