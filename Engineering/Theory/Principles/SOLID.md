# SOLID Principles
## Class Design
- The first five principles of class design are defined below:

| Acronym | Principle Name                      | Description                                                           |
| ------- | ----------------------------------- | --------------------------------------------------------------------- |
| SRP     | The Single Responsibility Principle | A class should have one, and only one, reason to change               |
| OCP     | The Open Closed Principle           | You should be able to extend a class' behaviour, without modifying it |
| LSP     | The Liskov Substitution Principle   | Derived classes must be substitutable for their base classes          |
| ISP     | The Interface Segregation Principle | Make fine-grained interfaces that are client-specific                 |
| DIP     | The Dependency Inversion Principle  | Depend on abstractions, not on concretions                            |
### 1. Single Responsibility Principle (SRP)
	A class should have one, and only one, reason to change

- **Focus**: Each class should handle one aspect of the functionality
	- If you find that a class is handling multiple responsibilities, it might be a sign that it needs to be split into smaller classes
- **Cohesion**: The methods and properties of the class should be closely related to each other
	- High cohesion within a class indicates that it has a well-defined responsibility
- **Change Impact**: Consider the reasons why the class might need to change
	- If a class has multiple reasons to change, it should be divided so that each new class has only one reason to change
#### Example
```python
class Invoice:
    def __init__(self, amount):
        self.amount = amount

    def calculate_total(self):
        return self.amount * 1.2  # Assuming 20% tax

class InvoicePrinter:
    def print_invoice(self, invoice):
        print(f"Invoice amount: {invoice.calculate_total()}")

# Usage
invoice = Invoice(100)
printer = InvoicePrinter()
printer.print_invoice(invoice)
```
- In the above example, the `Invoice` class is responsible only for handling invoice data and calculations, while the `InvoicePrinter` class is responsible for printing the invoice
	- This separation ensures each class has a single responsibility
- A better example may be if you had a User class that was handling authentication, data access, and notifications
	- In this case it would be better to separate these into separate classes: `UserAuth`, etc.
### 2. Open/Closed Principle (OCP)
	Software entities (classes, modules, functions, etc.) should be open for extension but closed for modification

- **Extension**: You should be able to add new functionality to a class without changing its existing code
- **Benefits**: This promotes code reusability and reduces the risk of introducing bugs when adding new features
#### Example
```python
class Discount:
    def apply(self, amount):
        return amount

class TenPercentDiscount(Discount):
    def apply(self, amount):
        return amount * 0.9

class Invoice:
    def __init__(self, amount, discount):
        self.amount = amount
        self.discount = discount

    def calculate_total(self):
        return self.discount.apply(self.amount) * 1.2  # Assuming 20% tax

# Usage
discount = TenPercentDiscount()
invoice = Invoice(100, discount)
print(invoice.calculate_total())
```
- Here, the `Discount` class can be extended with different discount strategies without modifying the `Invoice` class
### 3. Liskov Substitution Principle (LSP)
	Objects of a superclass should be replaceable with objects of a subclass without affecting the correctness of the program

- **Substitutability**: Derived classes must fully implement the behaviour expected by the base class
- **Benefits**: This ensures that a subclass can stand in for its superclass without causing errors or unexpected behaviour
#### Example
```python
class Bird:
    def fly(self):
        pass

class Sparrow(Bird):
    def fly(self):
        print("Sparrow flying")

class Ostrich(Bird):
    def fly(self):
        raise NotImplementedError("Ostriches can't fly")

def make_bird_fly(bird):
    bird.fly()

# Usage
sparrow = Sparrow()
make_bird_fly(sparrow)

ostrich = Ostrich()
make_bird_fly(ostrich)  # This will raise an error
```
- In this example, `Ostrich` violates the Liskov Substitution Principle because it cannot be substituted for `Bird` without causing errors. A better design would avoid using `fly` for `Ostrich`.
### 4. Interface Segregation Principle (ISP)
	Clients should not be forced to depend on interfaces they do not use

- **Fine-Grained Interfaces**: Create smaller, more specific interfaces rather than large, general-purpose ones
- **Benefits**: This reduces the impact of changes and makes the system more flexible and easier to maintain
#### Example
```python
class Printer:
    def print(self, document):
        pass

class Scanner:
    def scan(self):
        pass

class MultiFunctionPrinter(Printer, Scanner):
    def print(self, document):
        print(f"Printing: {document}")

    def scan(self):
        print("Scanning document")

# Usage
mfp = MultiFunctionPrinter()
mfp.print("My Document")
mfp.scan()
```
- Here, `Printer` and `Scanner` are fine-grained interfaces, and `MultiFunctionPrinter` implements both
	- This way, clients can depend on the specific interface they need
### 5. Dependency Inversion Principle (DIP)
	High-level modules should not depend on low-level modules. Both should depend on abstractions
	Abstractions should not depend on details. Details should depend on abstractions

- **Abstractions**: Depend on interfaces or abstract classes rather than concrete implementations
- **Benefits**: This decouples high-level and low-level components, making the system more modular and easier to change
#### Example
```python
from abc import ABC, abstractmethod

class PaymentProcessor(ABC):
    @abstractmethod
    def process_payment(self, amount):
        pass

class StripePaymentProcessor(PaymentProcessor):
    def process_payment(self, amount):
        print(f"Processing {amount} through Stripe")

class Invoice:
    def __init__(self, amount, payment_processor):
        self.amount = amount
        self.payment_processor = payment_processor

    def finalize(self):
        self.payment_processor.process_payment(self.amount)

# Usage
processor = StripePaymentProcessor()
invoice = Invoice(100, processor)
invoice.finalize()
```
- In this example, `Invoice` depends on the `PaymentProcessor` abstraction, not on a specific implementation like `StripePaymentProcessor`
	- This allows for easy substitution of different payment processors
## Package Design
- The next six principles are about packages
- In this context, a **package** refers to a **binary deliverable** rather than a namespace. Here's a breakdown:
	- **Binary Deliverable**: This is a compiled file that can be executed or used by other programs
	    - **.jar file**: Used in Java, it bundles compiled Java classes and associated resources (like text and images) into a single file
	    - **.dll file**: Used in Windows, it stands for Dynamic Link Library and contains code and data that can be used by multiple programs simultaneously
	- **Namespace**: This is a way to organize code and avoid naming conflicts. Examples include:
	    - **Java package**: A way to group related classes and interfaces in Java
	    - **C++ namespace**: A way to group related functions, classes, and variables in C++
	- In Python, you might be more familiar with packages as directories containing modules (Python files) and an `__init__.py` file
		- However, in this context, think of a package as a compiled, ready-to-use file that can be distributed and reused across different projects or systems
- The first three package principles are about package _cohesion_, they tell us what to put inside packages

| Acronym | Principle Name                          | Description                                          |
| ------- | --------------------------------------- | ---------------------------------------------------- |
| REP     | The Release Reuse Equivalency Principle | The granule of reuse is the granule of release       |
| CCP     | The Common Closure Principle            | Classes that change together are packaged together   |
| CRP     | The Common Reuse Principle              | Classes that are used together are packaged together |
- The last three principles are about the couplings between packages, and talk about metrics that evaluate the package structure of a system

| Acronym | Principle Name                     | Description                                          |
| ------- | ---------------------------------- | ---------------------------------------------------- |
| ADP     | The Acyclic Dependencies Principle | The dependency graph of packages must have no cycles |
| SDP     | The Stable Dependencies Principle  | Depend in the direction of stability                 |
| SAP     | The Stable Abstractions Principle  | Abstractness increases with stability                |
