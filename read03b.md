# what is css ?
>css (Cascading Style Sheets) allows you to create great-looking web pages

>CSS can be used for very basic document text styling — for example changing the color and size of headings and links. It can be used to create layout — for example turning a single column of text into a layout with a main content area and a sidebar for related information. It can even be used for effects such as animation. Have a look at the links in this paragraph for specific examples.

## 

# CSS syntax

>
```
h1 {
    color: red;
    font-size: 5em;
}


>  The rule opens with a selector . This selects the HTML element that we are going to style. In this case we are styling level one headings (<h1>).
We then have a set of curly braces { }. Inside those will be one or more declarations, which take the form of property and value pairs. Each pair specifies a property of the element(s) we are selecting, then a value that we'd like to give the property

### CSS color Property syntax
```
    body {
      color: red;
    }


    h1 {
      color: #00ff00;
    }

    p.ex {
      color: rgb(0,0,255);
    }


```
##
##

# Three Ways to Insert CSS
  There are three ways of inserting a style sheet:

 - External CSS
   -
   ```
   <!DOCTYPE html>
    <html>
    <head>
    <link rel="stylesheet" href="mystyle.css">
    </head>
    <body>
    <h1>This is a heading</h1>
    <p>This is a paragraph.</p>
    </body>
    </html>
 - Internal CSS
   
   ```
   <!DOCTYPE html>
      <html>
      <head>
      <style>
      body {
        background-color: linen;
      }
      h1 {
        color: maroon;
        margin-left: 40px;
      }
      </style>
      </head>
      <body>
      <h1>This is a heading</h1>
      <p>This is a paragraph.</p>
      </body>
      </html>

  - Inline CSS
  ```
    <!DOCTYPE html>
      <html>
      <body>
      <h1 style="color:blue;text-align:center;">This is a heading</h1>
      <p style="color:red;">This is a paragraph.</p>
      </body>
      </html>
