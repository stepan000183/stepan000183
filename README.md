import tkinter as tk
from PIL import Image, ImageTk
import requests
import io

def greet():
    holiday_greeting = "З Новим Роком і Святим Миколаєм!"
    greeting_label.config(text=holiday_greeting)

window = tk.Tk()

image_url = "https://example.com/your_image.jpg"
response = requests.get(image_url)
image = Image.open(io.BytesIO(response.content))

photo = ImageTk.PhotoImage(image)
image_label = tk.Label(window, image=photo)
image_label.pack()

icon_path = "path/to/your/icon.ico"
icon_image = Image.open(icon_path)
window.iconphoto(True, ImageTk.PhotoImage(icon_image))

greeting_label = tk.Label(window, text="", font=("Helvetica", 16))
greeting_label.pack()

greet_button = tk.Button(window, text="Вітати", command=greet)
greet_button.pack()

window.mainloop()
