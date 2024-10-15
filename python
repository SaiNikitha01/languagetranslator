import tkinter as tk
from tkinter import PhotoImage
from googletrans import Translator
from PIL import Image, ImageTk  # For resizing image


class LanguageTranslator:
    def __init__(self, root):
        self.root = root
        self.root.title("Language Translator")
        self.root.geometry("400x300")

        # Create input fields
        self.input_label = tk.Label(root, text="Enter text to translate:")
        self.input_label.pack()
        self.input_field = tk.Text(root, height=5, width=40)
        self.input_field.pack()

        # Create language selection dropdowns
        self.src_label = tk.Label(root, text="Source language:")
        self.src_label.pack()
        self.src_var = tk.StringVar()
        self.src_var.set("en")  # Default to English
        self.src_menu = tk.OptionMenu(root, self.src_var, "en", "es", "fr", "de", "it")
        self.src_menu.pack()

        self.dst_label = tk.Label(root, text="Target language:")
        self.dst_label.pack()
        self.dst_var = tk.StringVar()
        self.dst_var.set("es")  # Default to Spanish
        self.dst_menu = tk.OptionMenu(root, self.dst_var, "en", "es", "fr", "de", "it")
        self.dst_menu.pack()

        # Create translate button
        self.translate_button = tk.Button(root, text="Translate", command=self.translate_text)
        self.translate_button.pack()

        # Create output field with image background
        self.output_label = tk.Label(root, text="Translated text:")
        self.output_label.pack()

        # Create a Canvas to hold the background image
        self.canvas = tk.Canvas(root, width=400, height=100)
        self.canvas.pack()

        # Load and resize the image using PIL
        self.original_image = Image.open(r"c:\Users\DELL\Downloads\translatorimg1.jpeg")
        self.resized_image = self.original_image.resize((390, 250), Image.Resampling.LANCZOS)
        self.background_image = ImageTk.PhotoImage(self.resized_image)

        # Add the resized image to the canvas
        self.canvas.create_image(10, 10, anchor="nw", image=self.background_image)

        # Create the Text widget on top of the canvas
        self.output_field = tk.Text(root, height=5, width=40, bg="white")
        self.output_field.pack()

    def translate_text(self):
        input_text = self.input_field.get("1.0", "end-1c")
        src_language = self.src_var.get()
        dst_language = self.dst_var.get()

        translator = Translator()
        translated_text = translator.translate(input_text, src=src_language, dest=dst_language)

        self.output_field.delete("1.0", "end")
        self.output_field.insert("1.0", translated_text.text)


if __name__ == "__main__":
    root = tk.Tk()
    translator = LanguageTranslator(root)
    root.mainloop()
