# Controladores - Afterimage

Como criar controladores no meu projeto?
- Os controllers são definidos no diretório **/app/controller**;
<br>

Essa é a estrutua básica de um controlador:

- Arquivo **/app/controller/HomeController.php**
```php
<?php
namespace App\Controller; // namespace do controller

class HomeController // nome do controller
{
    // Retorna a view home
    public function index()
    {
        return view('home', [
            'title' => 'Tela Inicial',
            'breadcrumb' => ['Home']
        ]);
    }

    // exibe um json
    public function json()
    {
        header('Content-type: application/json');
        echo json_encode([
                'message' => 'Thanks!!!!',
                'github' => 'WeslleyRAraujo'
        ], JSON_PRETTY_PRINT);
    }
}

```

Os métodos a serem executados diretamente de **get** e **post** precisam ser publicos.

A linha ```return view('home', [...])``` chama a classe **Twig** para renderizar o layout.
