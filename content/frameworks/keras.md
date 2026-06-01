---
name: Keras
slug: keras
language: python
description: High-level deep learning API — simple model building with backends for TensorFlow, PyTorch, and JAX.
logo: https://upload.wikimedia.org/wikipedia/commons/a/ae/Keras_logo.svg
website: https://keras.io
github: keras-team/keras
year: 2015
pricing: free
open_source: true
license: Apache-2.0
tool_type: data
tags: [ml, deep-learning, neural-networks, python, tensorflow, multi-backend]
related_frameworks: [tensorflow, pytorch, jax]
features:
  - "Sequential and Functional API for quick model prototyping"
  - "Backend-agnostic — run on TensorFlow, PyTorch, or JAX"
  - "Built-in layers: Dense, Conv2D, LSTM, Transformer, Attention"
  - "Callbacks — EarlyStopping, ModelCheckpoint, TensorBoard"
  - "`model.fit()` training loop handles batching, validation, and epochs"
  - "Keras Tuner for hyperparameter search"
  - "Export to TF SavedModel, ONNX, or TFLite"
  - "Pre-trained models via `keras.applications` (ResNet, EfficientNet, MobileNet)"
install:
  pip: "pip install keras tensorflow"
---

Keras provides an intuitive API for building neural networks with `Sequential` models, functional API, and subclassing. Keras 3 is backend-agnostic — the same model code runs on TensorFlow, PyTorch, or JAX. As TensorFlow's official high-level API it is the first framework most practitioners encounter when learning deep learning, offering a much gentler learning curve than raw PyTorch.

## Quick start

```bash
pip install keras tensorflow
```

```python
import keras
import numpy as np

# Sequential model for image classification
model = keras.Sequential([
    keras.layers.Input(shape=(28, 28, 1)),
    keras.layers.Conv2D(32, 3, activation='relu'),
    keras.layers.MaxPooling2D(),
    keras.layers.Conv2D(64, 3, activation='relu'),
    keras.layers.GlobalAveragePooling2D(),
    keras.layers.Dense(10, activation='softmax'),
])

model.compile(
    optimizer='adam',
    loss='sparse_categorical_crossentropy',
    metrics=['accuracy'],
)

model.summary()

# Load MNIST and train
(x_train, y_train), (x_test, y_test) = keras.datasets.mnist.load_data()
x_train = x_train.astype('float32') / 255.0
x_test = x_test.astype('float32') / 255.0

history = model.fit(
    x_train[..., np.newaxis], y_train,
    epochs=5,
    validation_split=0.1,
    callbacks=[keras.callbacks.EarlyStopping(patience=2, restore_best_weights=True)],
)

loss, acc = model.evaluate(x_test[..., np.newaxis], y_test)
print(f"Test accuracy: {acc:.3f}")

# Save the model
model.save('mnist_model.keras')
```

## When to use

Keras is the recommended starting point for deep learning — its simple API gets you from idea to trained model in minutes. Keras 3's multi-backend support means you write once and can switch between TensorFlow and PyTorch. For production deployment at scale, you'll often move from Keras to lower-level PyTorch for fine-grained control or use TF Serving via the Keras SavedModel. For very large models (LLMs), use HuggingFace Transformers which wraps PyTorch/TF.
