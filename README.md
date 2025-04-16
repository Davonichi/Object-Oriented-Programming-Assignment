# Object-Oriented-Programming-Assignment
Assignment 1: Design Your Own Class! 🏗️
Create a class representing anything you like (a Smartphone, Book, or even a Superhero!).
Add attributes and methods to bring the class to life!
Use constructors to initialize each object with unique values.
Add an inheritance layer to explore polymorphism or encapsulation.


# Base class
class Smartphone:
    def __init__(self, brand, model, storage, battery_life):
        self.brand = brand
        self.model = model
        self.__storage = storage  # Encapsulated
        self.battery_life = battery_life

    def get_storage(self):  # Getter method for encapsulation
        return self.__storage

    def set_storage(self, new_storage):  # Setter method with a condition
        if new_storage > 0:
            self.__storage = new_storage
        else:
            print("Storage must be a positive value.")

    def make_call(self, contact):
        print(f"{self.brand} {self.model} is calling {contact}...")

    def take_photo(self):
        print(f"{self.brand} {self.model} is taking a photo!")

    def __str__(self):
        return f"{self.brand} {self.model} with {self.__storage}GB storage and {self.battery_life}h battery"


# Subclass
class GamingPhone(Smartphone):
    def __init__(self, brand, model, storage, battery_life, gpu_model):
        super().__init__(brand, model, storage, battery_life)
        self.gpu_model = gpu_model

    def play_game(self, game):
        print(f"Playing '{game}' on {self.brand} {self.model} with {self.gpu_model} GPU!")

    # Polymorphism: override take_photo()
    def take_photo(self):
        print(f"{self.brand} {self.model} takes a high-res gaming photo!")

    def __str__(self):
        return super().__str__() + f" and {self.gpu_model} GPU"


# Create instances
phone1 = Smartphone("Samsung", "Galaxy S21", 128, 24)
gaming_phone = GamingPhone("ASUS", "ROG Phone 5", 256, 30, "Adreno 660")

# Using methods
print(phone1)
phone1.make_call("Alice")
phone1.take_photo()

print("\n--- Gaming Phone ---")
print(gaming_phone)
gaming_phone.make_call("Bob")
gaming_phone.take_photo()
gaming_phone.play_game("Asphalt 9")


Activity 2: Polymorphism Challenge! 🎭

Create a program that includes animals or vehicles with the same action (like move()). However, make each class define move() differently (for example, Car.move() prints "Driving" 🚗, while Plane.move() prints "Flying" ✈️).


# Base class (optional in this case)
class Vehicle:
    def move(self):
        pass  # This can be overridden by each subclass


# Subclasses with their own move() implementations
class Car:
    def move(self):
        print("Driving on the road 🚗")


class Plane:
    def move(self):
        print("Flying in the sky ✈️")


class Boat:
    def move(self):
        print("Sailing across the water 🚤")


# List of vehicles
vehicles = [Car(), Plane(), Boat()]

# Demonstrate polymorphism
for v in vehicles:
    v.move()
