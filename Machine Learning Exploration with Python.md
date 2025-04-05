# Machine Learning Exploration with Python

**1.  Create and activate a virtual environment:**

```
python -m venv venv_ml
source venv_ml/bin/activate  # On Windows: venv_ml\Scripts\activate
```



**2. Install required packages (with Lower NumPy Version Compatible with Torch):**

```
pip install "numpy<2" torch torchvision matplotlib pillow tqdm
```



**3.  Create a directory in the venv for data:**

```
mkdir data
```



**4.  Download a dataset of images of cats and dog by pasting the following URL into a browser window:**

```
https://storage.googleapis.com/mledu-datasets/cats_and_dogs_filtered.zip
```

Pasting the URL listed above into a browser will start the `cats_and_dogs_filtered.zip` download. Alternatively, you can download the ZIP file via command line using `wget` or `curl` if preferred.



**5.  Unzip the file and move the dataset to the `data` directory you just created:** 

After you do this, the following directory tree should be in place:

```
(venv_ml) $ tree data -L 2
data
└── cats_and_dogs_filtered
    ├── train
    ├── validation
    └── vectorize.py
```



**6.  Create a file named `cats_and_dogs.py` in the  `venv_ml` directory:** 

Add the following code to the file:

```
# cats_and_dogs.py

import os
import numpy as np
import matplotlib.pyplot as plt
from PIL import Image

import torch
import torch.nn as nn
from torch.utils.data import DataLoader

from torchvision import datasets, models, transforms, utils

# Set data paths (still hardcoded)
data_dir = 'data/cats_and_dogs_filtered'
train_dir = os.path.join(data_dir, 'train')
validation_dir = os.path.join(data_dir, 'validation')

# Define image transform (Resizing and converting to tensor)
# Add normalization if using pretrained models like ResNet
transform = transforms.Compose([
    transforms.Resize((224, 224)),
    transforms.ToTensor(),
    transforms.Normalize([0.485, 0.456, 0.406],
                          [0.229, 0.224, 0.225]),
])

# Load the datasets
train_dataset = datasets.ImageFolder(train_dir, transform=transform)
validation_dataset = datasets.ImageFolder(validation_dir, transform=transform)

# Create the dataloaders
train_loader = DataLoader(train_dataset, batch_size=32, shuffle=True)
validation_loader = DataLoader(validation_dataset, batch_size=32, shuffle=False)

# Get class names for human-readable labels
class_names = train_dataset.classes

# Image display helper
def imshow(img):
    npimg = img.numpy()
    plt.imshow(np.transpose(npimg, (1, 2, 0)))
    plt.axis('off')
    plt.show()

# Preview a batch of training images
if __name__ == "__main__":
    dataiter = iter(train_loader)
    images, labels = next(dataiter)

    class_names = train_dataset.classes  # Ensure this is defined

    # Show the first 5 images with labels
    fig, axes = plt.subplots(1, 5, figsize=(15, 3))
    for i in range(5):
        img = images[i].numpy().transpose((1, 2, 0))  # CHW → HWC
        axes[i].imshow(img)
        axes[i].set_title(class_names[labels[i]])
        axes[i].axis('off')

    plt.tight_layout()
    plt.show()
```



**7.  Run and Review:**

Making sure that you are in the  `venv_ml` directory, run the script:

```
python cats_and_dogs.py
```

It may take a few minutes to run. At the end, the script will open a Matplotlib figure showing five images of cats and dogs correctly labeled.



**8.  Suggestion for Future Sharing:**

To save the dependencies for future use or sharing:

```
pip freeze > requirements.txt
```

