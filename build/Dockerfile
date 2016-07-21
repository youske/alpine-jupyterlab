# Alpine Linux miniconda with Jupyter
# youske/alpine-jupyter based

FROM youske/alpine-jupyter:latest
MAINTAINER youske miyakoshi <youske@gmail.com>

#ENV JUPYTER_HOME=/jupyter_notebook \
#    LANG=C.UTF-8\
#    PORT=8888
#ENV PACKAGE='sudo gawk git ncurses ca-certificates' \
#    BUILD_PACKAGE='wget build-base musl-dev linux-headers' \
#    CONDA_PACKAGE='jupyter matplotlib dateutil pyyaml pymysql sqlalchemy psycopg2 pandas scipy numpy cython bokeh xlrd xlutils openpyxl ipywidgets' \
#    PIP_PACKAGE='psutil jupyter_cms metakernel_bash metakernel_python redis_kernel pandas-td pandas-datareader ' \
#    WIDGET_PACKAGE='ipyleaflet bqplot pythreejs'

#RUN apk update --no-cache && apk add ${PACKAGE} --no-cache && apk add ${BUILD_PACKAGE} --no-cache -t buildpack
#RUN conda update -q -y conda && conda install -y ${CONDA_PACKAGE} && conda clean -itpsly
#RUN pip install -U ${PIP_PACKAGE} ${WIDGET_PACKAGE}

# jupyter lab
RUN pip install jupyterlab && \
    jupyter serverextension enable --py jupyterlab

WORKDIR /tmp
USER root
# remove buildpack
RUN apk del buildpack --no-cache && rm -rf /tmp/* /var/cache/apk/*

EXPOSE ${PORT}
WORKDIR /home/admin
ENTRYPOINT ["switch","shell=su admin -c /bin/bash","--","switch","root=/bin/bash","--","/init"]
CMD ["gosu","admin","jupyter", "lab", "--no-browser","--ip=*"]
