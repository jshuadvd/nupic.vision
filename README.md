# NuPIC Vision Toolkit

This tool kit is intended to help people who are interested in using Numenta's NuPIC on vision problems.

## Running MNIST Experiment

1. Install nupic.vision and it's dependencies
    ```
    pip install -e .
    ```

2. Prepare MNIST data
    ```
    cd src/nupic/vision/mnist
    ./extract_mnist.sh
    mkdir mnist
    mv mnist_extraction_source/training mnist/
    mv mnist_extraction_source/testing mnist/
    python ./convertImages.py mnist
    ./create_training_sample.sh
    ```
3. Run experiment
    ```
    python run_mnist_experiment.py --data-dir mnist
    ```

### Using Docker

1. Build docker image
    ```
    docker build -t nupic.vision .
    ```
2. Run MNIST experiment (See [Dockerfile](./Dockerfile) for details)
    ```
    docker run nupic.vision 
    ```