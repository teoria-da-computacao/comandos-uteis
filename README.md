# comandos-uteis

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

* para ativar, colocar em settings.py:

```Python
MEDIA_ROOT = os.path.join(BASE_DIR, "media")
MEDIA_URL = "/media/"
```

* no app/urls.py   (funciona no config/urls.py ?!): 

```Python
urlPatterns += static(settings.MEDIA_URL, document_root=settings.MEDIA_ROOT)
```


* exemplo de utilização:

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
