# How to use @property decorator

The @property decorator in Python is used to define getter methods in a class, allowing you to access a method as if it were an attribute. It provides a clean and Pythonic way to manage attribute access, while still allowing you to control how attributes are calculated or validated.
```python
class Circle:
    def __init__(self, radius):
        self._radius = radius  # Private attribute to store radius

    @property
    def radius(self):
        """Getter for radius."""
        return self._radius

    @radius.setter
    def radius(self, value):
        """Setter for radius with validation."""
        if value < 0:
            raise ValueError("Radius cannot be negative.")
        self._radius = value

    @property
    def area(self):
        """Calculate the area dynamically."""
        return 3.14159 * self._radius ** 2

# Example usage
c = Circle(5)
print(c.radius)  # Accessing the radius as an attribute
print(c.area)    # Accessing the calculated area as an attribute
c.radius = 10    # Modifying the radius
print(c.area)    # The area is updated dynamically
