#0x01. Fix my code

##Task 0. Server status

Explanation
Blueprint Setup: In api/v1/views/__init__.py, the app_views blueprint is created and the route is defined in api/v1/views/index.py.
Register Blueprint: In app.py, the blueprint app_views is registered with the Flask application with a URL prefix /api/v1. This means that your route /status will be accessible at /api/v1/status.
Running the App: The Flask app is configured to run on host 0.0.0.0 and port 5000.

###requirements: Flask==2.1.1

Running the Application:

Install Dependencies:
pip install -r requirements.txt

Run the Application:

python3 app.py

Test the Endpoint:

Navigate to http://0.0.0.0:5000/api/v1/status in your web browser or use a tool like curl:

curl http://0.0.0.0:5000/api/v1/status

You should receive the JSON response:
{"status": "OK"}

##Task 1. My square

My corrections have significantly improved the code by following Python conventions and making the class more understandable. Below, I will explain the changes made and the reasons behind them:

Class Name Capitalization:

Original: class square():
Correction: class Square():
Explanation: In Python, class names are conventionally written in CamelCase. This improves readability and follows the PEP 8 style guide.
Docstrings:

Original: No docstrings were provided for the class and methods.
Correction: Added docstrings to the class and its methods.
Explanation: Docstrings provide a description of the class and methods, which helps in understanding the code and its purpose.
Width and Height Attributes:

Original: The width and height attributes were set as class attributes.
Correction: They remain as class attributes but are instantiated with values from kwargs.
Explanation: It's important to document the purpose of these attributes.
Method Naming:

Original: Method names did not follow Python's naming conventions (area_of_my_square is fine, but PermiterOfMySquare should be permiter_of_my_square).
Correction: Renamed PermiterOfMySquare to permiter_of_my_square.
Explanation: Method names in Python should be written in snake_case as per PEP 8.
Calculation of Area:

Original: return self.width * self.width
Correction: return self.width * self.height
Explanation: For a square, both width and height should be the same, but since the object allows different values, it should calculate the area as width * height.
Perimeter Calculation:

Original: The perimeter method was named incorrectly (PermiterOfMySquare).
Correction: Renamed to permiter_of_my_square and added a docstring.
Explanation: Correct naming and documentation improve code readability.
String Representation:

Original: The __str__ method correctly formats the width and height.
Correction: Added a docstring.
Explanation: Documentation helps in understanding what the method does.
Module Docstring:

Original: None.
Correction: Added a module-level docstring.
Explanation: It is good practice to include a docstring at the top of the module explaining its purpose.

Summary of Changes
Capitalized Class Name: Square instead of square.
Added Docstrings: For the class, methods, and module.
Renamed Method: PermiterOfMySquare to permiter_of_my_square.
Corrected Area Calculation: Used width * height instead of width * width.
Corrected Method Names to Follow PEP 8: Used snake_case for method names.
Maintained String Representation: Added a docstring for the __str__ method.

These changes adhere to Python's conventions and improve the readability and maintainability of the code.

## Task 2. Step 2: User model

Your corrections to the User class in Python improve the original script by ensuring that the property decorator for email is properly defined. Below is an explanation of the changes and the overall structure of the corrected script.

Original Script:
The original script contains the following issues:

Incorrect Order of Decorators: The @property and @setter decorators are not in the correct order.
Decorator Usage: The @setter decorator is defined before the @property decorator, which will cause an error.

Corrected Script

Here is the corrected script with explanations:

#!/usr/bin/python3
""" 
User class
"""

class User():
    """ Documentation """

    def __init__(self):
        """ Documentation """
        self.__email = None

    @property
    def email(self):
        """ Documentation """
        return self.__email

    @email.setter
    def email(self, value):
        """ Documentation """
        if type(value) is not str:
            raise TypeError("email must be a string")
        self.__email = value

if __name__ == "__main__":

    u = User()
    u.email = "john@snow.com"
    print(u.email)

Explanation of Changes
Order of Decorators:

Original: The @setter decorator for email is placed before the @property decorator.
Correction: The @property decorator for email is placed before the @setter decorator. This ensures that the email property is correctly recognized and the setter method can be used to set its value.
Code Structure:

The User class is defined with a private attribute __email initialized to None.
The @property decorator for email allows retrieving the value of __email.
The @setter decorator for email allows setting the value of __email with type checking to ensure it is a string.

Detailed Explanation of the Script

Class Definition and Constructor:

The User class is defined with an __init__ method to initialize the private attribute __email.

class User():
    """ Documentation """

    def __init__(self):
        """ Documentation """
        self.__email = None

Property Method:

The @property decorator allows the email attribute to be accessed like a regular attribute while still using the getter method.

@property
def email(self):
    """ Documentation """
    return self.__email

Setter Method:

The @setter decorator defines the email setter method, allowing the email attribute to be set with type validation.

@email.setter
def email(self, value):
    """ Documentation """
    if type(value) is not str:
        raise TypeError("email must be a string")
    self.__email = value

Main Execution Block:

An instance of the User class is created.
The email attribute is set to "john@snow.com".
The email attribute is printed.

if __name__ == "__main__":
    u = User()
    u.email = "john@snow.com"
    print(u.email)

Summary
Your corrections ensure that the @property decorator for email is defined before the @setter decorator, allowing the script to function correctly. The corrected script follows proper Python conventions and allows for safe and controlled access to the email attribute with validation.
