[< Volver al Indice](/docs/readme.md)

# ***Make a Route and link to it***

* Cambio de archivo en /views/welcome.blade.php.
  * En este capítulo, se cambia el nombre del archivo "welcome.blade.php" a "posts.blade.php", el cual se encuentra en la 
  carpeta /views/.

* Actualización en /routes/web.php.
  * Y en la parte de /routes/web.php cambiamos los siguiente:
  
```php
Route::get('/', function () {
    return view('posts');
});
```
* Continuamos eliminando el archivo app.js que se encuentra ubicado en la carpeta /public y luego nos movemos al archivo posts.blade.php y eliminamos la linea de codigo del script asi:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel= "stylesheet" href="/app.css">
    <title>My Blog</title>
</head>
<body>
    <h1>Hola mundillo</h1>
</body>
</html>
```

* Modificamos el archivo app.css:
  
```css
body {
    background: white;
    color: #222222;
}
```

* Modificamos el archivo posts.blade.php:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel= "stylesheet" href="/app.css">
    <title>My Blog</title>
</head>
<body>
    <article>
<h1>MI PRIMER POST</h1>
<P>
Si los extraterrestres nos estuvieran observando desde el espacio, probablemente pensarían que los humanos
 caminan a sus coches para viajar por la Tierra, cuando en realidad están yendo a una caja mágica que los 
 lleva a otro lugar con solo presionar botones y girar un volante. xd
</P>

    </article>
    
</body>
</html>
```

* Modificamos el archivo app.css:
  
```css
body{

background-color: white;
color: black;

max-width: 600px;

margin: auto;

font-family: sans-serif;
}

p{
    line-height: 1.6;
}
```
* Modificamos el archivo posts.blade.php con un segundo posts:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel= "stylesheet" href="/app.css">
    <title>My Blog</title>
</head>
<body>
    <article>
<h1>MI PRIMER POST</h1>
<P>
Si los extraterrestres nos estuvieran observando desde el espacio, probablemente pensarían que los humanos
 caminan a sus coches para viajar por la Tierra, cuando en realidad están yendo a una caja mágica que los 
 lleva a otro lugar con solo presionar botones y girar un volante. xd
</P>

<h1>MI SEGUNDO POST</h1>
<P>
"Los extraterrestres aterrizaron en la Tierra esperando encontrar una civilización avanzada. En lugar de 
eso, encontraron a humanos usando sombreros de papel de aluminio para bloquear 'señales alienígenas'.
 Decidieron que la Tierra no estaba lista para su 'Wi-Fi' universal y se fueron rascándose la cabeza 
 (o lo que sea que tengan). xd x2"

</P>
    </article>
    
</body>
</html>
```

* Modificamos el archivo app.css para dar margen:
  
```css
article + article{
    margin-top: 3rem;
    padding: 3rem;
    border-top: 1px solid #c5c5c5;
}
```

* Modificamos el archivo posts.blade.php con un tercer posts:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel= "stylesheet" href="/app.css">
    <title>My Blog</title>
</head>
<body>
    <article>
<h1>MI PRIMER POST</h1>
<P>
Si los extraterrestres nos estuvieran observando desde el espacio, probablemente pensarían que los humanos
 caminan a sus coches para viajar por la Tierra, cuando en realidad están yendo a una caja mágica que los 
 lleva a otro lugar con solo presionar botones y girar un volante. xd
</P>

<h1>MI SEGUNDO POST</h1>
<P>
"Los extraterrestres aterrizaron en la Tierra esperando encontrar una civilización avanzada. En lugar de 
eso, encontraron a humanos usando sombreros de papel de aluminio para bloquear 'señales alienígenas'.
 Decidieron que la Tierra no estaba lista para su 'Wi-Fi' universal y se fueron rascándose la cabeza 
 (o lo que sea que tengan). xd x2"

 <h1>MI TERCER POST</h1>

 <P>
 "Los extraterrestres llegaron a la Tierra con curiosidad. Al ver a los humanos bailando bajo 
 la lluvia, pensaron que era un ritual de comunicación. Decidieron intentarlo, pero rápidamente
  se dieron cuenta de que no tenían paraguas espaciales. xd x3jaja"


 </P>

</P>
    </article>
    
</body>
</html>
```

* Vamos a /routes/web.php y modificamos con lo siguiente:
  
  ```php
  Route::get('post', function () {
    return view ('post');
    });
```
