## Commands used in the project

# install django
pip install django

# start a project
django-admin startproject premiosplatziapp

# create app
py manage.py startapp polls	

# start dev server
(venv) \premiosplatziapp>py manage.py runserver

# migrations to make changes in databases
py manage.py makemigrations polls (prepare the migration)
py manage.py migrate (make the migration)

# interactive console django
py manage.py shell 

# clear screen
import os 
os.system("clear")

## Querys

# gest all questions
from polls.models import Question, Choice
Question.objects.all()
 
# create questions
q = Question(question_text="Cual es el mejor curso de Platzi?", pub_date=timezone.now())
q.save()

# get only 1 result, by pk
Question.objects.get(pk=1)

# filter 
Question.objects.filter(question_text__startswith="cual")
Question.objects.filter(pub_date__year=timezone.now().year)

# get all choices for a question
q.choice_set.all()

# create choices
q.choice_set.create(choice_text="Curso Basico de Python", votes=0)
q.choice_set.create(choice_text="Curso de Fundamentos de Ingenieria de Software", votes=0)
q.choice_set.create(choice_text="Curso de Elixir", votes=0)
  
# get total number of elements
q.choice_set.count()  

# filter choices
Choice.objects.filter(question__pub_date__year=timezone.now().year)

______

# create user
py manage.py createsuperuser
