# Book 1 Workflows

 ## Book 1 Chapter 3: get animals, employees & locations

File and dir prep
1. create locations directory
1. create __init__.py in locations directory
1. create request.py file
1. populate request.py with LOCATIONS lists
1. write defs for all and single locations in request.py
1. add import statement to __init__.py file [from .request import get_all_locations, get_single_location]

Add logic to request_handler.py
1. update request_handler.py - import get_all_locations, get_single_location
1. update do_GET functiomn with if/else logic for locations path

Test new path added to do_GET in postman


## Book 1 Chapter 4: add animals
1. import json into top request_handler.py
1. Review do_POST
1. implement create_animal function
1. In animals/__init__.py, import the create function.
1. In the main module, add create_animal to the list of functions being imported from the animals package.
1. Test in Postman

## add locations
1. refactor the new_animal var to be new_resource still = None
1. move the self.wfile.write below the if, only one response line is needed.
1. add elif for location and call create_location
1. Update the do_POST method in the main module to handle requests to the /locations path.
1. add new function to locations/__init__
1. add new create_location to the request.py import at the top from locations
1. Write a create_location function in the locations/request.py module that appends a new location dictionary to the list.

## add customers
1. Required to create customers from the ground up so dirs
1. create customers dir
1. create __init__.py file
1. create request.py file
1. add elif for customers and call create_customers
1. add the CUSTOMERS list data 
1. add create_customer into customers/request.py
1. update customers/__init__.py [from request import function name statemnet]
1. update request_handler.py import statement at top of file [from customers import create_customer]

## Book 1 - Chapter 5 DELETE ops - Animals
1. update request_handler.py w/ do_DELETE
1. add delete_animal(id) to animals/request.py
1. Import delete_animal function into animals/__init__.py
1. Import delete_animal from the package into request_handler.py  
note: ImportError: cannot import name 'delete_animal' from 'animals.request' (/Users/davidb/workspace/python-server/animals/request.py)
The import was not picked up automatically for some reason even with multiple saves. Had to redo and resave.

## Book 1 - Chapter 5 DELETE ops - Locations
1. update request_handler.py do_DELETE function wtih additional logic for the "locations" resource
 - elif resource == "locations" then call delete_location(id)
1. update animals/request.py with delete_location function
1. Import delete_location function into locations/__init__.py
1. Import delete_location from the package into request_handler.py
1. Test in POSTMAN


## Book 1 - Chapter 6 Update Ops - Animals
1. Add "Status" key to the ANIMALS list
1. add/update do_PUT method in request_handler.py
1. add update_animal function to the animals/request.py module
1. Import update_animal function into the animals/__init__.py module
1. import update_animal into the request_handler.py module.
1. test in POSTMAN with data from the request.py
- note: POSTMAN body content can fail to parse due to minor differences in format. ' vs " and True vs true

## Book 1 - Chapter 9
1. Import json, and sqlite3 into the animals/request.py
1. Import the corresponding class for the resource [from models import Animal]
1. Write SQL statements to get all database rows for the get_all_* functions.
1. Write SQL statements with a WHERE clause to get a single database row for the get_single_* functions.
1. Request all resources with the Postman client and verify that all GET requests return the correct JSON representations.

## Book 1 - Chapter 10 - filter & query params
1. Update the parse_url() method in request_handler.py  - book 1 - chapter 10
 - includes new parse logic to detect query string params
1. Update the parse_url() do_GET method in request_handler.py
1. Update the do_GET() method in request_handler.py - book 1 - chapter 10
 - determine resource,key and value and add elif statement to do new function call
1. Update the models/customer.py model to implement default parameter values (Only needed for employees, not for practice)
1. Update customers/request.py with new method get_customers_by_email(email)
1. Update the customers/__init__.py to import new function get_customers_by_email
1. Update request_handler.py to import new function: get_customers_by_email
1. request_handler.py response = get_customers_by_email(value) to response = f"{get_customers_by_email(value)}"
1. Test in POSTMAN w/ http://localhost:8088/customers?email=jenna@solis.com

## Book 1 - Chapter 11 - Delete by id
1. Update animals/request.py with the delete_animal() function
1. Update the animals/__init__.py to import new function delete_animal()
1. Update request_handler.py to import new function: delete_animal()
1. Test in Postman: GET all animals, note last id
1. From the Postman client, perform a DELETE request to http://localhost:8088/animals/5
1. Then request all animals again with a GET request to http://localhost:8088/animals
1. Verify that the animal with an id of 5 is not in the response and got deleted from the database.
1. If deleted record is needed - write INSERT INTO statement to add back deleted record
- INSERT INTO `Animal` VALUES (null, "Daps", "Kennel", "Boxer", 2, 2);

## Book1 - Chapter 13 - Update Animal Records
1. Update animals/request.py with refactored update_animal function
1. Update request_handler.py do_PUT method
 - add new var named success and init to False
 - update resource outcomes so return of update animal is stored in the sucess var
 - Note: The remaining update_* functions do not return values but I went ahead and updated the function calls to store their return values in the sucess var. This was done with the expectation that the the remaining update functions will be refactored to return true/false return values.




# Book 1 Col-2 Daily Journal Workflows

## Daily Journal - Chapter 8

1. Create a new sub-directory in your ~/workspace directory for this project. A good name would be daily-journal-server
1. In your project directory, create a dailyjournal.db file to be your database
1. Use the CREATE TABLE statement to define all of your tables. Also make sure you set up the foreign key constraints where needed
1. Write INSERT INTO statements for all of the moods that you want to support in the Moods table
1. Write INSERT INTO journal entries in the JournalEntries table
1. Create the database connection, name it and point it to the .dailyjournal.db file created in step 2
1. Create a request_handler.py file in your Python project directory.
1. Create an entries package directory and its corresponding __init__.py file.
1. Create a request.py file in the entries directory
1. create a models directory
1. create __init__.py file in the models directory
1. create the entry.py file
1. add class Entry(): def to the model/entry.py file - reference erd for properties
1. For now, copy pasta the request_handler.py code from the Kennel application that your instructor is walking you through.
  - update request_handler.py: implement parse_url method in HandleRequests #book-1 chapter-3
  - note: the do_GET method self.path == "" logic will need to be modified to search for entries and invoke the get_all_entries method
1. Have your server listen for the http://localhost:8088/entries URL
1. Write a get_all_entries() function in the entries request module and write the SQL to get all records from the Entries table.
1. Test in Postman: Ensure the entries resource returns all records from database as JSON representations.




