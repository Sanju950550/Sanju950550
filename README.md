# Define an empty list to store the registered donors
donors = []

# Function to register a new donor
def register_donor():
    name = input("Enter your name: ")
    blood_group = input("Enter your blood group: ")
    phone_number = input("Enter your phone number: ")
    village = input("Enter your village name: ")
    mandal = input("Enter your mandal: ")
    district = input("Enter your district: ")
    state = input("Enter your state: ")

    donor = {
        "name": name,
        "blood_group": blood_group,
        "phone_number": phone_number,
        "address": {
            "village": village,
            "mandal": mandal,
            "district": district,
            "state": state
        }
    }
    donors.append(donor)
    print("Donor registered successfully!")

# Function to ask for blood and display donors
def ask_for_blood():
    blood_group_needed = input("Enter the blood group you need: ")
    mandal_needed = input("Enter the mandal you need: ")

    print(f"Donors with blood group {blood_group_needed} in mandal {mandal_needed}:")
    matching_donors = [donor for donor in donors if donor["blood_group"].upper() == blood_group_needed.upper() and donor["address"]["mandal"].upper() == mandal_needed.upper()]

    if len(matching_donors) == 0:
        print("No matching donors found.")
    else:
        for donor in matching_donors:
            print(f"Name: {donor['name']}, Phone: {donor['phone_number']}")

# Main function to run the app
def blood_donation_system():
    while True:
        print("\nBlood Donation System")
        print("1. New Donor")
        print("2. Ask for Blood")
        print("3. Exit")

        choice = input("Enter your choice (1-3): ")

        if choice == "1":
            register_donor()
        elif choice == "2":
            ask_for_blood()
        elif choice == "3":
            print("Thank you for using the Blood Donation System!")
            break
        else:
            print("Invalid choice. Please try again.")

# Run the blood donation system app
blood_donation_system()
