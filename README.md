# python_image_convert
Python Image Convert JPG to PNG with color profile

A common issue faced during image format conversion, especially from JPG to PNG, is the alteration of the image's colors.
This repository provides a solution to maintain color integrity while performing such conversions.
It contains two color profile files, 'USWebCoatedSWOP.icc' and 'sRGB Color Space Profile.icm', to facilitate the conversion without losing the original colors.

## Prerequisites
- Python
- Pillow

Install the necessary Python packages using pip:
```shell
pip install Pillow
```

## How to Use

Here's a simple Python script demonstrating how to use the provided ICC profiles to convert a JPEG image to PNG without losing color accuracy:

```python
from PIL import Image, ImageCms
import os
from datetime import datetime

# Load the JPEG image
path = "./test.jpeg"
img = Image.open(path)

# Convert the color profile
conv_img = ImageCms.profileToProfile(img, 'USWebCoatedSWOP.icc', 'sRGB Color Space Profile.icm', renderingIntent=0, outputMode='RGB')

# Save the converted image
output_path = "./test_converted.png"
conv_img.save(output_path, "PNG")
```

Remember to download 'USWebCoatedSWOP.icc' and 'sRGB Color Space Profile.icm' from this repository and place them in the same directory as your script, or provide the correct path to the files in the script.


## Contributing
Feel free to fork this repository, open issues, or submit pull requests if you have suggestions or improvements to share.

## License
This project is licensed under the MIT License - see the LICENSE file for details.

## Acknowledgements
Thanks to @dongdongju96 and all the contributors who are helping in refining and improving this project, making it more user-friendly and robust.
