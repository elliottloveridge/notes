# 🔀 Switch Statements in Python

## 🧠 What Is a Switch Statement?
- A switch statement is a control flow structure used to execute different blocks of code based on the value of a variable
- Common in languages like C, Java, and JavaScript
- Python does not have a built-in `switch` statement, but similar behaviour can be achieved using `match` (introduced in Python 3.10), `if-elif-else`, or dictionaries
## 🆕 Using `match` in Python 3.10+
- Python 3.10 introduced **structural pattern matching** using the `match` keyword
- This allows for more readable and expressive branching logic

```python
def http_status(code):
    match code:
        case 200:
            return "OK"
        case 404:
            return "Not Found"
        case 500:
            return "Server Error"
        case _:
            return "Unknown status"
```
- `case _` acts like a default or fallback case
## 🧱 Using Dictionaries as Switch Alternatives
- Before Python 3.10, dictionaries were commonly used to simulate switch behaviour
- It's hard to make a switch statement in Python
	- Python's equivalent would be dictionary mapping and if/else chains
- They don't do one thing, by their nature they always do $N$ things
### More on Switch Statements in Python
- It is hard to avoid switch statements, but we can make sure that each switch statement is buried in a low-level class and is never repeated by using polymorphism
```python
class InvalidEmployeeType(Exception):
    pass

def calculate_pay(employee):
    pay_calculators = {
        'COMMISSIONED': calculate_commissioned_pay,
        'HOURLY': calculate_hourly_pay,
        'SALARIED': calculate_salaried_pay
    }

    try:
        return pay_calculators[employee.type]
    except KeyError:
        raise InvalidEmployeeType(employee.type)
```
- What's wrong with the above example?
	1. It’s large, and when new employee types are added, it will grow
	2. It very clearly does more than one thing
	3. It violates the Single Responsibility Principle (SRP) because there is more than one reason for it to change
	4. It violates the Open Closed Principle (OCP) because it must change whenever new types are added
	5. There are an unlimited number of other functions that will have the same structure
		1. For example you may need an `is_payday` function, or a `send_pay` function, all with a similar format
- The final point is the **worst** problem with it
	- The solution to this problem is to bury the 'switch' statement within an abstract factory
___
- The general rule for switch statements is that they can be tolerated if they;
	- Appear only once
	- Are used to create polymorphic objects
	- Are hidden behind an inheritance relationship so that the rest of the system can’t see them
```python
class InvalidEmployeeType(Exception):
    pass

class EmployeeFactory:
    employee_classes = {
        'COMMISSIONED': CommissionedEmployee,
        'HOURLY': HourlyEmployee,
        'SALARIED': SalariedEmployee
    }

    @classmethod
    def make_employee(cls, record):
        try:
            return cls.employee_classes[record.type]
        except KeyError:
            raise InvalidEmployeeType(f"Invalid employee type: {record.type}")
```
- For the above you would then define separate Employee derived classes where you implement the interface of the abstract Employee class
