# 0x06. AirBnB clone - Web dynamic
<img src="https://github.com/jarehec/AirBnB_clone_v3/blob/master/dev/HBTN-hbnb-Final.png" width="160" height=auto />

# AirBnB Clone: Phase # 4

: API with Swagger

The console is the first segment of the AirBnB project at Holberton School that will collectively cover fundamental concepts of higher level programming. The goal of AirBnB project is to eventually deploy our server a simple copy of the AirBnB Website(HBnB). A command interpreter is created in this segment to manage objects for the AirBnB(HBnB) website.

#### Functionalities of this command interpreter:
* Create a new object (ex: a new User or a new Place)
* Retrieve an object from a file, a database etc...
* Do operations on objects (count, compute stats, etc...)
* Update attributes of an object
* Destroy an object

# Concepts
_For this project, we expect you to look at this concept:_
* [AirBnB clone](https://intranet.alxswe.com/concepts/74)

# 1. AirBnB clone

![65f4a1dd9c51265f49d0](https://github.com/elyse502/AirBnB_clone/assets/125453474/acf08a8b-f4e4-47b6-b32e-25d73c434b32)

I know you were waiting for it: it’s here!

The AirBnB clone project starts now until… the end of the first year. The goal of the project is to deploy on your server a simple copy of the [AirBnB website](https://www.airbnb.com/).

You won’t implement all the features, only some of them to cover all fundamental concepts of the higher level programming track.

After 4 months, you will have a complete web application composed by:
* A command interpreter to manipulate data without a visual interface, like in a Shell (perfect for development and debugging)
* A website (the front-end) that shows the final product to everybody: static and dynamic
* A database or files that store data (data = objects)
* An API that provides a communication interface between the front-end and your data (retrieve, create, delete, update them)

## Final product

![fe2e3e7701dec72ce612472dab9bb55fe0e9f6d4](https://github.com/elyse502/AirBnB_clone/assets/125453474/25b2713a-ff3d-496e-ac61-c82173a11825)


![da2584da58f1d99a72f0a4d8d22c1e485468f941](https://github.com/elyse502/AirBnB_clone/assets/125453474/1841b787-c8af-49b4-9c5e-dab0a5633846)

## Concepts to learn
* [Unittest](https://docs.python.org/3.4/library/unittest.html#module-unittest) - and please work all together on tests cases
* **Python packages** concept page
* Serialization/Deserialization
* `*args, **kwargs`
* `datetime`
* More coming soon!

## Steps
You won’t build this application all at once, but step by step.

Each step will link to a concept:

## The console
* create your data model
* manage (create, update, destroy, etc) objects via a console / command interpreter
* store and persist objects to a file (JSON file)

The first piece is to manipulate a powerful storage system. This storage engine will give us an abstraction between “My object” and “How they are stored and persisted”. This means: from your console code (the command interpreter itself) and from the front-end and RestAPI you will build later, you won’t have to pay attention (take care) of how your objects are stored.

This abstraction will also allow you to change the type of storage easily without updating all of your codebase.

The console will be a tool to validate this storage engine

![815046647d23428a14ca](https://github.com/elyse502/AirBnB_clone/assets/125453474/10c12086-2708-4322-b6b4-a3df7a66123b)

## Web static
* learn HTML/CSS
* create the HTML of your application
* create template of each object

![87c01524ada6080f40fc](https://github.com/elyse502/AirBnB_clone/assets/125453474/704ad78d-053c-4c30-bedc-3d87b19ebc69)

## MySQL storage
* replace the file storage by a Database storage
* map your models to a table in database by using an O.R.M.

![5284383714459fa68841](https://github.com/elyse502/AirBnB_clone/assets/125453474/f492838c-4d2a-4a75-8324-cc903634c361)

## Web framework - templating
* create your first web server in Python
* make your static HTML file dynamic by using objects stored in a file or database

![cb778ec8a13acecb53ef](https://github.com/elyse502/AirBnB_clone/assets/125453474/e801f00d-ced0-42ce-9bfc-acd1c2273f3e)

## RESTful API
* expose all your objects stored via a JSON web interface
* manipulate your objects via a RESTful API

![06fccc41df40ab8f9d49](https://github.com/elyse502/AirBnB_clone/assets/125453474/d0515e05-f4b0-44a7-bbbc-f7ad7ecc159f)

## Web dynamic
* learn JQuery
* load objects from the client side by using your own RESTful API

![d2d06462824fab5846f3](https://github.com/elyse502/AirBnB_clone/assets/125453474/50a350bb-2492-4701-a198-ef284721d971)

## Files and Directories
* `models` directory will contain all classes used for the entire project. A class, called “model” in a OOP project is the representation of an object/instance.
* `tests` directory will contain all unit tests.
* `console.py` file is the entry point of our command interpreter.
* `models/base_model.py` file is the base class of all our models. It contains common elements:
    * attributes: `id`, `created_at` and `updated_at`
    * methods: `save()` and `to_json()`
* `models/engine` directory will contain all storage classes (using the same prototype). For the moment you will have only one: `file_storage.py`.

## Storage
Persistency is really important for a web application. It means: every time your program is executed, it starts with all objects previously created from another execution. Without persistency, all the work done in a previous execution won’t be saved and will be gone.

In this project, you will manipulate 2 types of storage: file and database. For the moment, you will focus on file.

Why separate “storage management” from “model”? It’s to make your models modular and independent. With this architecture, you can easily replace your storage system without re-coding everything everywhere.

You will always use class attributes for any object. Why not instance attributes? For 3 reasons:
* Provide easy class description: everybody will be able to see quickly what a model should contain (which attributes, etc…)
* Provide default value of any attribute
* In the future, provide the same model behavior for file storage or database storage

## How can I store my instances?
That’s a good question. So let’s take a look at this code:
```groovy
class Student():
    def __init__(self, name):
        self.name = name

students = []
s = Student("John")
students.append(s)
```
Here, I’m creating a student and store it in a list. But after this program execution, my Student instance doesn’t exist anymore.
```groovy
class Student():
    def __init__(self, name):
        self.name = name

students = reload() # recreate the list of Student objects from a file
s = Student("John")
students.append(s)
save(students) # save all Student objects to a file
```
Nice!

But how it works?

First, let’s look at `save(students)`:
* Can I write each `Student` object to a file => _NO_, it will be the memory representation of the object. For another program execution, this memory representation can’t be reloaded.
* Can I write each `Student.name` to a file => _YES_, but imagine you have other attributes to describe `Student`? It would start to be become too complex.

The best solution is to convert this list of `Student` objects to a JSON representation.

Why JSON? Because it’s a standard representation of object. It allows us to share this data with other developers, be human readable, but mainly to be understood by another language/program.

Example:
* My Python program creates `Student` objects and saves them to a JSON file
* Another Javascript program can read this JSON file and manipulate its own `Student` class/representation

And the `reload()`? now you know the file is a JSON file representing all `Student` objects. So `reload()` has to read the file, parse the JSON string, and re-create `Student` objects based on this data-structure.

## File storage == JSON serialization
For this first step, you have to write in a file all your objects/instances created/updated in your command interpreter and restore them when you start it. You can’t store and restore a Python instance of a class as “Bytes”, the only way is to convert it to a serializable data structure:
* convert an instance to Python built in serializable data structure (list, dict, number and string) - for us it will be the method `my_instance.to_json()` to retrieve a dictionary
* convert this data structure to a string (JSON format, but it can be YAML, XML, CSV…) - for us it will be a `my_string = JSON.dumps(my_dict)`
* write this string to a file on disk

And the process of deserialization?

The same but in the other way:
* read a string from a file on disk
* convert this string to a data structure. This string is a JSON representation, so it’s easy to convert - for us it will be a `my_dict = JSON.loads(my_string)`
* convert this data structure to instance - for us it will be a `my_instance = MyObject(my_dict)`

### `*args, **kwargs`

#### [`How To Use them`](https://www.digitalocean.com/community/tutorials/how-to-use-args-and-kwargs-in-python-3)
How do you pass arguments to a function?
```groovy
def my_fct(param_1, param_2):
    ...

my_fct("Best", "School")
```
But with this function definition, you must call `my_fct` with 2 parameters, no more, no less.

Can it be dynamic? Yes you can:
```groovy
def my_fct(*args, **kwargs):
    ...

my_fct("Best", "School")
```
What? What’s `*args` and `**kwargs`?
* `*args` is a Tuple that contains all arguments
* `*kwargs` is a dictionary that contains all arguments by key/value

A dictionary? But why?

So, to make it clear, `*args` is the list of anonymous arguments, no name, just an order. `**kwargs` is the dictionary with all named arguments.

Examples:
```groovy
def my_fct(*args, **kwargs):
    print("{} - {}".format(args, kwargs))

my_fct() # () - {}
my_fct("Best") # ('Best',) - {}
my_fct("Best", 89) # ('Best', 89) - {}
my_fct(name="Best") # () - {'name': 'Best'}
my_fct(name="Best", number=89) # () - {'name': 'Best', 'number': 89}
my_fct("School", 12, name="Best", number=89) # ('School', 12) - {'name': 'Best', 'number': 89}
```
Perfect? Of course you can mix both, but the order should be first all anonymous arguments, and after named arguments.

Last example:
```groovy
def my_fct(*args, **kwargs):
    print("{} - {}".format(args, kwargs))

a_dict = { 'name': "Best", 'age': 89 }

my_fct(a_dict) # ({'age': 89, 'name': 'Best'},) - {}
my_fct(*a_dict) # ('age', 'name') - {}
my_fct(**a_dict) # () - {'age': 89, 'name': 'Best'}
```
You can play with these 2 arguments to clearly understand where and how your variables are stored.

### `datetime`
`datetime` is a Python module to manipulate date, time etc…

In this example, you create an instance of `datetime` with the current date and time:
```groovy
from datetime import datetime

date_now = datetime.now()
print(type(date_now)) # <class 'datetime.datetime'>
print(date_now) # 2017-06-08 20:42:42.170922
```
`date_now` is an object, so you can manipulate it:
```groovy
from datetime import timedelta

date_tomorrow = date_now + timedelta(days=1)
print(date_tomorrow) # 2017-06-09 20:42:42.170922
```
… you can also store it:
```groovy
a_dict = { 'my_date': date_now }
print(type(a_dict['my_date'])) # <class 'datetime.datetime'>
print(a_dict) # {'my_date': datetime.datetime(2017, 6, 8, 20, 42, 42, 170922)}
```
What? What’s this format when a `datetime` instance is in a datastructure??? It’s unreadable.

How to make it readable: [`strftime`](https://strftime.org/)
```groovy
print(date_now.strftime("%A")) # Thursday
print(date_now.strftime("%A %d %B %Y at %H:%M:%S")) # Thursday 08 June 2017 at 20:42:42
```
## Data diagram

![99e1a8f2be8c09d5ce5ac321e8cf39f0917f8db5](https://github.com/elyse502/AirBnB_clone/assets/125453474/3d7ad352-6e69-479b-be7c-96e850e0cb2c)

<img src="https://user-images.githubusercontent.com/73097560/115834477-dbab4500-a447-11eb-908a-139a6edaec5c.gif"><br><br>

# Resources🏗️
### Read or watch:
* [Selector](https://jquery-tutorial.net/selectors/using-elements-ids-and-classes/)
* [Get and set content](https://jquery-tutorial.net/dom-manipulation/getting-and-setting-content/)
* [Manipulate CSS classes](https://jquery-tutorial.net/dom-manipulation/getting-and-setting-css-classes/)
* [Manipulate DOM elements](https://jquery-tutorial.net/dom-manipulation/the-append-and-prepend-methods/)
* [Document ready](https://learn.jquery.com/using-jquery-core/document-ready/)
* [Introduction](https://jquery-tutorial.net/ajax/introduction/)
* [GET & POST request](https://jquery-tutorial.net/ajax/the-get-and-post-methods/)
* [HTTP access control (CORS)](https://developer.mozilla.org/en-US/docs/Web/HTTP/CORS)

# General🧵
* How cool it is to request your own API
* How to modify an HTML element style
* How to get and update an HTML element content
* How to modify the DOM
* How to make a `GET` request with JQuery Ajax
* How to make a `POST` request with JQuery Ajax
* How to listen/bind to DOM events
* How to listen/bind to user events

# Requirements
## General
* Allowed editors: `vi`, `vim`, `emacs`
* All your files will be interpreted on Chrome (version 57.0)
* All your files should end with a new line
* A `README.md` file, at the root of the folder of the project, is mandatory
* Your code should be `semistandard` compliant with the flag `--global $`: `semistandard *.js --global $`
* All your JavaScript must be in the folder `scripts`
* You must use JQuery version 3.x
* You are not allowed to use `var`
* HTML should not reload for each action: DOM manipulation, update values, fetch data…

# More Info
## Import JQuery
```groovy
<head>
    <script src="https://code.jquery.com/jquery-3.2.1.min.js"></script>
</head>
```
## Before starting the project…
You will work on a codebase using [Flasgger](https://github.com/flasgger/flasgger), you will need to install it locally first before starting the RestAPI:
```groovy
$ sudo apt-get install -y python3-lxml
$ sudo pip3 install flask_cors # if it was not installed yet
$ sudo pip3 install flasgger
```
If the RestAPI is not starting, please read the error message. Based on the(ses) error message(s), you will have to troubleshoot potential dependencies issues.

Here some solutions:

**`jsonschema` exception**
```groovy
$ sudo pip3 uninstall -y jsonschema 
$ sudo pip3 install jsonschema==3.0.1
```
**`No module named 'pathlib2'`**
```groovy
$ sudo pip3 install pathlib2
```
## Expose ports from your Vagrant
In your `Vagrantfile`, add this line for each port forwarded
```groovy
# I expose the port 5001 of my vm to the port 5001 on my computer
config.vm.network :forwarded_port, guest: 5001, host: 5001
```
if you need to expose other ports, same line but you will need to replace the “guest port” (inside your vagrant) and your “host port” (outside your vagrant, used from your browser for example)

It’s important in your project, to use the AirBnB API with the port `5001`

![hbnb_step5](https://github.com/elyse502/AirBnB_clone_v4/assets/125453474/246adcf0-fd6c-496a-ab6b-b243bfb31e4d)

# Tasks 📃
## 0. Last clone!: [AirBnB_clone_v4](https://github.com/elyse502/AirBnB_clone_v4)
A new codebase again? Yes!

For this project you will fork this [codebase](https://github.com/jzamora5/AirBnB_clone_v3):
* Update the repository name to `AirBnB_clone_v4`
* Update the `README.md`:
   * Add yourself as an author of the project
   * Add new information about your new contribution
   * Make it better!
* If you’re the owner of this codebase, create a new repository called `AirBnB_clone_v4` and copy over all files from `AirBnB_clone_v3`
* If you didn’t install Flasgger from the previous project, it’s time! `sudo pip3 install flasgger`

## 1. Cash only: [0-hbnb.py](https://github.com/elyse502/AirBnB_clone_v4/blob/master/web_dynamic/0-hbnb.py), [templates/0-hbnb.html](https://github.com/elyse502/AirBnB_clone_v4/blob/master/web_dynamic/templates/0-hbnb.html)
Write a script that starts a Flask web application:
* Based on `web_flask`, copy: `web_flask/static`, `web_flask/templates/100-hbnb.html`, `web_flask/__init__.py` and `web_flask/100-hbnb.py` into the `web_dynamic` folder
* Rename `100-hbnb.py` to `0-hbnb.py`
* Rename `100-hbnb.html` to `0-hbnb.html`
* Update `0-hbnb.py` to replace the existing route to `/0-hbnb/`

**If `100-hbnb.html` is not present, use `8-hbnb.html` instead**
```groovy
guillaume@ubuntu:~/AirBnB_v4$ HBNB_MYSQL_USER=hbnb_dev HBNB_MYSQL_PWD=hbnb_dev_pwd HBNB_MYSQL_HOST=localhost HBNB_MYSQL_DB=hbnb_dev_db HBNB_TYPE_STORAGE=db python3 -m web_dynamic.0-hbnb
* Running on http://0.0.0.0:5000/ (Press CTRL+C to quit)
....
```
One problem now is the asset caching done by Flask.

To avoid that, you will add a query string to each asset:

In `0-hbnb.py`, add a variable `cache_id` to the `render_template`. The value of this variable must be an UUID `(uuid.uuid4()`)

In `0-hbnb.html`, add this variable `cache_id` as query string to each `<link>` tag URL
```groovy
guillaume@ubuntu:~/AirBnB_v4$ curl -s -XGET http://0.0.0.0:5000/0-hbnb/ | head -6
<!DOCTYPE HTML>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <link rel="stylesheet" type="text/css" href="../static/styles/4-common.css?e211c9eb-7d17-4f12-85eb-4d50fa50cb1d" />
    <link rel="stylesheet" type="text/css" href="../static/styles/3-header.css?e211c9eb-7d17-4f12-85eb-4d50fa50cb1d" />
guillaume@ubuntu:~/AirBnB_v4$ curl -s -XGET http://0.0.0.0:5000/0-hbnb/ | head -6
<!DOCTYPE HTML>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <link rel="stylesheet" type="text/css" href="../static/styles/4-common.css?f834413e-0aa9-4767-b64a-c92db9cb1f82" />
    <link rel="stylesheet" type="text/css" href="../static/styles/3-header.css?f834413e-0aa9-4767-b64a-c92db9cb1f82" />
guillaume@ubuntu:~/AirBnB_v4$
```

## 2. Select some Amenities to be comfortable!: [1-hbnb.py](https://github.com/elyse502/AirBnB_clone_v4/blob/master/web_dynamic/1-hbnb.py), [templates/1-hbnb.html](https://github.com/elyse502/AirBnB_clone_v4/blob/master/web_dynamic/templates/1-hbnb.html), [static/scripts/1-hbnb.js](https://github.com/elyse502/AirBnB_clone_v4/blob/master/web_dynamic/static/scripts/1-hbnb.js)
For the moment the filters section is static, let’s make it dynamic!

Replace the route `0-hbnb` with `1-hbnb` in the file `1-hbnb.py` (based on `0-hbnb.py`)

Create a new template `1-hbnb.html` (based on `0-hbnb.html`) and update it:
* Import JQuery in the `<head>` tag
* Import the JavaScript `static/scripts/1-hbnb.js` in the `<head>` tag
   * In 1-hbnb.html and the following HTML files, add this variable cache_id as query string to the above `<script>` tag
* Add a `<input type="checkbox">` tag to the `li` tag of each amenity
* The new checkbox must be at 10px on the left of the Amenity name
* Add to the `input` tags of each amenity (`<li>` tag) the attribute `data-id=":amenity_id"` => this will allow us to retrieve the Amenity ID from the DOM
* Add to the `input` tags of each amenity (`<li>` tag) the attribute `data-name=":amenity_name"` => this will allow us to retrieve the Amenity name from the DOM

Write a JavaScript script (`static/scripts/1-hbnb.js`):
* Your script must be executed only when DOM is loaded
* You must use JQuery
* Listen for changes on each `input` checkbox tag:
   * if the checkbox is checked, you must store the Amenity ID in a variable (dictionary or list)
   * if the checkbox is unchecked, you must remove the Amenity ID from the variable
   * update the `h4` tag inside the `div` Amenities with the list of Amenities checked

As example:

![8e3c27078d62806b8ad1c1a682fbb3a48636ab89](https://github.com/elyse502/AirBnB_clone_v4/assets/125453474/806c3299-2b37-4bc9-8598-08276e21f904)
![4e5cecdd82a70f07cd283ef8e242ad325c95b564](https://github.com/elyse502/AirBnB_clone_v4/assets/125453474/49ad59c7-aa08-4b38-ad01-76908b513450)
![fb54e3081e229654db6e71ba919db753a791dcc3](https://github.com/elyse502/AirBnB_clone_v4/assets/125453474/e335bc44-6cad-494b-8662-ef92099bfdca)

## 3. API status: [api/v1/app.py](https://github.com/elyse502/AirBnB_clone_v4/blob/master/api/v1/app.py), [web_dynamic/2-hbnb.py](https://github.com/elyse502/AirBnB_clone_v4/blob/master/web_dynamic/2-hbnb.py), [web_dynamic/templates/2-hbnb.html](https://github.com/elyse502/AirBnB_clone_v4/blob/master/web_dynamic/templates/2-hbnb.html), [web_dynamic/static/styles/3-header.css](https://github.com/elyse502/AirBnB_clone_v4/blob/master/web_dynamic/static/styles/3-header.css), [web_dynamic/static/scripts/2-hbnb.js](https://github.com/elyse502/AirBnB_clone_v4/blob/master/web_dynamic/static/scripts/2-hbnb.js)
Before requesting the HBNB API, it’s better to know the status of this one.

Update the API entry point (`api/v1/app.py`) by replacing the current `CORS CORS(app, origins="0.0.0.0"`) by `CORS(app, resources={r"/api/v1/*": {"origins": "*"}})`.

Change the route `1-hbnb` to `2-hbnb` in the file `2-hbnb.py` (based on `1-hbnb.py`)

Create a new template `2-hbnb.html` (based on `1-hbnb.html`) and update it:
* Import the JavaScript `static/scripts/2-hbnb.js` in the `<head>` tag (instead of `1-hbnb.js`)
* Add a new `div` element in the `header` tag:
   * Attribute ID should be `api_status`
   * Align to the right
   * Circle of 40px diameter
   * Center vertically
   * At 30px of the right border
   * Background color #cccccc
* Also add a class `available` for this new element in `web_dynamic/static/styles/3-header.css`:
   * Background color #ff545f

Write a JavaScript script (`static/scripts/2-hbnb.js`):
* Based on `1-hbnb.js`
* Request `http://0.0.0.0:5001/api/v1/status/`:
   * If in the status is “OK”, add the class `available` to the `div#api_status`
   * Otherwise, remove the class `available` to the `div#api_status`

To start the API in the port 5001:
```groovy
guillaume@ubuntu:~/AirBnB_v4$ HBNB_MYSQL_USER=hbnb_dev HBNB_MYSQL_PWD=hbnb_dev_pwd HBNB_MYSQL_HOST=localhost HBNB_MYSQL_DB=hbnb_dev_db HBNB_TYPE_STORAGE=db HBNB_API_PORT=5001 python3 -m api.v1.app
...
```

![b68cd1e385963da099899f51ee5f3a6bbf0adcb3](https://github.com/elyse502/AirBnB_clone_v4/assets/125453474/0635ec85-68ef-4d3c-a625-a243e9c01e53)
![62fbb2d674fca4a843458e61cf3b05ee9f68ad04](https://github.com/elyse502/AirBnB_clone_v4/assets/125453474/5fa02094-22da-43f7-8a41-0943e9c0e632)

## 4. Fetch places: [web_dynamic/3-hbnb.py](https://github.com/elyse502/AirBnB_clone_v4/blob/master/web_dynamic/3-hbnb.py), [web_dynamic/templates/3-hbnb.html](https://github.com/elyse502/AirBnB_clone_v4/blob/master/web_dynamic/templates/3-hbnb.html), [web_dynamic/static/scripts/3-hbnb.js](https://github.com/elyse502/AirBnB_clone_v4/blob/master/web_dynamic/static/scripts/3-hbnb.js)
Replace the route `2-hbnb` with `3-hbnb` in the file `3-hbnb.py` (based on `2-hbnb.py`)

Create a new template `3-hbnb.html` (based on `2-hbnb.html`) and update it:
* Import the JavaScript `static/scripts/3-hbnb.js` in the `<head>` tag (instead of `2-hbnb.js`)
* Remove the entire Jinja section of displaying all places (all `article` tags)

Write a JavaScript script (`static/scripts/3-hbnb.js`):
* Based on `2-hbnb.js`
* Request `http://0.0.0.0:5001/api/v1/places_search/`:
   * Description of this endpoint [here](https://github.com/elyse502/AirBnB_clone_v3/blob/master/api/v1/views/places.py). **If this endpoint is not available, you will have to add it to the API** (you can work all together for creating this endpoint)
   * Send a `POST` request with `Content-Type: application/json` and an empty dictionary in the body - cURL version: `curl "http://0.0.0.0:5001/api/v1/places_search" -XPOST -H "Content-Type: application/json" -d '{}'`
   * Loop into the result of the request and create an `article` tag representing a `Place` in the `section.places`. (you can remove the Owner tag in the place description)

The final result must be the same as previously, but now, places are loaded from the front-end, not from the back-end!

## 5. Filter places by Amenity: [web_dynamic/4-hbnb.py](https://github.com/elyse502/AirBnB_clone_v4/blob/master/web_dynamic/4-hbnb.py), [web_dynamic/templates/4-hbnb.html](https://github.com/elyse502/AirBnB_clone_v4/blob/master/web_dynamic/templates/4-hbnb.html), [web_dynamic/static/scripts/4-hbnb.js](https://github.com/elyse502/AirBnB_clone_v4/blob/master/web_dynamic/static/scripts/4-hbnb.js)
Replace the route `3-hbnb` with `4-hbnb` in the file `4-hbnb.py` (based on `3-hbnb.py`)

Create a new template `4-hbnb.html` (based on `3-hbnb.html`) and update it:
* Import the JavaScript `static/scripts/4-hbnb.js` in the `<head>` tag (instead of `3-hbnb.js`)

Write a JavaScript script (`static/scripts/4-hbnb.js`):
* Based on `3-hbnb.js`
* When the `button` tag is clicked, a new POST request to `places_search` should be made with the list of Amenities checked

Now you have the first filter implemented, enjoy!

## 6. States and Cities: [web_dynamic/100-hbnb.py](https://github.com/elyse502/AirBnB_clone_v4/blob/master/web_dynamic/100-hbnb.py), [web_dynamic/templates/100-hbnb.html](https://github.com/elyse502/AirBnB_clone_v4/blob/master/web_dynamic/templates/100-hbnb.html), [web_dynamic/static/scripts/100-hbnb.js](https://github.com/elyse502/AirBnB_clone_v4/blob/master/web_dynamic/static/scripts/100-hbnb.js)
Now, reproduce the same steps with the State and City filter:

Replace the route `4-hbnb` to `100-hbnb` in the file `100-hbnb.py` (based on `4-hbnb.py`)

Create a new template `100-hbnb.html` (based on `4-hbnb.html`) and update it:
* Import the JavaScript `static/scripts/100-hbnb.js` in the `<head>` tag (instead of `4-hbnb.js`)
* Add to all `li` tags of each state a new tag: `<input type="checkbox">`
* Add to all `li` tags of each cities a new tag: `<input type="checkbox">`
* The new checkbox must be at 10px on the left of the State or City name
* Add to all `input` tags of each states (`<li>` tag) the attribute `data-id=":state_id"`
* Add to all `input` tags of each states (`<li>` tag) the attribute `data-name=":state_name"`
* Add to all `input` tags of each cities (`<li>` tag) the attribute `data-id=":city_id"`
* Add to all `input` tags of each cities (`<li>` tag) the attribute `data-name=":city_name"`

Write a JavaScript script (`static/scripts/100-hbnb.js`):
* Based on `4-hbnb.js`
   * Listen to changes on each `input` checkbox tag:
   * if the checkbox is checked, you must store the State or City ID in a variable (dictionary or list)
   * if the checkbox is unchecked, you must remove the State or City ID from the variable
   * update the `h4` tag inside the `div` Locations with the list of States or Cities checked
* When the `button` tag is clicked, a new POST request to `places_search` should be made with the list of Amenities, Cities and States checked

## 7. Reviews: [web_dynamic/101-hbnb.py](https://github.com/elyse502/AirBnB_clone_v4/blob/master/web_dynamic/101-hbnb.py), [web_dynamic/templates/101-hbnb.html](https://github.com/elyse502/AirBnB_clone_v4/blob/master/web_dynamic/templates/101-hbnb.html), [web_dynamic/static/scripts/101-hbnb.js](https://github.com/elyse502/AirBnB_clone_v4/blob/master/web_dynamic/static/scripts/101-hbnb.js)
Let’s add a new feature: show and hide reviews!

Replace the route `100-hbnb` to `101-hbnb `in the file `101-hbnb.py` (based on `100-hbnb.py`)

Create a new template `101-hbnb.html` (based on `100-hbnb.html`) and update it:
* Import the JavaScript `static/scripts/101-hbnb.js` in the `<head>` tag (instead of `101-hbnb.js`)
* Design the list of reviews from this [task 9. Full details](https://github.com/elyse502/AirBnB_clone/tree/master/web_static)
* Add a `span` element at the right of the `H2` “Reviews” with value “show” (add all necessary attributes to do this feature)

Write a JavaScript script (`static/scripts/101-hbnb.js`):
* Based on `100-hbnb.js`
* When the `span` next to the Reviews `h2` is clicked by the user:
   * Fetch, parse, display reviews and change the text to “hide”
   * If the text is “hide”: remove all Review elements from the DOM
   * This button should work like a toggle to fetch/display and hide reviews


