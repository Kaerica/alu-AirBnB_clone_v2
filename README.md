 alu-AirBnB_clone_v2
 AirBnB Clone - Command Line Interface

This project represents the foundational phase of developing an AirBnB website replica. The current implementation focuses on building a command-line interface that serves as the backend management system for handling application data. The interface provides comprehensive functionality for object manipulation including creation, modification, deletion, and persistent storage through JSON serialization.

Project Structure & Task Breakdown

| Task | File(s) | Purpose |
|------|---------|---------|
| 0: Documentation | AUTHORS | Contributor and project documentation |
| 1: Code Standards | All files | PEP8 compliance across codebase |
| 2: Testing Framework | /tests | Comprehensive unit testing for all modules |
| 3: Base Class Implementation | /models/base_model.py | Foundation class for inheritance hierarchy |
| 4: Instance Recreation | /models/base_model.py | Dictionary-to-object conversion functionality |
| 5: Storage System | /models/engine/file_storage.py, /models/__init__.py, /models/base_model.py | Persistent data management system |
| 6: Basic Console | console.py | Core console functionality with exit and input handling |
| 7: Enhanced Console | console.py | Full CRUD operations through console interface |
| 8: User Management | console.py, /models/engine/file_storage.py, /models/user.py | User class implementation |
| 9: Extended Models | /models/user.py, /models/place.py, /models/city.py, /models/amenity.py, /models/state.py, /models/review.py | Additional model classes |
| 10: Complete Integration | console.py, /models/engine/file_storage.py | Dynamic class handling and storage system |

## Getting Started

### Installation
Begin by cloning this repository to your local machine.

### Launching the Console
Navigate to the project directory and execute the console:

```bash
/AirBnB_clone$ ./console.py
```

Upon successful execution, you'll see the interactive prompt:
```
(hbnb)
```

This indicates you're now operating within the HBnB console environment.

## Available Operations

### Core Commands

**create** - Instantiates a new object of the specified class

**destroy** - Removes an object using class name and unique identifier

**show** - Displays object details using class name and UUID

**all** - Lists all stored objects or filters by class type

**update** - Modifies object attributes using class name and UUID

**quit** - Terminates the console session (Ctrl+D also works)

### Advanced Command Syntax

The console supports an object-oriented command format:

**Format:** `<class_name>.<method>([<id>[name_arg value_arg]|[kwargs]])`

Supported advanced operations:
- **all** - Retrieve all objects or filter by class
- **count** - Get total instances of a specific class
- **show** - Display specific object details
- **destroy** - Remove specific object
- **update** - Modify object attributes

## Usage Examples

### Standard Command Format

#### Creating Objects
**Syntax:** `create <class_name>`

```
(hbnb) create BaseModel
3aa5babc-efb6-4041-bfe9-3cc9727588f8
(hbnb)
```

#### Displaying Objects
**Syntax:** `show <class_name> <object_id>`

```
(hbnb) show BaseModel 3aa5babc-efb6-4041-bfe9-3cc9727588f8
[BaseModel] (3aa5babc-efb6-4041-bfe9-3cc9727588f8) {'id': '3aa5babc-efb6-4041-bfe9-3cc9727588f8', 'created_at': datetime.datetime(2020, 2, 18, 14, 21, 12, 96959), 'updated_at': datetime.datetime(2020, 2, 18, 14, 21, 12, 96971)}
(hbnb)
```

#### Removing Objects
**Syntax:** `destroy <class_name> <object_id>`

```
(hbnb) destroy BaseModel 3aa5babc-efb6-4041-bfe9-3cc9727588f8
(hbnb) show BaseModel 3aa5babc-efb6-4041-bfe9-3cc9727588f8
** no instance found **
(hbnb)
```

#### Modifying Objects
**Syntax:** `update <class_name> <object_id> <attribute> <value>`

```
(hbnb) update BaseModel b405fc64-9724-498f-b405-e4071c3d857f first_name "person"
(hbnb) show BaseModel b405fc64-9724-498f-b405-e4071c3d857f
[BaseModel] (b405fc64-9724-498f-b405-e4071c3d857f) {'id': 'b405fc64-9724-498f-b405-e4071c3d857f', 'created_at': datetime.datetime(2020, 2, 18, 14, 33, 45, 729889), 'updated_at': datetime.datetime(2020, 2, 18, 14, 33, 45, 729907), 'first_name': 'person'}
(hbnb)
```

### Object-Oriented Command Format

#### Listing All Objects by Class
**Syntax:** `<class_name>.all()`

```
(hbnb) User.all()
["[User] (99f45908-1d17-46d1-9dd2-b7571128115b) {'updated_at': datetime.datetime(2020, 2, 19, 21, 47, 34, 92071), 'id': '99f45908-1d17-46d1-9dd2-b7571128115b', 'created_at': datetime.datetime(2020, 2, 19, 21, 47, 34, 92056)}", "[User] (98bea5de-9cb0-4d78-8a9d-c4de03521c30) {'updated_at': datetime.datetime(2020, 2, 19, 21, 47, 29, 134362), 'id': '98bea5de-9cb0-4d78-8a9d-c4de03521c30', 'created_at': datetime.datetime(2020, 2, 19, 21, 47, 29, 134343)}"]
```

#### Deleting with Method Syntax
**Syntax:** `<class_name>.destroy(<object_id>)`

```
(hbnb) User.destroy("99f45908-1d17-46d1-9dd2-b7571128115b")
(hbnb) User.all()
["[User] (98bea5de-9cb0-4d78-8a9d-c4de03521c30) {'updated_at': datetime.datetime(2020, 2, 19, 21, 47, 29, 134362), 'id': '98bea5de-9cb0-4d78-8a9d-c4de03521c30', 'created_at': datetime.datetime(2020, 2, 19, 21, 47, 29, 134343)}"]
```

#### Single Attribute Updates
**Syntax:** `<class_name>.update(<object_id>, <attribute>, <value>)`

```
(hbnb) User.update("98bea5de-9cb0-4d78-8a9d-c4de03521c30", name "Todd the Toad")
(hbnb) User.all()
["[User] (98bea5de-9cb0-4d78-8a9d-c4de03521c30) {'updated_at': datetime.datetime(2020, 2, 19, 21, 47, 29, 134362), 'id': '98bea5de-9cb0-4d78-8a9d-c4de03521c30', 'name': 'Todd the Toad', 'created_at': datetime.datetime(2020, 2, 19, 21, 47, 29, 134343)}"]
```

#### Bulk Updates with Dictionary
**Syntax:** `<class_name>.update(<object_id>, <dictionary>)`

```
(hbnb) User.update("98bea5de-9cb0-4d78-8a9d-c4de03521c30", {'name': 'Fred the Frog', 'age': 9})
(hbnb) User.all()
["[User] (98bea5de-9cb0-4d78-8a9d-c4de03521c30) {'updated_at': datetime.datetime(2020, 2, 19, 21, 47, 29, 134362), 'name': 'Fred the Frog', 'age': 9, 'id': '98bea5de-9cb0-4d78-8a9d-c4de03521c30', 'created_at': datetime.datetime(2020, 2, 19, 21, 47, 29, 134343)}"]
```
