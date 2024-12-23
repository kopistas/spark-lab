FROM jupyter/pyspark-notebook:latest

# Set environment variables for Spark
ENV SPARK_HOME=/usr/local/spark
ENV PATH=$SPARK_HOME/bin:$PATH

USER root
RUN apt-get update && apt-get install -y \
    openjdk-8-jdk \
    && pip install psycopg2-binary

# Add PostgreSQL JDBC driver

RUN wget https://jdbc.postgresql.org/download/postgresql-42.7.4.jar -P /usr/local/spark/jars/

# Set the working directory for Jupyter
WORKDIR /home/jovyan/work

# Expose Jupyter and Spark UI ports
EXPOSE 8888 8080

# Start Jupyter notebook on container start
CMD ["start-notebook.sh", "--NotebookApp.ip='*'", "--NotebookApp.port=8888", "--NotebookApp.allow_root=True"]