# Django admin Panel

While working on web apps , having a good admin panel is gold .(at least for me).

Django provides a very efficient admin panel.
Based on your apps metadata , it provides you a model-centric interface where you(the admin or other trusted users) can manage the content of your site.
It's very useful when building new models , you can really simply check them up, add fileds, edit fiels before start using them in the code.

The admin panel is also customizable , and allow you to chnage the views , to edit the interface of the panel, the details of your models.

The admin panel is enabled by default when you create your app. and can be accessed at **localhost/admin/**.
To use it , you will have to create a superuser account: ```python manage.py createsuperuser``` .

References :
 - [The Django admin site-Documentation](https://docs.djangoproject.com/en/4.1/ref/contrib/admin/)

