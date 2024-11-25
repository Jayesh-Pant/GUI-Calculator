# Calculator Application
## Description
This project is a simple calculator application built using Python's Tkinter library. It supports basic arithmetic operations like addition, subtraction, multiplication, and division. The graphical user interface (GUI) provides a clean and interactive design for the user.

## Features
Interactive GUI: Buttons for digits and operations with easy-to-read labels.
Basic Arithmetic Operations: Addition, subtraction, multiplication, and division.
Clear Functionality: A "C" button to clear the current input.
Instant Evaluation: Calculates and displays the result when the "=" button is clicked.
## Prerequisites
Python 3.x installed on your system.
Tkinter library (comes pre-installed with Python).
## How to Run
Save the script as calculator.py.
Open a terminal or command prompt and navigate to the script's directory.
Run the script using:
bash
Copy code
python calculator.py
Code
python
Copy code
import tkinter as tk

# Function to handle button clicks
def button_click(event):
    global expression
    button_text = event.widget.cget("text")
    if button_text == "=":
        try:
            result = eval(expression)
            input_text.set(str(result))
            expression = str(result)  # Update the expression with the result
        except:
            input_text.set("Error")
            expression = ""
    elif button_text == "C":
        expression = ""
        input_text.set("")
    else:
        expression += button_text
        input_text.set(expression)

# Setting up the main window
root = tk.Tk()
root.title("Calculator")

# Expression and input field
expression = ""
input_text = tk.StringVar()

# Input display
input_field = tk.Entry(root, textvariable=input_text, font=("Helvetica", 16), justify="right")
input_field.pack(fill="x", ipadx=8, pady=10, padx=10)

# Button frame
button_frame = tk.Frame(root)
button_frame.pack()

# Calculator buttons
buttons = [
    "7", "8", "9", "/",
    "4", "5", "6", "*",
    "1", "2", "3", "-",
    "C", "0", "=", "+"
]

row, col = 0, 0
for btn in buttons:
    b = tk.Button(button_frame, text=btn, font=("Helvetica", 14), width=4, height=2)
    b.grid(row=row, column=col, padx=5, pady=5)
    b.bind("<Button-1>", button_click)
    col += 1
    if col > 3:
        col = 0
        row += 1

# Run the application
root.geometry("300x400")
root.mainloop()
Functionality
Input Field:
Displays the current expression or result.
Updates dynamically as buttons are clicked.
Buttons:
Digits (0-9): Input numbers into the expression.
Operators (+, -, *, /): Perform arithmetic operations.
C: Clears the current input and resets the calculator.
=: Evaluates the expression and displays the result.
User Interface
A clean layout with buttons arranged in a grid.
A responsive input field at the top for displaying the current input or result.
The window size is set to 300x400, providing a compact and user-friendly design.
Example Usage
Launch the application.
Input a calculation (e.g., 7 + 3).
Press "=" to see the result (e.g., 10).
Use "C" to clear and start a new calculation.
Future Improvements
Add support for advanced operations (e.g., square root, percentage).
Improve the GUI design with colors and themes.
Enable keyboard input for calculations.
