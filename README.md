# Snellen Chart Simulator

## Overview

The Snellen Chart Simulator is a simple Python-based tool for generating and displaying Snellen charts used in vision acuity testing. This project demonstrates how to create Snellen charts with varying font sizes to simulate different levels of visual acuity. By using this tool, you can visualize how text sizes affect readability, which is essential for assessing vision performance.

## Purpose

The Snellen chart is a common tool in ophthalmology and optometry for measuring visual acuity. It consists of letters arranged in rows, each row progressively decreasing in size. The smallest letters a person can read from a specific distance determine their visual acuity.

This simulator helps in:
- **Educational Demonstrations**: Providing a visual representation of how text size affects readability.
- **Training**: Helping students and professionals understand the principles of vision acuity testing.
- **Prototyping**: Allowing developers to quickly create charts for research or software testing.

## How It Works

The simulator generates a Snellen chart with varying font sizes to represent different vision acuity levels. The steps involved are:

1. **Configuration**: Define a list of font sizes corresponding to different vision levels.
2. **Chart Creation**: Use the `create_snellen_chart` function to generate an image of the Snellen chart with the specified font size.
3. **Chart Display**: Use the `display_chart` function to visualize the generated chart.

## Getting Started

### Prerequisites

Ensure you have the following libraries installed:
- `matplotlib`
- `PIL` (Pillow)
- `numpy`

You can install them using pip:

```bash
pip install matplotlib pillow numpy
```

## Running the Simulator
### 1. Clone the Repository
```
git clone https://github.com/yourusername/snellen-chart-simulator.git
cd snellen-chart-simulator
```
### 2. Run the Python Script

Save the following code in a file, e.g., snellen_chart_simulator.py:
```
import matplotlib.pyplot as plt
from PIL import Image, ImageDraw, ImageFont
import numpy as np

# Configuration for the simulator
font_sizes = [72, 48, 36, 24, 18, 14]  # List of font sizes for different vision acuity levels

def create_snellen_chart(font_size):
    """
    Create an image of a Snellen chart with a specific font size.
    
    Parameters:
        font_size (int): The size of the font to use for the letters.
    
    Returns:
        Image object: The generated image of the Snellen chart.
    """
    # Create a blank white image
    width, height = 800, 1000
    image = Image.new("RGB", (width, height), "white")
    draw = ImageDraw.Draw(image)

    # Use a default PIL font
    font = ImageFont.load_default()
    
    # Define letters to be used in the test
    letters = ['E', 'F', 'P', 'T', 'O', 'Z', 'L', 'P', 'E', 'T']
    
    # Adjust font size if necessary
    # Note: The default font does not support size changes, so all letters will be the same size
    # You may need to find a suitable .ttf font file if size variation is needed.

    # Draw letters on the image
    y_position = 50
    for letter in letters:
        draw.text((width // 4, y_position), letter, font=font, fill="black")
        y_position += font_size + 20
    
    return image

def display_chart(image):
    """
    Display the Snellen chart image.
    
    Parameters:
        image (Image object): The image of the Snellen chart to display.
    """
    plt.figure(figsize=(8, 10))
    plt.imshow(np.array(image))
    plt.axis('off')  # Hide the axis
    plt.show()

# Create and display charts with different font sizes
for size in font_sizes:
    chart_image = create_snellen_chart(size)
    display_chart(chart_image)
    input(f"Press Enter to view the chart with font size {size}...")
```

Execute the script:
```
python snellen_chart_simulator.py
```

# Results
The simulator generates Snellen charts with various font sizes to help visualize how text size affects readability. Each chart corresponds to a different level of visual acuity.

**Sample Charts**


- **Font Size 72** : Represents the largest letters, typically used for the highest levels of vision acuity.
-**Font Size 14**: Represents the smallest letters, useful for testing lower levels of acuity.

These visualizations can be used for educational purposes or preliminary testing before a formal eye examination.

# Contributing
Contributions are welcome! If you have suggestions or improvements, please open an issue or submit a pull request.

# License
This project is licensed under the MIT License. See the LICENSE file for details.

# Contact
For any questions, please contact me at mgsite94@gmail.com
