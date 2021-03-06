# Suggestions on how to study TensorFlow 2.0

Author: Umberto Michelucci (umberto.michelucci@toelt.ai)
(Thanks to Feedback from Paolo Galeone https://github.com/galeone)

I will try to give some suggestions on how to approach the study of TensorFlow 2.0. 
In particular I will try to highlight the right order in which to tackle different parts. 
I will separate each part in sections, and in each sections try to put material that is useful to
study it.

## What is new in TensorFlow 2.0

Summarized the new features are

* Easy model building with Keras and __eager execution__ (activated by default in TF2.0).
* Robust model deployment in production on any platform.
* Powerful experimentation for research.
* Simplifying the API by cleaning up deprecated APIs and reducing duplicatio (__relevant in case you have code developed in 
TensorFlow 1.X and you need to convert it__)
* Load your data using `tf.data`. Training data is read using input pipelines which are created using` tf.data.` 
* Build, train and validate your model with `tf.keras`, or use Premade Estimators.
* TensorFlow Hub.
* Run and debug with __eager execution__, then use `tf.function` for the benefits of graphs. 
TensorFlow 2.0 runs with eager execution by default for ease of use and smooth debugging. 
Additionally, the `tf.function` annotation transparently translates your Python programs into TensorFlow graphs. 
* Use Distribution Strategies for distributed training. 
* hardware accelerators like CPUs, GPUs, and TPUs; you can enable training workloads to be distributed to 
single-node/multi-accelerator as well as multi-node/multi-accelerator configurations, including TPU Pods. 
* Export to `SavedModel`. TensorFlow will standardize on SavedModel as an interchange format for TensorFlow Serving, 
TensorFlow Lite, TensorFlow.js, TensorFlow Hub, and more.
* Tensorflow Datasets

Once you’ve trained and saved your model, you can execute it directly in your application or serve it using one 
of the deployment libraries:

* **TensorFlow Serving**: A TensorFlow library allowing models to be served over HTTP/REST or gRPC/Protocol Buffers.
* **TensorFlow Lite**: TensorFlow’s lightweight solution for mobile and embedded devices provides the capability 
to deploy models on Android, iOS and embedded systems like a Raspberry Pi and Edge TPUs.
* **TensorFlow.js**: Enables deploying models in JavaScript environments, such as in a web browser or server 
side through Node.js. TensorFlow.js also supports defining models in JavaScript and training directly 
in the web browser using a Keras-like API.

Possible link to check: [https://www.tensorflow.org/beta](https://www.tensorflow.org/beta)

# Order in which to approach the study of TF2.0

Assuming you have a good knowledge of Python, ML and you know (at least on a basic level) how TF 1.X works, I would suggest
the following order for studying TF 2.0 (splitted in __basics__ and __advanced__ topics)

## Basics

1. Tensors
2. Computational graphs basics (this is relevant when you are going to study how `@tf.function` works and how it creates a 
graph in the background. Unless you understand how Computational graphs are working, you will not really understand
how `@tf.function` is working)
3. Eager Execution (basics and subtelties)
4. `tf.Variable` (aka no need to initialize them anymore in eager mode)
5. Keras basics (`Sequential()` models, `.compile()` and `.fit()` calls)
6. Keras functional APIs 
7. `tf.data.Dataset` and data processing pipelines


## Advanced

1. Model subclassing
2. Custom layers in Keras
3. Custom callbacks in Keras
4. `@tf.function`
5. Keras metrics
6. Autodifferentiation (`tf.GradientTape()`) and custom training loops
7. Custom layers and models
8. Save and load models
9. Using CPUs, GPUs and TPUs (hardware acceleration)

## Subjects that are related to production-grade models

The following aspects are relevant when you need to deploy models in a productive environment 
and therefore needs additional components. Those are not relevant for everyone.

1. Distributed training
2. TFX (create and manage a production pipeline)


If you master the __basics__ you are already well underway to master TensorFlow 2.0 and can 
already build some quite complicated models. The moment you want to use more complex 
architectures (for example Multi Task Learning, or networks with multiple inputs or outputs) 
then the Keras functional APIs comes to rescue and will give you quite some flexibility.
