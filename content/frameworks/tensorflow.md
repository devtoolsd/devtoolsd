---
name: TensorFlow
slug: tensorflow
language: python
description: End-to-end open-source ML platform from Google — model building, training, deployment across CPU, GPU, TPU, and mobile.
logo: https://upload.wikimedia.org/wikipedia/commons/2/2d/Tensorflow_logo.svg
website: https://tensorflow.org
github: tensorflow/tensorflow
year: 2015
pricing: free
open_source: true
license: Apache-2.0
tool_type: data
tags: [ml, ai, deep-learning, neural-networks, gpu, python, google]
related_frameworks: [pytorch, keras, jax]
features:
  - "Keras high-level API — define models in minutes with `Sequential` and `Model`"
  - "TensorFlow Serving for production model serving with REST and gRPC"
  - "TensorFlow Lite for mobile and embedded deployment (iOS, Android, Raspberry Pi)"
  - "TensorFlow.js for in-browser inference without a server"
  - "Distributed training across multiple GPUs and TPU pods"
  - "TensorBoard for training visualisation and hyperparameter tuning"
  - "SavedModel format for language-agnostic model export"
  - "Full pipeline tools — TFX, TensorFlow Data Validation, TensorFlow Transform"
install:
  pip: "pip install tensorflow"
  conda: "conda install -c conda-forge tensorflow"
---

TensorFlow is Google's production ML platform, covering the full pipeline from research to deployment. TensorFlow Serving, TensorFlow Lite, and TensorFlow.js handle server, mobile, and browser inference respectively. Since TF2, Keras is TensorFlow's high-level API, making model definition intuitive while TensorFlow handles the underlying computation graph and hardware acceleration. TensorFlow's production tooling (TFX, TF Serving, TFLite) remains the most mature in the ecosystem.

## Quick start

```bash
pip install tensorflow
```

```python
import tensorflow as tf
from tensorflow import keras

# Build a simple image classifier
model = keras.Sequential([
    keras.layers.Input(shape=(28, 28, 1)),
    keras.layers.Conv2D(32, (3, 3), activation='relu'),
    keras.layers.MaxPooling2D(),
    keras.layers.Flatten(),
    keras.layers.Dense(64, activation='relu'),
    keras.layers.Dense(10, activation='softmax'),
])

model.compile(
    optimizer='adam',
    loss='sparse_categorical_crossentropy',
    metrics=['accuracy'],
)

# Load MNIST dataset
(x_train, y_train), (x_test, y_test) = keras.datasets.mnist.load_data()
x_train, x_test = x_train / 255.0, x_test / 255.0
x_train = x_train[..., tf.newaxis]
x_test = x_test[..., tf.newaxis]

model.fit(x_train, y_train, epochs=5, validation_data=(x_test, y_test))

# Save the model
model.save('mnist_model.keras')
```

## When to use

TensorFlow is the right choice when production deployment is the primary concern — TF Serving, TFLite for mobile, and TFX pipelines are unmatched. Google's TPU infrastructure also runs TensorFlow natively. For research and experimentation, PyTorch has become the dominant choice due to its Pythonic API and HuggingFace ecosystem. If you're primarily using pretrained models (LLMs, vision transformers), PyTorch + HuggingFace Transformers is more practical.
