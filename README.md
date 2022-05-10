# comandos-uteis


## Passos para instalar git

* Descarregar de www.git-scm.com o git e instalá-lo.
* Abra a linha de comandos.
* Execute os seguintes comandos para definir a sua identidade para o git:

```bash
$ git config --global user.name "username_usado_no_git"
$ git config --global user.email "iniciais@meuemail.pt"
```

## Passos para correr aplicação django disponivel no GitHub

1. Abra a linha de comandos (PowerShell ou cmd)
1. Descarregue uma cópia (clone) do repositório com o comando `git clone https://github.com/teoria-da-computacao/web-app-flights` 
1. Entre na pasta  `cd web-app-flights`
1. Garanta que tem o pipenv instalado, correndo o comando `python3 -m pip install pipenv`
   1. se tiver erro de permissões execute:`Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser`
   1. se não conseguir instalar o pipenv ou der erro, trabalhe sem ambiente virtual. Para tal, instale o django sem pipenv (ambiente virtual) com o comando `python -m pip install django`. nessa caso não precisarás de ativar o ambiente, com `pipenv shell`
3. Crie um ambiente virtual `pipenv install django` 
4. Active o ambiente virtual `pipenv shell`
5. Lance a aplicação no browser com o comando `python manage.py runserver`. 
6. Tem disponíveis as aplicações hello no link `http://127.0.0.1:8000`
7. abra a pasta com o Pycharm ou VS Code, para a explorar.
8. devera criar um superuser `python manage.py createsuperuser` para pode aceder ao modo admin e ditar diretamente a base de dados
9. aceda à aplicação admin, em  `http://127.0.0.1:8000/admin`


## Comandos úteis

pipenv:
* `pipenv install`, cria ambiente virtual com os packages de pipfile
* `pipenv shell`, ativa ambiente virtual

python manage.py:
* `python manage.py runserver` para correr app
* `python manage.py shell` lança consola python para correr comandos
* `python manage.py makemigrations` cria ficheiro de instruções SQL para modificar base de dados de acordo com especificado em models.py
* `python manage.py migrate` realiza alterações na base de dados de acordo com models.py


## Manipular base de dados com ORM
Passos para manipular models.y e a Base de dados:
1. modificar `models.py`
1. `python manage.py makemigrations` cria comandos sql para modificar base de dados de acordo com o `models.py` 
1. `python manage.py migrate` executa comandos sql para modificar base de dados 
1. só depois podemos manipular a base de dados no `admin`, inserindo elementos
    1. tens que tens permissões de superuser: `py manage.py createsuperuser` 
1. na consola, tambem é possivel manipular a base de dados. para tal, lançar `python manage.py shell`, que lança a consola python. PAssps:
    1. importar models: `>> import nomeAplicacao.models`
    1. obter todos os objetos duma tabela: `>> Celula.objects.all()`

