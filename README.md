## Integration of a Mathematical Calulations with a Chat Completion System using LLM Function-Calling

### AIM:
To design and implement a Python function for calculating the volume of a cylinder, integrate it with a chat completion system utilizing the function-calling feature of a large language model (LLM).

### PROBLEM STATEMENT:

### DESIGN STEPS:

#### STEP 1:
Install required packages

#### STEP 2:
Give the essential function calling code into it

#### STEP 3:
Integrate the function into an LLM-based chat completion system with function-calling capabilities.

### PROGRAM:
```
from dotenv import load_dotenv
import google.generativeai as genai
import os

# Load API key from .env
load_dotenv()
genai.configure(api_key="Enter API Key")

# Create a Gemini model
model = genai.GenerativeModel("gemini-1.5-flash")

import math
import json

# Function to calculate the volume of a cone
def find_volume_of_cone(radius, height):
    """Calculate the volume of a cone given its radius and height"""
    volume = (1/3) * math.pi * (radius ** 2) * height
    cone_info = {
        "shape": "cone",
        "radius": radius,
        "height": height,
        "formula": "(1/3) * pi * r^^2 * h",
        "volume": volume,
        "steps": [
            f"Step 1: Square the radius ({radius}² = {radius ** 2})",
            f"Step 2: Multiply by height ({radius ** 2} × {height} = {radius ** 2 * height})",
            f"Step 3: Multiply by π ({math.pi:.2f} × {radius ** 2 * height})",
            f"Step 4: Divide by 3 to get volume ({volume:.2f})"
        ]
    }
    return json.dumps(cone_info, indent=4)

# Function definition schema
functions = [
    {
        "name": "find_volume_of_cone",
        "description": "Calculate the volume of a cone given its radius and height",
        "parameters": {
            "type": "object",
            "properties": {
                "radius": {
                    "type": "number",
                    "description": "The radius of the cone (e.g., 5.0)",
                },
                "height": {
                    "type": "number",
                    "description": "The height of the cone (e.g., 10.0)",
                }
            },
            "required": ["radius", "height"],
        },
    }
]

# Example messages
messages = [
    {
        "role": "user",
        "content": "Find the volume of a cone with radius 5 and height 10"
    }
]

# Example usage
if __name__ == "__main__":
    print(find_volume_of_cone(5, 10))

```

### OUTPUT:
<img width="617" height="278" alt="image" src="https://github.com/user-attachments/assets/6ea16f7a-813b-45bb-aa42-3d7c79b5cfd8" />

### RESULT:
Thus, The integration of a Mathematical Calulations with a Chat Completion System using LLM Function-Calling is executed successfully.
