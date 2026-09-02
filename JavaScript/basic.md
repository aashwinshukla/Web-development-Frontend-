## overveiw
as we already saw html created a structure 
css style the website 
now javacript will help us to add interactivity

js works on browser.
js makes things usefull like making a calculator actually work , which was structured by html and styled by css. 

(add more info and overveiw )

## making files on IDE
to make the program know the language write the name of the file and .js 
eg :- index.js
we will also make index.html and style.css

## linking them 
```html
    !--inside index.html--!
    <!DOCTYPE html>
    <html lang = "en">
    <head>
        <title>My Website</title>
        <link rel = "stylesheet" href = "style.css"> !--css file added which was in same folder --!
    </head>
    <body>
        <h1></h1>
        <h2></h2>
        <p></p>
        <script src = "index.js"></script> !--javascript file added which was in the same file, also try to keep this js declaration at bottom so if any issue we want at least html to render--!
    </body>
    </html>
```


```css
    /*inside style.css*/
    body{
        font-famly: Verdana;
        font-size: 2em;
    }
    
```

## getting output 
to get output in js we have to 
```js
    // inside index.js
    console.log(`hello`);
    console.log('i like pizza');
    console.log("hello world");
    // above are few ways of printing things out but i will use back ticks ``

```
to check the output you will have to go live and then right click on the website and inspect and then go console thats where we will see js output 

```js
    // inside index.js
    
    window.alert(`This is an alert`);
    
```

this will create a alert pop up on the window with the text inside 

now lets populate our website 
```html
    !--inside index.html--!
    <!DOCTYPE html>
    <html lang = "en">
    <head>
        <title>My Website</title>
        <link rel = "stylesheet" href = "style.css">
    </head>
    <body>
        <h1 id = "myH1"></h1>
        !--add any id that you can remember so we can call on index.js--!
        <p id = "myP"></p>
        <script src = "index.js"></script> 
    </body>
    </html>
```

```js
    // inside index.js
    
    document.getElementById("myH1").textContent = `Hello`; 
    // this time website will show Hello h1 font 
    document.getElementById("myP").textContent = `i like solving and making`; 
    // we will also get the paragraph text 
    
```