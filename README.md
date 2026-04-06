# Smart Study Planner (Python Tkinter Project)

A simple GUI-based study planner built using Python Tkinter.
Users can enter their Name, Subject, and Study Hours, and the data will be stored in a text file in table format.

The user can also choose the location where the file will be saved.

## Features
Simple Tkinter GUI

Uses MessageBox for alerts

Allows custom file save location

Stores data in table format

Automatically creates header row in file

## Requirements
Python 3.x

Tkinter (comes with Python)

## Python Code
```py
# Smart Study Planner
# A simple Tkinter project that stores study data in a text file

import tkinter as tk
from tkinter import messagebox, filedialog
import os

# Global variable to store selected file path
file_path = ""


# Function to choose file saving location
def choose_location():
    global file_path

    file_path = filedialog.asksaveasfilename(
        defaultextension=".txt",
        filetypes=[("Text Files", "*.txt")],
        title="Select file location"
    )

    # Create file and write table header if it does not exist
    if file_path and not os.path.exists(file_path):
        with open(file_path, "w") as file:
            header = f"{'NAME':<15}{'SUBJECT':<15}{'HOURS':<10}\n"
            file.write(header)
            file.write("-" * 40 + "\n")


# Function to save entered data
def save_data():

    name = entry_name.get()
    subject = entry_subject.get()
    hours = entry_hours.get()

    # Check if file location selected
    if file_path == "":
        messagebox.showwarning("Warning", "Please choose file location first!")

    # Check empty fields
    elif name == "" or subject == "" or hours == "":
        messagebox.showwarning("Warning", "Please fill all fields!")

    else:
        # Append data to file
        with open(file_path, "a") as file:
            row = f"{name:<15}{subject:<15}{hours:<10}\n"
            file.write(row)

        messagebox.showinfo("Success", "Data saved successfully!")

        # Clear entry fields
        entry_name.delete(0, tk.END)
        entry_subject.delete(0, tk.END)
        entry_hours.delete(0, tk.END)


# ---------------- GUI DESIGN ---------------- #

root = tk.Tk()
root.title("Smart Study Planner")
root.geometry("350x300")

# Title
tk.Label(root, text="Smart Study Planner",
         font=("Arial", 16, "bold")).pack(pady=10)

# Name input
tk.Label(root, text="Name").pack()
entry_name = tk.Entry(root)
entry_name.pack()

# Subject input
tk.Label(root, text="Subject").pack()
entry_subject = tk.Entry(root)
entry_subject.pack()

# Study hours input
tk.Label(root, text="Study Hours").pack()
entry_hours = tk.Entry(root)
entry_hours.pack()

# Buttons
tk.Button(root,
          text="Choose Save Location",
          command=choose_location).pack(pady=5)

tk.Button(root,
          text="Save Data",
          command=save_data).pack(pady=5)

tk.Button(root,
          text="Exit",
          command=root.quit).pack(pady=5)

# Run application
root.mainloop()
```

## Example Stored File (study_data.txt):
```py
NAME           SUBJECT        HOURS
----------------------------------------
Hari           AI             3
Arun           Python         2
Priya          DBMS           4
```
## How to Run
```py
python study_planner.py
```
## Output:
<img width="444" height="424" alt="image" src="https://github.com/user-attachments/assets/c8095565-3c0f-4705-b65e-c74a0a345519" />

<img width="1261" height="588" alt="image" src="https://github.com/user-attachments/assets/252b6599-6d12-4afb-ba76-9f9a0f208e0c" />

##  Result:
Thus the project created is executed using VS code.
