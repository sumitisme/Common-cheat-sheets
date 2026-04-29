# <span style="color:green">Pytorch Cheat sheet</span>

---

## Use Jupyter Notebook when using pytorch and pandas, it's much more convenient.

---

# IMPORTING PYTORCH

---

```py

# MAIN STUFF

# Root package
import torch

# Neural Networks
import torch.nn as nn


# EXTRA STUFF

# Popular image datsets, architectures and transforms
from torchvision import datasets, models, transforms

# Collection of layers, activations and more
import torch.nn.functional as F            
```
---

# EXTRA STUFF AFTER IMPORTS 

---

## Checking version

```py
print(f"PyTorch version: {torch.__version__}")
```
---

## Some intro regarding neural networks

```py
# Almost everything in PyTorch is called a "Module"
# Neural Networks are built by stacking Modules together

This_is_a_module = nn.Linear(in_features = 1, out_features = 1)

print(type(this_is_a_module))
# Will print out 
# <class 'torch.nn.modules.linear.Linear'>
```
---

# DATA IMPORTS

---

```py
# Import PyTorch Dataset (You can store your data here) and DataLoader (You can load your data here)
from torch.utils.data import Dataset, DataLoader
```
---

# CREATING TENSORS

---

```py
# Create a single number tensor (scalar)
scalar = torch.tensor(7)

# Create a random tensor
# This will create a Tensor of size 3x4
random_tensor = torch.rand(size = (3, 4))

# multiply two random tensors
random_tensor_1 = torch.rand(size = (3, 4))
random_tensor_2 = torch.rand(size = (3, 4))
random_tensor_3 = random_tensor_1 * random_tensor_2

# NOTE: Pytorch has support for most math operators (+, *, -, /)
```
---

# DOMAIN LIBRARIES

---

## Computer Vision

```py
# Base computer vision library
import torchvision

# Other components of TorchVision (premade datasets, pretrained models and image transforms)
from torchvision import datasets, models, transforms
```
---

## Text and Natural Language Processing (NLP)

```py
# Base Text and NLP library
import torchtext

# Other components of TorchText (premade datasets, pretrained models and text transforms)
from torchtext import datasets, models, transforms
```
---

## Audio and Speech

```py
# Base Audio and Speech processing library
import torchaudio

# Other components of TorchAudio (premade datasets, pretrained models and text transforms)
from torchaudio import datasets, models, transforms
```
---

## Recommendation systems (currently in beta, don't use yet)

```py
# Base recommendation system library
import torchrec

# Other components of TorchRec
from torchrec import datasets, models
```
---

# PYTORCH ON CPU, GPU or MPS

---

<p>NVIDIA GPU("cuda") > MPS device ("mps") > CPU ("cpu")</p><br>
<p>MPS is apple hardware</p><br>
<p>Set up device-agnostic code at the start of your workflow</p>

---

## Setting up device-agnostic code

```py
if torch.cuda.is_available():
    device = "cuda"
elif torch.backends.mps.is_available():
    device = "mps"
else:
    device = "cpu"

print(f"Using Device: " {device})
# If this part isn't written then the device is defaulted to the cpu
```
---

# SENDING A TENSOR TO TARGET DEVICE

---

```py
# Creating a tensor
x = torch.tensor([1, 2, 3])
print(x.device) # Default is CPU

# Send tensor to target device
x = x.to(device)
print(x.device)
```
---

# SETTING RANDOM SEEDS

---

```py
import torch

# The number inside the brackets represents "degree of randomness"
torch.manual_seed(42)

# Creating random tensors
random_tensor_A = torch.rand(3, 4) # Tensor of size 3x4

torch.manual_seed(42) # If this is commented out then the results won't be reproduced
random_tensor_B = torch.rand(3, 4)

# Here, random_tensor_A and random_tensor_B will have the same value since they are derived from the same seed. Essentially, random isn't random

# Checking
print(f"Tensor A:\n{random_tensor_A}\n")
print(f"Tensor B:\n{random_tensor_B}\n")
print(f"Does Tensor A equal Tensor B? (anywhere)?\n")
random_tensor_A == random_tensor_B
```

```py
# You can also set the random seed on the GPU (for CUDA)
torch.cuda.manual_seed(42)
```
---

# Neural Networks

---

## Importing

```py
from torch import nn
```
---

## Linear Layers

```py
# Create a linear layer with 10 in features and 10 out features
linear_layer = nn.Linear(in_features = 10, out_features = 10)

# Create an Identity layer
identity_layer = nn.Identity()
```
---

## Convolutional Layers (For making Convolutional Neural Networks and CNN's)

<p>PyTorch has several in-built convolutional layers. Naming of convolutional layers usually follows torch.nn.convXd where "X" can be a value of 1, 2, 3</p><br><br>
<p>X represents the number of dimensions the convolution will operate over, 1 for single dimension text, 2 for two dimension images, 3 for objects like videos. (height x width x time)</p><br>

```py
# Create a Conv1d layer (Often used for text with a singular dimension)
conv1d = nn.Conv1d( in_channels = 1, 
                    out_channels = 10, 
                    kernel_size = 3)


# Create a Conv2d layer (for images, height x width)
conv2d = nn.Conv1d( in_channels = 3, # 3 channels for color images (red, green, blue)
                    out_channels = 10, 
                    kernel_size = 3)


# Create a Conv3d layer (often used for video with Height x Width x Time dimensions)
conv3d = nn.Conv3d( in_channels = 3,
                    out_channels = 10,
                    kernel_size = 3)
```