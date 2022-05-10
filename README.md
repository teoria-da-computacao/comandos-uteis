# comandos-uteis


Passos para instalar git:
* Descarregar de www.git-scm.com o git e instalá-lo.
* Abra a linha de comandos.
* Execute os seguintes comandos para definir a sua identidade para o git:

```bash
$ git config --global user.name "username_usado_no_git"
$ git config --global user.email "iniciais@meuemail.pt"
```

* `pipenv install`, cria ambiente virtual com os packages de pipfile
* `pipenv shell`, ativa ambiente virtual
* `python manage.py runserver` para correr app
* `python manage.py shell` lança consola python para correr comandos



Passos para manipular models.y e a Base de dados:
1. modificar `models.py`
1. `python manage.py makemigrations` cria comandos sql para modificar base de dados de acordo com o `models.py` 
1. `python manage.py migrate` executa comandos sql para modificar base de dados 
1. só depois podemos manipular a base de dados no `admin`, inserindo elementos
    1. tens que tens permissões de superuser: `py manage.py createsuperuser` 
1. na consola, tambem é possivel manipular a base de dados. para tal, lançar `python manage.py shell`, que lança a consola python. PAssps:
    1. importar models: `>> import nomeAplicacao.models`
    1. obter todos os objetos duma tabela: `>> Celula.objects.all()`



# campo ImageField

Passos para ter um campo para carregar corretamente uma imagem para uma pasta que queiramos:

1. Primeiro devemos dar instruções para criar uma pasta (MEDIA) onde guardar as imagens. Colocar em settings.py:

```Python
MEDIA_ROOT = os.path.join(BASE_DIR, "media")
MEDIA_URL = "/media/"
```

2. no app/urls.py   (funciona no config/urls.py ?!): 

```Python
urlPatterns += static(settings.MEDIA_URL, document_root=settings.MEDIA_ROOT)
```

Depois podemos utilizar na definição do atributo da classe. Podemos especificar  no `upload_to` a pasta, dentro da pasta MEDIA, onde queremos guardar. Por exemplo, em baixo queremos guardar uma imagem duma resposta duma resolução (com id 3) de um teste feito por um paciente (com id 1) em `users/1/resolutions/3`:

```Python
def resolution_path(instance, filename):
    return f'users/{instance.resolution.patient.id}/resolutions/{instance.resolution.id}'
    
    
class Answer(models.Model):
    question = models.ForeignKey('Question',
                                 on_delete=models.CASCADE)
    resolution = models.ForeignKey('Resolution',on_delete=models.CASCADE)
    submitted_answer = models.ImageField(upload_to=resolution_path)
```


# notas


class AuthorForm(ModelForm):
    class Meta:
        model = Cuidador
        fields = ('name', 'escolaridade', 'birth_date')
        widgets = {
            'name': Textarea(attrs={'cols': 80, 'rows': 20}),
        }
        
        
        
 selected="True"
