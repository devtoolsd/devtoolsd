---
name: PyTorch
slug: pytorch
language: python
description: Dynamic neural network framework from Meta — the dominant platform for ML research and increasingly for production.
logo: https://upload.wikimedia.org/wikipedia/commons/1/10/PyTorch_logo_icon.svg
website: https://pytorch.org
github: pytorch/pytorch
year: 2016
pricing: free
open_source: true
license: BSD-2-Clause
tool_type: data
tags: [ml, ai, deep-learning, research, gpu, python, meta, dynamic]
related_frameworks: [tensorflow, keras, jax]
features:
  - "Dynamic computation graph — define-by-run, debug with standard Python tools"
  - "Autograd — automatic differentiation for any computation graph"
  - "CUDA acceleration — move tensors to GPU with `.to('cuda')`"
  - "`torch.nn` module system for building neural network layers"
  - "DataLoader and Dataset abstractions for efficient data pipelines"
  - "TorchScript for exporting models to production without Python"
  - "torch.compile (PyTorch 2.0) for significant speedups with no code changes"
  - "Vast ecosystem — HuggingFace Transformers, Lightning, torchvision, torchaudio"
install:
  pip: "pip install torch torchvision torchaudio"
  conda: "conda install pytorch torchvision torchaudio pytorch-cuda=12.1 -c pytorch -c nvidia"
---

PyTorch's dynamic computation graph ("define-by-run") makes debugging neural networks intuitive — you use standard Python control flow and `print()` statements. It became the dominant framework for ML research and, with TorchServe and `torch.compile`, is now widely used in production at Meta, Tesla, and OpenAI. Most modern LLMs (including GPT, LLaMA, and Mistral) are built and trained in PyTorch.

## Quick start

```bash
pip install torch torchvision
```

```python
import torch
import torch.nn as nn
import torch.optim as optim

# Define a simple feedforward network
class Net(nn.Module):
    def __init__(self):
        super().__init__()
        self.fc1 = nn.Linear(784, 128)
        self.fc2 = nn.Linear(128, 10)
        self.relu = nn.ReLU()

    def forward(self, x):
        x = self.relu(self.fc1(x))
        return self.fc2(x)

model = Net()
optimizer = optim.Adam(model.parameters(), lr=1e-3)
criterion = nn.CrossEntropyLoss()

# Training loop
for epoch in range(10):
    for batch_x, batch_y in dataloader:
        optimizer.zero_grad()
        output = model(batch_x)
        loss = criterion(output, batch_y)
        loss.backward()
        optimizer.step()
    print(f"Epoch {epoch+1}, Loss: {loss.item():.4f}")

# Save and load
torch.save(model.state_dict(), 'model.pt')
model.load_state_dict(torch.load('model.pt'))
```

## When to use

PyTorch is the first choice for deep learning research, fine-tuning pretrained models (via HuggingFace), and production ML systems. Its Pythonic API and dynamic graphs make experimentation fast. TensorFlow/Keras is still used in mobile deployment (TFLite) and some production pipelines, but PyTorch's HuggingFace integration and `torch.compile` speedups have made it the default in most new ML projects. JAX is worth considering for large-scale TPU training.
