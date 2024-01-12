### How to run tests:

Creating test database is really slow in our project, and we need to make the creation faster, but as of now this is how we can run the tests.
```
./manage.py test --keepdb

# Mind you, the first time you do this, it's still going to take quite some time because the db needs to created. But after that it's going to be quick!
```

 But what if we are testing a `Model` and we made some changes to it's schema?
```
# Simple, we can just makemigrations and migrate as usual
./manage.py makemigrations
./manage.py migrate

# This will update the test database, then again run
./manage.py test --keepdb
```

### Tools and Technologies
- Django's `unittest` library
- Factory Boy
- Django's test client
- Django Rest Framework's specific tools.
- Selenium for "in-browser" testing.

## Testing Philosophy
*most important thing, in my opinion*

From [Zulip]([Testing philosophy — Zulip 9.0-dev+git documentation](https://zulip.readthedocs.io/en/latest/testing/philosophy.html)):

> *“move quickly without breaking things”*

- Tests might seem pointless to write, especially the most obvious ones, but they can be really helpful when making code changes in the future, to make sure some other thing doesn't break.

>*A good practice is to get a “failing test” before you start to implement your feature. First, it is a useful exercise to understand what needs to happen in your tests before you write the code, as it can help drive out simple design or help you make incremental progress on a large feature. 
>
>Second, you want to avoid introducing tests that give false positives. Ensuring that a test fails before you implement the feature ensures that if somebody accidentally regresses the feature in the future, the test will catch the regression.

## Important Links:

- [Writing and running tests in django]([Writing and running tests | Django documentation | Django (djangoproject.com)](https://docs.djangoproject.com/en/5.0/topics/testing/overview/))
	- [Password hashing](https://docs.djangoproject.com/en/5.0/topics/testing/overview/#password-hashing)
	- [Preserving the test database](https://docs.djangoproject.com/en/5.0/topics/testing/overview/#preserving-the-test-database)
- [Testing tools]([Testing tools | Django documentation | Django (djangoproject.com)](https://docs.djangoproject.com/en/5.0/topics/testing/tools/))
- [Factory Boy](https://factoryboy.readthedocs.io/en/stable/)
- [Advanced Testing topics]([Advanced testing topics | Django documentation | Django (djangoproject.com)](https://docs.djangoproject.com/en/5.0/topics/testing/advanced/))
	- [The request Factory](https://docs.djangoproject.com/en/5.0/topics/testing/advanced/#django.test.RequestFactory)
	- [Testing class-based views](https://docs.djangoproject.com/en/5.0/topics/testing/advanced/#testing-class-based-views)