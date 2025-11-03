# Online Shopping System

print("=== Welcome to Online Shopping System ===")

# Step 1: Product list with price
products = {
    1: ["T-Shirt", 500],
    2: ["Jeans", 1200],
    3: ["Shoes", 1500],
    4: ["Watch", 800],
    5: ["Bag", 700]
}

cart = {}

# Step 2: Display product list
def show_products():
    print("\nAvailable Products:")
    print("ID\tProduct\t\tPrice (₹)")
    print("-" * 30)
    for pid, details in products.items():
        print(f"{pid}\t{details[0]:<10}\t₹{details[1]}")

# Step 3: Add to cart
def add_to_cart(pid, qty):
    if pid in products:
        if pid in cart:
            cart[pid][1] += qty
        else:
            cart[pid] = [products[pid][0], qty, products[pid][1]]
        print(f"{qty} x {products[pid][0]} added to cart.")
    else:
        print("❌ Invalid Product ID!")

# Step 4: Show cart and total
def show_cart():
    if not cart:
        print("🛒 Your cart is empty.")
        return
    print("\n--- Your Cart ---")
    total = 0
    print("Product\t\tQty\tPrice\tSubtotal")
    print("-" * 50)
    for item in cart.values():
        name, qty, price = item
        subtotal = qty * price
        total += subtotal
        print(f"{name:<10}\t{qty}\t₹{price}\t₹{subtotal}")
    print("-" * 50)
    print(f"💰 Total Amount: ₹{total}")

# Step 5: Main program loop
while True:
    show_products()
    choice = input("\nEnter product ID to buy (or 'q' to checkout): ").strip()

    if choice.lower() == 'q':
        break

    if not choice.isdigit():
        print("⚠️ Please enter a valid number.")
        continue

    pid = int(choice)
    qty = input("Enter quantity: ").strip()

    if not qty.isdigit():
        print("⚠️ Please enter a valid quantity.")
        continue

    qty = int(qty)
    add_to_cart(pid, qty)

print("\n=== Checkout ===")
show_cart()
print("\n✅ Thank you for shopping with us! 🛍️")
