# We will use Ubuntu for our image
FROM ubuntu

# Updating Ubuntu packages
RUN apt-get update && yes|apt-get upgrade

# Adding wget and bzip2
RUN apt-get install -y wget bzip2

# Anaconda installing
#RUN wget https://repo.continuum.io/archive/Anaconda3-5.0.1-Linux-x86_64.sh
RUN wget https://repo.continuum.io/miniconda/Miniconda3-4.7.10-Linux-x86_64.sh
#RUN bash Anaconda3-5.0.1-Linux-x86_64.sh -b
RUN bash Miniconda3-4.7.10-Linux-x86_64.sh -b
RUN rm Miniconda3-4.7.10-Linux-x86_64.sh

# Set path to conda
ENV PATH /root/miniconda3/bin:$PATH

# Updating Anaconda packages
RUN conda install pandas
RUN conda install matplotlib
RUN conda install plotly
RUN conda install jupyter -y --quiet
RUN conda install scikit-learn
RUN conda install -c conda-forge jupytext
RUN conda install seaborn
RUN conda install -c conda-forge missingno
RUN conda update conda
#RUN conda update miniconda
RUN conda update --all

# Configuring access to Jupyter
RUN mkdir /opt/notebooks
RUN jupyter notebook --generate-config --allow-root
RUN echo "c.NotebookApp.password = u'sha1:6a3f528eec40:6e896b6e4828f525a6e20e5411cd1c8075d68619'" >> /root/.jupyter/jupyter_notebook_config.py

RUN echo "c.NotebookApp.contents_manager_class='jupytext.TextFileContentsManager'" >> /root/.jupyter/jupyter_notebook_config.py

RUN echo "c.ContentsManager.default_jupytext_formats = 'ipynb,md'" >> /root/.jupyter/jupyter_notebook_config.py


# Jupyter listens port: 8888
EXPOSE 8888

# Set working directory
WORKDIR /opt/notebooks

# Copy examples
ADD notebooks /opt/notebooks

# Run Jupytewr notebook as Docker main process
CMD ["jupyter", "notebook", "--allow-root", "--notebook-dir=/opt/notebooks", "--ip='*'", "--port=8888", "--no-browser"]
