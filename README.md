# Fortune teller checkpoints
Author link: [https://author.codecademy.com/content-items/e1477470374547ebd2b8560babc88df4/drafts/604d27bcb6ae10000e3e3238](https://author.codecademy.com/content-items/e1477470374546ebd2b8560babc88df4/drafts/604d27bcb6ae10000e3e3238)

## Start Project
1. `django-admin startproject fortuneteller`
2. Add `".cc-propeller.cloud"` to `ALLOWED_HOSTS` in __settings.py__
3. `cd` into __fortuneteller and run `python3 manage.py migrate`
4. Start development server and test for no errors.

  __NOTE: Start on port 4001 with `python3 manage.py runserver 0.0.0.0:4001`__

## Start app
5. `django-admin startapp randomfortune`
6. Add `"randomfortune.apps.RandomfortuneConfig"` to `INSTALLED_APPS`

## Create Template
6. Create __templates/randomfortune__ folder
8. Create __fortune.html__ and place provided text:
  ```html
<!DOCTYPE html>
<html lang="en">
<head>
  <title>Django Fortune Teller</title>
  <style>
    body {
      text-align: center;
    }
  </style>
</head>
<body>

  <h1>Here is your fortune:</h1>

  <p>{{fortune}}</p>

</body>
</html>
  ```

## Create View
9. Add `fortune()` to __views.py__ and return __fortune.html__
  ```python
  def fortune(request):
    return render(request, "randomfortune/fortune.html")
  ```
## Wire up view
10. Create __urls.py__ in __randomfortune/__
11. Import `path` and view functions
12. Create `urlpatterns` list and add route to `fortune()`
13. Import URLconf to project conf
14. Start development server and test

  __NOTE: Start on port 4001 with `python3 manage.py runserver 0.0.0.0:4001`__

## Add fortunes
15. Add list of fortunes to __views.py__
  ```python
  fortunes = [
    "All will go well with your new project.",
    "If you continually give, you will continually have.",
    "Self-knowledge is a life long process.",
    "You are busy, but you are happy.",
    "Your abilities are unparalleled.",
    "Those who care will make the effort.",
    "Now is the time to try something new.",
    "Miles are covered one step at a time.",
    "Don’t just think, act!",
  ]
  ```
16. Import `random` module
17. Inside `fortune()` get a random number
  ```python
  random_number = random.randrange(len(fortunes))
  ```
18. Create context variable with `"fortune"` as a key and random fortune as a value
  ```python
  context = {
    "fortune": fortunes[random_number]
  }
  ```
19. Add `context` to `render()`
20. Replace placeholder inside __fortune.html__ with `{{ fortune }}`
21. Refresh browser to see fortune
22. Next steps, spruce up __fortune.html__ with additional HTML formatting or adding internal css. Try adding another url view for your horoscope.