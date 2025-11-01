+++
date = '2025-11-01T12:12:33+08:00'
draft = false
title = 'Running Jupyter Notebook by Docker'
+++

## Run Jupyter in a container

reference:

* [Jupyter container guide](https://docs.docker.com/guides/jupyter/)

### Prerequisites
- Having [doocker](https://www.docker.com/) or Docker Desktop installed according to your operating system.


### Running

```bash
docker run --rm -p 8889:8888 quay.io/jupyter/base-notebook start-notebook.py --NotebookApp.token='my-token'
```
 - `-p 8889:8888` host port mapping to container port
 - `start-notebook.py --NotebookApp.token='my-token'` customizing your token.
 - The `start-notebook.py` script configures the internal container and then runs `jupyter lab` command (see [here](https://jupyter-docker-stacks.readthedocs.io/en/latest/using/common.html#jupyter-server-options)).
- We can use the `crtl + c` command to stop the terminal process.

Letting the container reading host folder, run:

```bash
docker run --rm -p 8889:8888 -v "$(pwd):/home/jovyan/work" quay.io/jupyter/base-notebook start-notebook.py --NotebookApp.token='my-token'
```
 - `-v` maps the current working directory to `/home/jovyan/work` folder of the container.
 - Your can edit,save and run notebooks in the container. Files will be saved on the volume except the packages that you have newly installed during the running of the container. You will have to install them everytime when restarting the container and running the code that you previously saved.

To avoid the problem, we can define an enviroment in a file named `Dockerfile`. Below the matplotlib and scikit-learn packages are what we want to added to the default environment:

```bash
# syntax=docker/dockerfile:1

FROM quay.io/jupyter/base-notebook
RUN pip install --no-cache-dir matplotlib scikit-learn
```

Then build the defined envrionment into an image:

```bash
docker build -t my-jupyter-image .
```
 - `-t` sets the name and tag of the image, using the current working direcotry `.`.


 More:  [reference](https://docs.docker.com/guides/jupyter/).

