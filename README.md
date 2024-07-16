# Python
# The task involves selecting products from a list, adding them to a cart, and displaying the total price of the products in the cart.

# Task Description
# Define Product Class: Create a Product class with attributes like name, price, and stock.
# Define Cart Class: Create a Cart class that allows adding products, removing products, and calculating the total price.
# Main Program: Create a main program to interact with the user, allowing them to select products from a list, add them to the cart, and display the total price

# code:-
class Product:
    def __init__(self, name, price, stock):
        self.name = name
        self.price = price
        self.stock = stock
class Cart:
    def __init__(self):
        self.items = {}
    def add_product(self, product, quantity):
        if product.stock >= quantity:
            if product.name in self.items:
                self.items[product.name] += quantity
            else:
                self.items[product.name] = quantity
            product.stock -= quantity
            print(f"{quantity} {product.name} added to cart.")
        else:
            print(f"Not enough stock for {product.name}.")
    def remove_product(self, product, quantity):
        if product.name in self.items:
            if self.items[product.name] >= quantity:
                self.items[product.name] -= quantity
                product.stock += quantity
                print(f"{quantity} {product.name} removed from cart.")
            else:
                print(f"Only {self.items[product.name]} {product.name} in cart.")
        else:
            print(f"{product.name} is not in cart.")
    def get_total_price(self):
        total = 0
        for product_name, quantity in self.items.items():
            for product in products:
                if product.name == product_name:
                    total += product.price * quantity
                    break
        return total
# Sample
products = [
    Product("Onion", 1.00, 10),
    Product("Pea",0.20, 20),
    Product("Tamato", 2.00, 5),
    Product("Patato", 5.00, 15),
]
# Cart
cart = Cart()
# Loop
while True:
    print("\nChoose an option:")
    print("1. View products")
    print("2. Add product to cart")
    print("3. Remove product from cart")
    print("4. View cart total")
    print("5. Exit")
    choice = input("Enter your choice: ")
    if choice == '1':
        print("\nAvailable products:")
        for i, product in enumerate(products):
            print(f"{i+1}. {product.name} - ${product.price:.2f} (Stock: {product.stock})")
    elif choice == '2':
        product_index = int(input("Enter the product number to add: ")) - 1
        if 0 <= product_index < len(products):
            product = products[product_index]
            quantity = int(input("Enter the quantity: "))
            cart.add_product(product, quantity)
        else:
            print("Invalid product number.")
    elif choice == '3':
        product_index = int(input("Enter the product number to remove: ")) - 1
        if 0 <= product_index < len(products):
            product = products[product_index]
            quantity = int(input("Enter the quantity: "))
            cart.remove_product(product, quantity)
        else:
            print("Invalid product number.")
    elif choice == '4':
        total = cart.get_total_price()
        print(f"\nTotal price: ${total:.2f}")
    elif choice == '5':
        print("Exiting...")
        break
    else:
        print("Invalid choice.")
