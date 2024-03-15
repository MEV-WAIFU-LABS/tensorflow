## ⚛️🔋 Quantum Computing Tensorflow in K8s

<br>

### 👉 this repository contains my work deploying a quantum computing version of tensorflow in kubernetes.

<br>

---

### Theoretical Introduction

<br>

* With the recent progress in the development of quantum computing, the development of new quantum ML models could have a profound impact on the world’s biggest problems, leading to breakthroughs in the areas of medicine, materials, sensing, and communications.

* TFQ provides the tools for bringing the quantum computing and machine learning research together to control and model natural or artificial quantum systems; e.g. (NISQ) processors with ~50 - 100 qubits.

* TFQ integrates Cirq with TensorFlow, and offers high-level abstractions for the design and implementation of both discriminative and generative quantum-classical models by providing quantum computing primitives compatible with existing TensorFlow APIs, along with high-performance quantum circuit simulators.

* A quantum model has the ability to represent and generalize data with a quantum mechanical origin:
    - Quantum data exhibits superposition and entanglement, leading to joint probability distributions that could require an exponential amount of classical computational resources to represent or store.
    - Quantum data generated by NISQ processors are noisy and are typically entangled just before the measurement occurs. However, applying quantum machine learning to noisy entangled quantum data can maximize extraction of useful classical information. 


* TFQ contains the basic structures, such as qubits, gates, circuits, and measurement operators that are required for specifying quantum computations. User-specified quantum computations can then be executed in simulation or on real hardware.

* TFQ allows researchers to construct quantum datasets, quantum models, and classical control parameters as tensors in a single computational graph. The outcome of quantum measurements, leading to classical probabilistic events, is obtained by TensorFlow Ops. Training can be done using standard Keras functions.

* A key feature of TensorFlow Quantum is the ability to simultaneously train and execute many quantum circuits. This is achieved by TensorFlow’s ability to parallelize computation across a cluster of computers, and the ability to simulate relatively large quantum circuits on multi-core computers. 

<br>

--- 


### Steps:

<br>

#### Prepare a quantum dataset

- Quantum data is loaded as tensors (a multi-dimensional array of numbers). 
- Each quantum data tensor is specified as a quantum circuit written in Cirq that generates quantum data on the fly. 
- The tensor is executed by TensorFlow on the quantum computer to generate a quantum dataset.

#### Evaluate a quantum neural network model 

- The researcher can prototype a quantum neural network using Cirq that they will later embed inside of a TensorFlow compute graph. 
- Parameterized quantum models can be selected from several broad categories based on knowledge of the quantum data's structure. 
- The goal of the model is to perform quantum processing in order to extract information hidden in a typically entangled state. 

#### Sample or Average 

- Measurement of quantum states extracts classical information in the form of samples from a classical random variable. 
- The distribution of values from this random variable generally depends on the quantum state itself and on the measured observable. 
- As many variational algorithms depend on mean values of measurements, also known as expectation values, TFQ provides methods for averaging over several runs involving steps (1) and (2).

#### Evaluate a classical neural networks model 

- Once classical information has been extracted, it is in a format amenable to further classical post-processing.
- As the extracted information may still be encoded in classical correlations between measured expectations, classical deep neural networks can be applied to distill such correlations.

#### Evaluate Cost Function 

- Given the results of classical post-processing, a cost function is evaluated. 
- This could be based on how accurately the model performs the classification task if the quantum data was labeled, or other criteria if the task is unsupervised.

#### Evaluate Gradients & Update Parameters 

- After evaluating the cost function, the free parameters in the pipeline should be updated in a direction expected to decrease the cost.
- This is most commonly performed via gradient descent.

<br>

-----

### Pre-requisites

<br>

* [Vagrant](https://www.vagrantup.com/).
* [Virtual Box](https://www.virtualbox.org/).
* [Kubeflow and MiniKF](https://www.kubeflow.org/docs/other-guides/virtual-dev/getting-started-minikf/).
* [TensorFlow Quantum](https://github.com/tensorflow/quantum/blob/master/docs/install.md).


