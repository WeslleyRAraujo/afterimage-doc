# Controladores - Afterimage

Como criar controladores no meu projeto?
- Os controllers são definidos no diretório **/app/controller**;
<br>

Essa é a estrutua básica de um controlador:

- Arquivo **/public/index.php**
```php
<?php
namespace App\Controller; // namespace do controller

class HomeController
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
        echo json_encode([
                'message' => 'Thanks!!!!',
                'github' => 'WeslleyRAraujo'
        ], JSON_PRETTY_PRINT);
    }
}

```

O Objeto ***Router*** é responsável pelo roteamento da aplicação, os métodos **get** e **post** são os auxiliares para esse tipo de tarefa.

Os parâmetros para ambos são:
> 1. A rota que vai ser acessada;
> 2. O controlador + método. 'Path\To\Controller:method'

<br>

Os métodos **get** e **post** fazem uso do ```return $this;``` por isso é possível utilizados de forma encadeada como no exemplo abaixo. **Por questões de semântica é recomendado usar apenas para agrupamento de rotas**

```php
<?php
include_once "./bootstrap.php";

use Afterimage\Core\Router;

$route = new Router();

// rotas encadeadas
$route
    ->get('/usuario/cadastro', 'App\Controller\UserController:index')
    ->get('/usuario/excluir', 'App\Controller\UserController:delete')
    ->get('/usuario/salvar', 'App\Controller\UserController:store');
```

Para usar rotas no projeto é obrigatório o uso de um controlador, o manual sobre os controladores estão nesse link: [Controladores.](https://github.com/WeslleyRAraujo/afterimage-doc/Controllers.md)