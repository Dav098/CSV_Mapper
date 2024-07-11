# ObjectCSVMapper

ObjectCSVMapper is a Python utility for mapping objects to CSV format and vice versa. This utility provides functionality to serialize and deserialize Python objects, including handling complex types such as lists, sets, dictionaries, tuples, and custom objects.

## Features
Serialize objects to CSV: Convert Python objects to CSV format.
Deserialize CSV to objects: Convert CSV data back into Python objects.
Handle complex data types: Supports lists, sets, dictionaries, tuples, and custom object fields.
CSV file operations: Write objects to a CSV file and read objects from a CSV file.
## Usage
### Class Definitions
Define your classes to be used with the mapper.
```
class Person:
    def __init__(self, name, age, hobbies, favorite_books, contact_info, address):
        self.name = name
        self.age = age
        self.hobbies = hobbies
        self.favorite_books = favorite_books
        self.contact_info = contact_info
        self.address = address
        
class Address:
    def __init__(self, a_id, street, city):
        self.a_id = a_id
        self.street = street
        self.city = city
```

### Creating the Mapper
Create an instance of ObjectCSVMapper with the desired fields.
```
mapper = ObjectCSVMapper(["name", "age", "hobbies", "favorite_books", "contact_info", "address"])
```

### Writing Objects to CSV
Convert a list of objects to CSV format and write to a file.
```
people = [
    Person("John", 25, ["reading", "hiking"], {"fiction": "1984", "non-fiction": "The Art of Thinking Clearly"}, ("john@example.com", "555-1234"), Address("id_1", "Wall st.", "New York")),
    Person("Jane", 30, ["swimming", "dancing"], {"fiction": "Pride and Prejudice", "non-fiction": "Sapiens"}, ("jane@example.com", "555-5678"), Address("id_2", "Rodeo Drive", "Los Angeles")),
    Person("Bob", 40, ["gardening", "cooking"], {"fiction": "The Great Gatsby", "non-fiction": "Atomic Habits"}, ("bob@example.com", "555-9101"), Address("id_3", "Main st.", "Dallas")),
]

mapper.to_csv_file(people, "people.csv")
```

### Reading Objects from CSV
Read objects from a CSV file.
```
people_from_csv = mapper.from_csv_file("people.csv")
```

### Notes
* Ensure that the fields parameter in ObjectCSVMapper matches the attributes of the objects you are mapping.
* The to_csv and from_csv methods handle the conversion of complex data types.
* When linking custom objects (e.g., Address) within another object (e.g., Person), a unique identifier is used to facilitate correct mapping during deserialization.
* 
This example demonstrates the flexibility and utility of ObjectCSVMapper for handling complex object serialization and deserialization in Python.
