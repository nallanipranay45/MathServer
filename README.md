# Ex.05 Design a Website for Server Side Processing
## Date:04/10/2025

## AIM:
 To design a website to calculate the BMI


## FORMULA:
P = w<sup>2</sup>H
<br> w--> weigth
<br> H-->Heigth
<br>

## DESIGN STEPS:

### Step 1:
Clone the repository from GitHub.

### Step 2:
Create Django Admin project.

### Step 3:
Create a New App under the Django Admin project.

### Step 4:
Create python programs for views and urls to perform server side processing.

### Step 5:
Create a HTML file to implement form based input and output.

### Step 6:
Publish the website in the given URL.

## PROGRAM :
```
math.html
<html>

<head>
    <title>BMI Calculator</title>
    <style>
        .goku {
            width: 40%;

            border: double 5px blue;
            border-radius: 5%;
            background: cyan;
        }

        body {
            font-family: Arial, sans-serif;
            margin: 45px;
            background-color:brown
        }

        form {

            padding: 20px;
            border-radius: 8px;
            width: 300px;
        }

        input {
            margin-top: 10px;
            width: 100%;
            padding: 8px;
        }

        h2 {
            margin-top: 20px;
        }
    </style>
</head>

<body>
    <center>
        <div class="goku">
            <h1>BMI CALCULATER</h1>
            <h1>lakshmi pranay n-25017706</h1>
            <form method="post">
                {% csrf_token %}
                <label for="height">Heigth [cm]:</label>
                <input type="text" id="height" name="height" required>

                <label for="weight">Weight [kg]:</label>
                <input type="text" id="weight" name="weight" required>

                <input type="submit" value="CALCULATE_BMI">
                {% if bmi %}
                <h2>YOUR BMI: {{ bmi }}</h2>
                {% if category %}
                <p>Category: {{ category }}</p>
                {% endif %}
                {% endif %}
        </div>

        </form>

        </div>
    </center>
</body>

</html>

urls.py

from django.contrib import admin
from django.urls import path
from mathapp import views

urlpatterns = [
    path('admin/', admin.site.urls),
    path('bmi/',views.calculate_bmi,name="bmi"),
    path('',views.calculate_bmi,name="bmicalculator")
]


views.py

from django.shortcuts import render
def calculate_bmi(request):
    context={}
    context['bmi']="0"
    context['w']="0"
    context['h']="0"
    if(request.method=='POST'):
       w= float(request.POST.get('weight','0'))
       h=float(request.POST.get('height','0'))
       print('request=',request)
       
       print('Weight=',w)
       print('Height=',h)
       bmi=w/((h/100)**2)
       context['bmi']=bmi
       context['w']=w
       context['h']=h
       print('BMI=',bmi)
    return render(request,'mathapp/math.html',context)





```

## SERVER SIDE PROCESSING:
![alt text](<Screenshot (17).png>)


## HOMEPAGE:
![alt text](<Screenshot (16).png>)


## RESULT:
The program for performing server side processing is completed successfully.
