# Data Models Queries
Querying django models


As **Django** provides the data models tool as layer on SQL databases to facilitate data manipulation in web apps ,
It also provide a simple way to query these data models, filter , count , sort , count ... items.

Let's us these models as example.

Here we have :
 - A **Blog** model , having two fields as attributes : name(the name of the blog article) , tagline(the taglines of the article)
 - An **Author** model , containing a name  en email attribute.
 - An **Entry** model containing the article's content, the related blog, the author or othors in a ```ManyToManyField``` field 

``` python
from datetime import date

from django.db import models

class Blog(models.Model):
    name = models.CharField(max_length=100)
    tagline = models.TextField()

    def __str__(self):
        return self.name

class Author(models.Model):
    name = models.CharField(max_length=200)
    email = models.EmailField()

    def __str__(self):
        return self.name

class Entry(models.Model):
    blog = models.ForeignKey(Blog, on_delete=models.CASCADE)
    headline = models.CharField(max_length=255)
    body_text = models.TextField()
    pub_date = models.DateField()
    mod_date = models.DateField(default=date.today)
    authors = models.ManyToManyField(Author, related_name='author_blogs')
    number_of_comments = models.IntegerField(default=0)
    number_of_pingbacks = models.IntegerField(default=0)
    rating = models.IntegerField(default=5)

    def __str__(self):
        return self.headline

```

# Querying

## Retrieving all objects
With the **all** method you can retrieve all the ```Entry``` objects from the model.


``` >>> all_entries = Entry.objects.all() ```

## Retrieving a filtered object
For retrieving specifif olters are very usefull.
A filter looks like : ```filter(**kwargs)``` and return a queryset containing object matching with the given parameters.

``` specific_entry = Entry.objects.all().filter(pub_date__year = 2006

