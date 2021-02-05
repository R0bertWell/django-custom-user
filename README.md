# :Criando um setup para fazer um modelo de User personalizado:
* #### Após criar o setup padrão do django, criaremos nossa pasta users, ou qualquer nome descritivo que quiser dar.
######(venv) DIR > py manage.py startapp (nome-do-app)
* #### Como mexeremos com tabelas, temos que usar os models primeiramente, além disso, como é um custom user, temos que importa o AbstractUser no módulo 'models'.
######from django.contrib.auth.models import AbstractUser
######from django.db import models
* #### Fazer com que uma classe 'QualquerCoisaUser' herde(extends) da AbstractUser importada.
###### class QualquerCoisaUser(AbstractUser):
* #### A classe ja está pronta para ser personalizada, campos podem ser adicionados à vontade, pra isso importamos os models (OBVIO)
###### from django.db import models
## Primeiros passos já criados, agora devemos por nosso modelo para que o django consiga ver, la em 'settings' do nosso projeto
### Em Apps instalados, adicionamos o nome da nossa pasta de Custom user, no nosso exemplo : 
######'users.apps.UsersConfig',

#### Lembrar de criar também uma variavel que remete ao nosso Modelo personalizado

######AUTH_USER_MODEL = 'users.User'

* ### Fazer agora as migrações
###### py manage.py makemigratios user
###### py manage.py migrate

* #### Criar um super user para acessar o painel de adm e logo depois startar o servidor
###### py manage.py createsuperuser
##### /\ criar a continha basic /\
###### py manage.py runserver

#### percebe-se que a tela de usuario nao foi adicionada ainda, temos que ir na admin.py 
###### from django.contrib import admin
###### from django.contrib.auth import admin as auth_admin
###### from .models import User
###### admin.site.register(User, auth_admin.UserAdmin)

