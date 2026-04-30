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

<p>PyTorch has several in-built convolutional layers. Naming of convolutional layers usually follows torch.nn.convXd where "X" can be a value of 1, 2, 3</p><br>
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
---

## Transformer Layers (for making Transformer models)

<p>PyTorch has inbuilt Transformer Layers.</p><br>
<p>Using in-built PyTorch Transformer Layers can speed up the process because of "Pytorch's BetterTransformer"</p><br>

```py
# Create a Transformer model (Based on the paper "Attention Is All You Need" - https://arxiv.org/abs/1706.03762)
transformer_model = nn.Transformer()

# Create a single Transformer encoder cell
transformer_encoder = nn.TransformerEncoderLayer(   d_model = 768, # embedding dimension
                                                    nhead = 12)    # number of attention heads

# Stacking together Transformer encoder cells
transformer_encoder_stack = nn.TransformerEncoder(  encoder_layer = transformer_encoder, # From above
                                                    num_layers = 6) # 6 Transformer encoders stacked on top of each other


# Create a single Transformer decoder cell
transformer_decoder = nn.TransformerDecoderLayer(d_model = 768,
                        nhead = 12)

# Stack together Transformer decoder cells
transformer_decoder_stack = nn.TransfomerDecoder(   decoder_layer = transformer_decoder,   # From above
                                                    num_layers = 6) # 6 Transformer decoders stacked on top of each other
```
---

## Recurrent Layers (for making Recurrent Neural Networks (RNN's))

<p>PyTorch has in-built support for Recurrent Neural Network layers such as LSTM (Long Short Term Memory) and GRU (Gated Recurrent Unit)</p><br>

```py
# Create a single LSTM cell
lstm_cell = nn.LSTMCell(input_size = 10,
                        hidden_size = 10)

# Stack together LSTM cells
lstm_stack = nn.LSTM(   input_size = 10,
                        hidden_size = 10,
                        num_layers = 3) # 3 single LSTM cells stacked on top of each other

# Create a single GRU cell
gru_cell = nn.GRUCell(  input_size = 10,
                        hidden_size = 10)

# Stack together GRU cells
gru_stack = nn.GRU( input_size = 10,
                    hidden_size = 10,
                    num_layers = 3) # 3 single GRU cells stacked on top of each other
```
---

# ACTIVATION FUNCTIONS

---

```py
# ReLU (rectified Linear Unit)
relu = nn.ReLu()

# Sigmoid
sigmoid = nn.Sigmoid()

# Softmax
softmax = nn.Softmax()
```
---

# LOSS FUNCTIONS

---

```py
# L1Loss - also known as MAE
loss_fn = nn.L1Loss()

# MSELoss - Mean Squared Error
loss_fn = nn.MSELoss()

# Binary cross entropy (for binary classification problems)
loss_fn = nn.BCEWithLogitsLoss()

# Cross entropy (for multi-class classification problems)
loss_fn = nn.CrossEntropyLoss()
```
---

# OPTIMIZERS

---

```py
# Create a baseline model
model = nn.Transformer()

# SGD (Stochastic Gradient Descent)
optimizer = torch.optim.SGD(lr = 0.1, # Set the learning rate (This is required)
                            params = model.parameters()) # Tell the optimizer what parameters to optimize
```

```py
# Create a baseline model
model = nn.Transformer()

# Adam Optimizer
optimizer = torch.optim.Adam(   lr = 0.001, # set the learning rate
                                params = model.parameters()) # Tell the optimizer what parameters to optimize
```
---

# CREATE DATA

---
```py
# Create *known* parameters
weight = 0.7
bias = 0.3

# Create data
start = 0
end = 1
step = 0.02

X = torch.arange(start, end, step).unsqueeze(dim = 1) # data
y = weight * X + bias # Labels (want model to learn from data to predict these)

X[:10], y[:10]
```

```py
# Create train/test split
train_split = int(0.8 * len(X)) # 80% of data used for training set, 20% for testing
X_train, y_train = X[:train_split], y[:train_split]
X_test, y_test = X[train_split:], y[train_split:]

len(X_train), len(y_train), len(X_test), len(y_test)
```
---

# CREATE A MODEL

---

```py
from torch import nn

# Option 1 - subclass torch.nn.Module
class LinearRegressionModel(nn.Module):
    def __init__(self):
        super().__init__()
        # Use nn.Linear() for creating the model parameter
        self.linear_layer = nn.Linear(  in_features = 1,
                                        out_features = 1)

    # Define the forward computation (input data x flows through nn.Linear())
    def forward(self, x: torch.Tensor) -> torch.Tensor:
        return self.linear_layer(x)

model_0 = LinearRegressionModel()
model_0, model_0.state_dict()
```
---

```py
# Creating the same model as above but using torch.nn.Sequential
from torch import nn

# Option 2 - use torch.nn.Sequential
model_1 = torch.nn.Sequential(
    nn.Linear(  in_features = 1
                out_features = 1)
)

model_1, model_1.state_dict()
```
---

# SETUP LOSS FUNCTION AND OPTIMIZER

---

```py
# Create loss function
loss_fn = nn.L1Loss()

# Create Optimizer
optimizer = torch.optim.SGD(params = model_1.parameters(), # optimize newly created model's parameters
                            lr = 0.01)
```
---

# CREATE A TRAINING / TESTING LOOP

---

```py
torch.manual_seed(42)

# Setting the number of epochs
epochs = 1000

# Put data on the available device
# Without this, an error will happen (not all data on target device)
X_train = X_train.to(device)
X_test = X_test.to(device)
y_train = y_train.to(device)
y_test = y_test.to(device)

# Put model on the available device
# With this, an error will happen (the model is not on target device)
model_1 = model_1.to(device)

for epoch on range(epochs):
    ### Training
    model_1.train() # train mode is on by default after construction

    # 1. Forward pass
    y_pred = model_1(X_train)

    # 2. Calculate loss
    loss = loss_fn(y_pred, y_train)

    # 3. Zero grad optimizer
    optimizer.zero_grad()

    # 4. Loss backward
    loss.backward()

    # 5. Step the optimizer
    optimizer.step()

    ### Testing
    model_1.eval() # Put the model in evaluation mode for testing (inference)

    # 1. Forward pass
    with torch.inference_mode():
        test_pred = model_1(X_test)

        # 2. Calculate the loss
        test_loss = loss_fn(test_pred, y_test)
    
    if epoch % 100 == 0:
        print(f"Epoch: {epoch} | Train loss: {loss} | Test loss: {test_loss}")
```