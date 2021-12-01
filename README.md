# javascript

## Trigger REST API from Vanilla JavaScript

```
<!doctype html>
<html lang="en">
  <head>
    <!-- Required meta tags -->
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1">

    <!-- Bootstrap CSS -->
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.1.3/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-1BmE4kWBq78iYhFldvKuhfTAU6auU8tT94WrHftjDbrCEXSU1oBoqyl2QvZ6jIW3" crossorigin="anonymous">

    <script src="js/invoke_api.js"></script>

    <title>Hello, world!</title>
  </head>
  <body>
    <h1>Invoking the REST API!</h1>

    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.1.3/dist/js/bootstrap.bundle.min.js" integrity="sha384-ka7Sk0Gln4gmtz2MlQnikT1wXgYsOg+OMhuP+IlRH9sENBO0LRn5q+8nbTov4+1p" crossorigin="anonymous"></script>

    <button type="submit" onclick="invokeRESTAPI()" class="btn btn-primary">Submit</button>

    <p id="showresulthere">Result will be shown here</p>

  </body>
</html>
```

- AJAX introduction - https://www.w3schools.com/xml/ajax_intro.asp
```
function invokeRESTAPI() {

    console.log('Start');

    var xhttp = new XMLHttpRequest();
    console.log('Created the object');
    xhttp.onreadystatechange = function() {

        console.log(this.readyState);

         if (this.readyState == 4 && this.status == 200) {
            const jsObject = JSON.parse(this.responseText);
            document.getElementById("showresulthere").innerHTML=jsObject.fact;
            console.log(jsObject.fact);
         }
    };
    console.log('Configured the function');
    xhttp.open("GET", "https://catfact.ninja/fact", true);
    console.log('Opened');
    xhttp.setRequestHeader("Content-type", "application/json");
    console.log('Set request header');
    xhttp.send();

    console.log('End');
}
```
