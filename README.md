class CoffeeShop:
    def __init__(self):
        self.menu = {
            "espresso": 2.50,
            "cappuccino": 3.00,
            "latte": 3.50,
            "americano": 2.00,
            "macchiato": 3.00
        }
        self.orders = []

    def display_menu(self):
        print("Menu:")
        for item, price in self.menu.items():
            print(f"{item.capitalize()}: ${price:.2f}")

    def take_order(self):
        while True:
            self.display_menu()
            order = input("Enter your order (type 'done' to finish): ").lower()
            if order == 'done':
                break
            if order in self.menu:
                self.orders.append(order)
            else:
                print("Sorry, that's not on the menu.")

    def calculate_total(self):
        total = sum([self.menu[item] for item in self.orders])
        return total

    def checkout(self):
        print("Your Orders:")
        for item in self.orders:
            print(item.capitalize())
        total = self.calculate_total()
        print(f"Total: ${total:.2f}")
        payment = float(input("Enter your payment amount: $"))
        if payment < total:
            print("Payment insufficient. Please pay the full amount.")
        else:
            change = payment - total
            print(f"Thank you for your order! Your change is ${change:.2f}")

    def run(self):
        print("Welcome to Our Coffee Shop!")
        self.take_order()
        self.checkout()


if __name__ == "__main__":
    coffee_shop = CoffeeShop()
    coffee_shop.run()
