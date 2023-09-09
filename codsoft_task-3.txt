from tkinter import *
from tkinter import messagebox
import random
import string

root = Tk()
root.title("Password Generator")
root.configure()
def generate_password(arbitrary):
    up = string.ascii_uppercase
    low = string.ascii_lowercase
    dig = string.digits
    punc = string.punctuation
    s = list(up + low + dig + punc)
    random.shuffle(s)
    password = "".join(random.choices(s, k=arbitrary))
    return password

def password_length():
   try:
      length = int(enter_length.get())
      if length <= 7:
         messagebox.showinfo("Error", "Password length needs to be 8 or more than 8.")
         return length

      password = generate_password(length)
      label_app_pass.insert(0, password)
   except ValueError:
      messagebox.showinfo("Error", "Please enter a valid integer.")


Label__name__length = Label(root, text="Enter user name")
Label__name__length.grid(row=0, column=0, padx=10, pady=10)

Label_pass_length = Label(root, text="Password Length:")
Label_pass_length.grid(row=1, column=0, padx=10, pady=10)
label_word_pass = Entry(root)
label_word_pass.grid(row=0, column=1, padx=10, pady=10)

enter_length = Entry(root)
enter_length.grid(row=1, column=1, padx=10, pady=10)

generate_button = Button(root, text="Generate Password", command=password_length)
generate_button.grid(row=4, column=1, columnspan=2, padx=10, pady=10)

generate_button_accept = Button(root, text="Accept")
generate_button_accept.grid(row=5, column=0, columnspan=2, padx=10, pady=10)

generate_button_reset= Button(root, text="Reset")
generate_button_reset.grid(row=5, column=1, columnspan=2, padx=10, pady=10)

Label__name__length = Label(root, text="Password ")
Label__name__length.grid(row=2, column=0, padx=10, pady=10)
label_app_pass = Entry(root, text="Password")
label_app_pass.grid(row=2, column=1, padx=10, pady=10)

root.mainloop()