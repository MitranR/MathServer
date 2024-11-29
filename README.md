# Ex.05 Design a Website for Server Side Processing
## Date:28-11-2024

## AIM:
 To design a website to calculate the power of a lamp filament in an incandescent bulb in the server side. 


## FORMULA:
P = I<sup>2</sup>R
<br> P --> Power (in watts)
<br> I --> Intensity
<br> R --> Resistance

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
<html>
<head>
    <title>Power Cal</title>
</head>
<body style="font-family: Arial, sans-serif; background-color: red; margin: 0; padding: 0; display: flex; justify-content: center; align-items: center; height: 100vh;">
    <div style="background-color: rebeccapurple; padding: 20px; border-radius: 10px; box-shadow: 0 4px 8px black(0, 0, 0, 0.2); width: 300px;">
        <h1 style="text-align: center; color: black;">Calculation</h1>
        <form method="POST">
            {% csrf_token %}
            <label for="intensity" style="font-weight: bold; display: block; margin-bottom: 5px;">Enter Current (I in Amps):</label>
            <input type="number" id="intensity" name="intensity" value="{{intensity}}" style="width: 100%; padding: 8px; margin-bottom: 15px; border: 1px solid white; border-radius: 5px;">

            <label for="resistance" style="font-weight: bold; display: block; margin-bottom: 5px;">Enter Resistance (R in Ohms):</label>
            <input type="number" id="resistance" name="resistance" value="{{resistance}}" style="width: 100%; padding: 8px; margin-bottom: 15px; border: 1px solid white; border-radius: 5px;">

            <button type="submit" style="background-color: black; color: white; border: none; padding: 10px; width: 100%; border-radius: 5px; font-size: 16px; cursor: pointer;">
                Calculate Power
            </button>
            <br><br>

            <label for="power" style="font-weight: bold; display: block; margin-bottom: 5px;">Calculated Power (Watts):</label>
            <input type="text" id="power" name="power" value="{{power}}" readonly style="width: 100%; padding: 8px; border: 1px solid white; border-radius: 5px; background-color: white;">
        </form>
    </div>
</body>
</html>

views.py
from django.shortcuts import render 
def calculate(request): 
    context={} 
    context['pow'] = "0" 
    context['intensity'] = "0" 
    context['resistance'] = "0" 
    if request.method == 'POST': 
        print("POST method is used")
        intensity = request.POST.get('intensity','0')
        resistance = request.POST.get('resistance','0')
        print('request=',request) 
        print('intensity=',intensity) 
        print('resistance=',resistance) 
        pow=(int(intensity)*int(intensity)*int(resistance))
        context['power'] = pow
        context['intensity'] = intensity
        context['resistance'] = resistance
        print('Power=',pow) 
    return render(request,'mathapp/math.html',context)

urls.py
from django.contrib import admin 
from django.urls import path 
from mathapp import views 
urlpatterns = [ 
    path('admin/', admin.site.urls), 
    path('calculate/',views.calculate,name="calculation"),
    path('',views.calculate,name="calculateroot")
]


```

## SERVER SIDE PROCESSING:
![alt text](<Screenshot (17).png>)

## HOMEPAGE:
![alt text](<Screenshot (16).png>)

## RESULT:
The program for performing server side processing is completed successfully.
