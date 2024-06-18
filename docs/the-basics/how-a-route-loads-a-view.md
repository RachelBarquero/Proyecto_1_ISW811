[< Volver al Indice](/docs/readme.md)

# ***How a Route Loads a View***

 En Laravel, las rutas se configuran en el archivo routes/web.php y te permiten mostrar diferentes tipos de contenido según lo que necesites.
  Por ejemplo: se puede mostrar una página de bienvenida usando una vista:

```PHP
Route::get('/', function () {
    return view('welcome');
});
```
Laravel también te permite retornar texto simple, como un saludo:

```PHP
Route::get('/', function () {
    return '¡Hola Mundo!';
});
```
También, se puede retornar datos en formato JSON, lo cual es útil para APIs:

```PHP
Route::get('/', function () {
    return ['foo' => 'bar'];
});
```