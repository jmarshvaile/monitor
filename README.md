# README

## Disclaimer

This repo is FULL of bad ideas.
- Do not read this README
- Do not run my code
- Do not listen to my recommendations (except for the ones in this bullet list)

Okay, now that you are gone I will continue ...

## Installation

Install Docker if you do not already have it installed.

## Environment

I am using a docker image called [jupyter/scipy-notebook](https://hub.docker.com/r/jupyter/scipy-notebook/) which creates a linux container with JupyterLab.

I've modified the container to include `iputils-ping` in order to use the linux `ping` shell command.

## Setup

Open a new terminal and execute the following. The `%cd%` or `$PWD` can be changed to a local directory of your choosing.

Windows:
```
docker run -d -v %cd%:/home/jovyan/work -e GRANT_SUDO=yes --user root -p 8888:8888 jupyter/scipy-notebook
```
Linux:
```
docker run -d -v $PWD:/home/jovyan/work -e GRANT_SUDO=yes --user root -p 8888:8888 jupyter/scipy-notebook
```

With a terminal open running inside the new container, execute the following commands to install `iputils-ping`.
```
apt-get update -y
apt-get install -y iputils-ping
```

You're ready to go. Open JupyterLab.

## JupyterLab

If the matplotlib magic `%matplotlib widget` doesn't work, you may need to enable third party extensions in JupyterLab's extension manager.

You will need to manually run each cell, allowing the plot to fully appear before running the next cell.

## Shutting Down

The `while` loop is infinite. You must interrupt the kernal to stop it.

After exiting the container, Windows users will need to free up the memory allocated to virtual environments. You can do this in a new terminal with the following command.
```
wsl --shutdown
```
