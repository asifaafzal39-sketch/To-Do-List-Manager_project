# Password_Generator_Project

import random
import string

print("Strong Password Generator")

while True:
    try:
        # Ask user for password length
        length = int(input("Enter password length: "))

        if length <= 0:
            print("Please enter a number greater than 0.")
            continue

        # Create character pool
        lowercase = string.ascii_lowercase
        uppercase = string.ascii_uppercase
        digits = string.digits
        symbols = string.punctuation

        all_characters = lowercase + uppercase + digits + symbols

        # Generate password
        password = ""
        for i in range(length):
            password += random.choice(all_characters)

        print("Your strong password is:", password)

    except ValueError:
        print("Invalid input! Please enter a number.")

    # Ask user to continue
    choice = input("Generate another password? (yes/no): ").lower()
    if choice != "yes":
        print("Program ended.")
        break

