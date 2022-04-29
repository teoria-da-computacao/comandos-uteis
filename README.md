# comandos-uteis

* `pipenv install`, cria ambiente virtual com os packages de pipfile
* `pipenv shell`, ativa ambiente virtual
* `python manage.py shell` lança consola python para correr comandos
* `python manage.py runserver` para correr app



# notas


class AuthorForm(ModelForm):
    class Meta:
        model = Cuidador
        fields = ('name', 'escolaridade', 'birth_date')
        widgets = {
            'name': Textarea(attrs={'cols': 80, 'rows': 20}),
        }
        
        
        
 selected="True"
