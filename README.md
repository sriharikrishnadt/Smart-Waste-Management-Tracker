# Smart-Waste-Management-Tracker
## 🗑️ Smart Waste Management Tracker
## 📌 Project Overview

The Smart Waste Management Tracker is a Python-based system that helps track daily waste generation in households or colleges.

It allows users to record waste type, quantity, and disposal status. The system helps promote cleanliness and environmental awareness.

## 🎯 Objectives
Track daily waste generated
Classify waste into categories (Plastic, Organic, Metal, etc.)
Monitor disposed and pending waste
Encourage proper waste management
## 🛠️ Technologies Used
Python

VS Code
## ⚙️ Features
Add waste record (type, quantity, location)
View all waste records
Mark waste as disposed
View pending waste
## ▶️ How to Run
```py
python main.py
```
## 🧪 Sample Output:
```py
♻ Waste Records:

1. Plastic - 2kg from Hostel Block A [Pending]
2. Organic - 5kg from Canteen [Disposed]
```
## 🌱 Future Enhancements
Store records using files
Add waste collection schedule
Build GUI using Tkinter
Generate waste statistics

## 💻 PROGRAM
```py
# Smart Waste Management Tracker

waste_records = []

def add_waste():
    wtype = input("Enter waste type (Plastic/Organic/Metal): ")
    quantity = input("Enter quantity (kg): ")
    location = input("Enter location: ")

    waste = {
        "type": wtype,
        "quantity": quantity,
        "location": location,
        "status": "Pending"
    }

    waste_records.append(waste)
    print("✅ Waste record added successfully!")


def view_waste():
    if not waste_records:
        print("No waste records available.")
        return

    print("\n♻ Waste Records:")
    for i, waste in enumerate(waste_records, start=1):
        print(f"{i}. {waste['type']} - {waste['quantity']}kg from {waste['location']} [{waste['status']}]")

        
def mark_disposed():
    view_waste()
    if not waste_records:
        return

    try:
        num = int(input("Enter record number to mark disposed: "))
        waste_records[num-1]["status"] = "Disposed"
        print("✅ Waste marked as disposed!")
    except:
        print("Invalid choice!")


def show_pending():
    print("\n⏳ Pending Waste:")
    found = False

    for waste in waste_records:
        if waste["status"] == "Pending":
            print(f"{waste['type']} - {waste['quantity']}kg from {waste['location']}")
            found = True

    if not found:
        print("No pending waste 🎉")


def main():
    while True:
        print("\n🗑 Smart Waste Management System")
        print("1. Add Waste Record")
        print("2. View All Records")
        print("3. Mark Waste as Disposed")
        print("4. View Pending Waste")
        print("5. Exit")

        choice = input("Enter choice: ")

        if choice == '1':
            add_waste()
        elif choice == '2':
            view_waste()
        elif choice == '3':
            mark_disposed()
        elif choice == '4':
            show_pending()
        elif choice == '5':
            print("Exiting program...")
            break
        else:
            print("Invalid choice!")


# Run program
main()
```
## Output:
<img width="1307" height="669" alt="image" src="https://github.com/user-attachments/assets/427eb6c0-4542-47b7-909b-77577d666111" />

##  Result

The Smart Waste Management Tracker helps track waste generation and disposal efficiently.
It promotes clean and organized waste management practices.
