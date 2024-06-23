[< Volver al Indice](/docs/readme.md)

# *Route Wildcard Costraints*

Lo que vamos a hacer es añadir una condición a nuestra ruta para asegurar que el slug de la entrada del blog esté compuesto únicamente por letras, números, guiones y guiones bajos.

``` php 
Route::get('posts/{post}', function ($slug) {

    $path = __DIR__ . "/../resources/posts/{$slug}.html";

    if (! file_exists($path)){
       return redirect('/');
    }

    $post = file_get_contents($path);


    return view('post', [
        'post' => $post
    ]);

})->whereAlpha('post', '[A-z_\-]+');
```