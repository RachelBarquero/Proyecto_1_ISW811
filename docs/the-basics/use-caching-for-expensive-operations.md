[< Volver al Indice](/docs/readme.md)

# *Use Caching for Expensive-Operation*

En este Ccapitulo se implementó un sistema de almacenamiento en caché del HTML generado para cada publicación de blog. Esto lo que hacees mejorar el rendimiento del sitio web. Usar file_get_contents() cada vez que se accede a una publicación de blog no es eficiente, especialmente cuando muchas personas acceden simultáneamente a la misma publicación.

El cambio específico realizado en el archivo web.php fue:

```php
Route::get('posts/{post}', function ($slug) {

    if (! file_exists($path = __DIR__ . "/../resources/posts/{$slug}.html")) {
       return redirect('/');
    }

    $post = cache()->remember("post.{$slug}", 1200, fn() => file_get_contents($path));

    return view('post', ['post' => $post]);

})->where('post', '[A-z_\-]+');
```