# Data Models Queries
Querying django models


As **Django** provides the data models tool as layer on SQL databases to facilitate data manipulation in web apps ,
It also provide a simple way to query these data models, filtering , counting , sorting these  items.

Let's use these models as example.

Here we have :
 - A **Blog** model , having two fields as attributes : name(the name of the blog article) , tagline(the taglines of the article)
 - An **Author** model , containing a name  en email attribute.
 - An **Entry** model containing the article's content, the related blog, the author or authors in a ```ManyToManyField``` field 

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
With the **all** method you can retrieve a QuerySet of all the ```Entry``` objects from the model.


``` >>> all_entries = Entry.objects.all() ```

## Retrieving a filtered object
For retrieving specifif objetcs , filters are very usefull.
A filter looks like : ```filter(**kwargs)``` and return a queryset containing object matching with the given parameters.
 

```python
q1 = Entry.objects.all().filter(pub_date__year = 2006) 
``` 

Here We're retrieving a QuerySet of all the Entries published in 2006
And we can add another filter to this queryset like :

```python
q2 = q1.filter(authors = Luc)
```

Here we're filtering for the Entries written in 2006 by **Luc**
and we can also **exclude** some objects like :

```python
q3 = q2.exclude(rating > 3)
```

Notice that the filter method as we have used here return a Queryset , not a single object .
You can retrieve an object by using the  ***get*** method with the same prarmeters that we used with the ***filter***

```python
q4 = q3.get(number_of_comments > 50)
```

Here we retrieve an entry object , by filtering the entries written in 2006 by **Luc**, excluding those whith less than 3 points of rating, that was commented more than 50 time .


References :
 - [CS50's Web Programming with Python and JavaScript](https://cs50.harvard.edu/web/)
 - [Making queries | Django documentation](https://docs.djangoproject.com/en/4.1/topics/db/queries/)

_Do not hesitate to submit your corrections to me in the event of an error in the lines above_

