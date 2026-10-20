import tkinter as tk
from tkinter import filedialog, messagebox
import os

# Crop Wealth App

root = tk.Tk()
root.title("Crop Wealth")
root.geometry("500x650")
root.configure(bg="#e2f5df")

# Background title
title = tk.Label(
    root,
    text="CROP WEALTH IS OUR WEALTH",
    font=("Arial", 19, "bold"),
    bg="#176b3a",
    fg="white",
    pady=20
)
title.pack(fill="x")

subtitle = tk.Label(
    root,
    text="Plant Disease Screening System",
    font=("Arial", 12),
    bg="#e2f5df",
    fg="#176b3a"
)
subtitle.pack(pady=12)

image_label = tk.Label(
    root,
    text="Upload a crop leaf photo",
    font=("Arial", 14),
    bg="#ffffff",
    fg="#333333",
    width=35,
    height=4
)
image_label.pack(pady=15)

result_label = tk.Label(
    root,
    text="Disease result will appear here",
    font=("Arial", 12),
    bg="#e2f5df",
    fg="#222222",
    wraplength=420,
    justify="left"
)
result_label.pack(pady=20)


def upload_image():
    filename = filedialog.askopenfilename(
        title="Select Leaf Photo",
        filetypes=[
            ("Image files", "*.png *.jpg *.jpeg")
        ]
    )

    if filename:
        image_label.config(
            text="Selected photo:\n" + os.path.basename(filename)
        )

        result_label.config(
            text=(
                "Photo uploaded successfully.\n\n"
                "AI disease detection is not connected yet.\n\n"
                "Please consult a local agricultural "
                "extension officer for diagnosis."
            )
        )


def show_guidance():
    messagebox.showinfo(
        "Crop Care Guidance",
        "1. Remove badly affected leaves when appropriate.\n\n"
        "2. Avoid unnecessary wetting of leaves.\n\n"
        "3. Check several plants for symptoms.\n\n"
        "4. Avoid pesticides until the disease is confirmed.\n\n"
        "5. Consult a local agricultural extension officer."
    )


upload_button = tk.Button(
    root,
    text="UPLOAD LEAF PHOTO",
    command=upload_image,
    font=("Arial", 12, "bold"),
    bg="#238443",
    fg="white",
    padx=20,
    pady=10
)
upload_button.pack(pady=10)

guidance_button = tk.Button(
    root,
    text="CROP CARE GUIDANCE",
    command=show_guidance,
    font=("Arial", 12, "bold"),
    bg="#d8a928",
    fg="black",
    padx=20,
    pady=10
)
guidance_button.pack(pady=10)

footer = tk.Label(
    root,
    text="Healthy Crops • Healthy Farmers • Healthy Future",
    font=("Arial", 10),
    bg="#e2f5df",
    fg="#176b3a"
)
footer.pack(side="bottom", pady=20)

root.mainloop()