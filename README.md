# Docker for Data Science

Docker image for working with Anaconda.

More details you can find in article: [Docker for Data Science](https://medium.com/@evheniybystrov/docker-for-data-science-9c0ce73e8263).

# Instructions for using miniconda

1. ```git clone git@github.com:WittmannJ/docker-data-science.git```
2. ```cd miniconda```
3. ```docker build -t docker-data-science-lite .```
4. ```docker run --name docker-data-science-lite -p 127.0.0.1:8888:8888 -v "$PWD/notebooks:/opt/notebooks" -d docker-data-science-lite```
4. Open Browser
6. Navigate to ```localhost:8888```
7. Passwort is ```root```
8. All new files that you create in jupyter notebook get saved into ```<local path to git repo>/docker-data-science/miniconda/notebooks```
