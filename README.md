# BMI_app
This project is a Body Mass Index (BMI) Calculator built using Python and the Tkinter library for a graphical user interface (GUI). The application allows users to input their weight and height, and it calculates their BMI based on these values. The result is displayed in a message box, including the calculated BMI and the corresponding 

First thing in this app I import the libraries that i need 
import tkinter as tk
from tkinter import messagebox

creation the main function calculate bmi
def calculate_bmi():
    try:
        # Get user input from entry fields
        weight = float(weight_entry.get())
        height = float(height_entry.get())
        
        # Validate inputs
        if weight <= 0 or height <= 0:
            raise ValueError("Height and weight must be positive numbers.")
        
        # Calculate BMI
        bmi = weight / (height ** 2)
        
        # Determine BMI category
        if bmi < 18.5:
            category = "Underweight"
        elif 18.5 <= bmi < 24.9:
            category = "Normal weight"
        elif 25 <= bmi < 29.9:
            category = "Overweight"
        else:
            category = "Obesity"
        
        # Show the result in a message box
        messagebox.showinfo("BMI Result", f"Your BMI is: {bmi:.2f}\nYou are: {category}")
    
    except ValueError as e:
        messagebox.showerror("Input Error", f"Invalid input: {e}")

set up the interface and design of the app 
app = tk.Tk()
app.title("BMI Calculator")
app.geometry("400x300")
app.config(bg="#f0f0f0")

# Title label
title_label = tk.Label(app, text="BMI Calculator", font=("Arial", 20), bg="#f0f0f0", fg="#333")
title_label.pack(pady=10)

# Weight input
weight_label = tk.Label(app, text="Enter your weight (kg):", font=("Arial", 12), bg="#f0f0f0")
weight_label.pack(pady=5)
weight_entry = tk.Entry(app, font=("Arial", 12), width=15)
weight_entry.pack(pady=5)

# Height input
height_label = tk.Label(app, text="Enter your height (m):", font=("Arial", 12), bg="#f0f0f0")
height_label.pack(pady=5)
height_entry = tk.Entry(app, font=("Arial", 12), width=15)
height_entry.pack(pady=5)

# Calculate Button
calculate_button = tk.Button(app, text="Calculate BMI", font=("Arial", 14), command=calculate_bmi, bg="#4CAF50", fg="white", padx=10, pady=5)
calculate_button.pack(pady=20)

# Start the application
app.mainloop()


