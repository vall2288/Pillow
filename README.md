from PIL import Image, ImageDraw, ImageFont

# Load the user's photo (replace "image1.jpg" with the actual path to the photo)
photo_path = "image1.jpg"  # Save the provided image as "image1.jpg" in your working directory
photo = Image.open(photo_path).resize((110, 130))

# Create the base license image
width, height = 600, 350
background_color = (225, 240, 255)
img = Image.new('RGB', (width, height), color=background_color)
draw = ImageDraw.Draw(img)

# Fonts
try:
    font = ImageFont.truetype("arial.ttf", 18)
    font_bold = ImageFont.truetype("arialbd.ttf", 22)
except:
    font = ImageFont.load_default()
    font_bold = font

# Title
draw.text((20, 18), "Pennsylvania Driver License", fill=(10, 60, 160), font=font_bold)

# Paste the photo
img.paste(photo, (30, 60))

# Details
details = [
    ("Name", "martin Lambert"),
    ("Date of Birth", "1992-05-14"),
    ("Address", "1234 Main St, Harrisburg, PA 17101"),
    ("License Number", "29 123 456"),
    ("Class", "C"),
    ("Expiration Date", "2029-05-14"),
    ("Issue Date", "2025-06-11"),
    ("Sex", "M"),
    ("Height", "5'-10\""),
    ("Eye Color", "BLU"),
    ("Organ Donor", "Yes"),
]

y = 60
for label, value in details:
    draw.text((160, y), f"{label}:", fill=(0, 0, 0), font=font)
    draw.text((340, y), value, fill=(0, 0, 0), font=font)
    y += 26

# Footer
draw.text((20, height - 30), "This is a mock Pennsylvania driver license for testing/UI/demo purposes only.", fill=(70, 70, 70), font=font)

img.save("mock_pennsylvania_driver_license_with_photo.png")
print("Mock license image saved as mock_pennsylvania_driver_license_with_photo.png")
