[< Volver al Indice](/docs/readme.md)

 # *Use the Filesystem Class to Read a Directory*

  En este capítulo, nuestro objetivo será buscar y revisar todas las publicaciones ubicadas dentro del directorio recursos/publicaciones. 
 Una vez que tengamos una lista completa, las recorreremos y las mostraremos en la página principal de nuestro blog para ofrecer una visión general.

 * Primero, empezamos eliminando las rutas que añadimos en los archivos HTML creados en el capítulo anterior:

``` html
 <h1>Mi primer Post<h1>
    <P>
    Si los extraterrestres nos estuvieran observando desde el espacio, probablemente pensarían que los humanos
     caminan a sus coches para viajar por la Tierra, cuando en realidad están yendo a una caja mágica que los 
     lleva a otro lugar con solo presionar botones y girar un volante. xd
    </P>
``` 

*  Después de esto, modificaremos el archivo web.php, una sección de código la moveremos a otra ubicación:

```php
Route::get('/', function () {
    return view('posts');
});

Route::get('/', function () {

    return view('posts', [
        'posts' => Post::all()
    ]);
});

Route::get('posts/{post}', function ($slug) {
 
    return view('post', [
        'post' => Post::find($slug)
    ]);
```

* Vamos a reorganizar el código actual moviéndolo a un nuevo archivo llamado Post.php dentro de la carpeta app/Models. Este archivo será una clase que hará el manejo del código de manera más organizada y dinámica, utilizando tres bibliotecas adicionales para mejorar su funcionalidad:

``` php
<?php

namespace App\Models;

use Illuminate\Database\Eloquent\Model;
use Illuminate\Database\Eloquent\ModelNotFoundException;
use Illuminate\Support\Facades\File;
use PhpParser\Node\Expr\FuncCall;

class Post
{
    public static function all()
    {
        $files = File::files(resource_path("posts/"));

        return array_map(fn($file) => $file->getContents(), $files);
    }

    public static function find($slug)
    {
        if (!file_exists($path = resource_path("posts/{$slug}.html"))) {
            throw new ModelNotFoundException();
        }

        return cache()->remember("posts.{$slug}", 1200, fn() => file_get_contents($path));
    }
}
```
* Tambien modificaremos el archivo posts.blade.php:

``` php
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel= "stylesheet" href="/app.css">
    <title>My Blog</title>
</head>
<body>
    <?php foreach ( $posts as $post ) : ?>
    <article>
        <?= $post; ?>
    </article>
    <?php endforeach; ?>
</body>
</html>
```

* Por ultimo creamos un cuarto Post, este se crea para dar un ejemplo:

```html
---
tittle: My Fourth Post
excerpt:  En un pequeño planeta en la Vía Láctea
date: 2024-0-26
---

<h1>My Fourth Post</h1>

<p>
    En un pequeño planeta en la Vía Láctea, vivían los Bliblins, seres verdes con tres ojos y 
    antenas brillantes. Su comida favorita era el gelatinastrón, un postre que brillaba en la oscuridad y
     hacía reír a quien lo comía. Los Bliblins pasaban sus días jugando a un juego de palabras telepático
      llamado "Punsatron", donde competían para inventar los juegos de palabras más absurdos y divertidos
       del universo.
</p>
```