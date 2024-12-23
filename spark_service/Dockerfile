FROM jupyter/pyspark-notebook:latest

# Set environment variables for Spark
ENV SPARK_MODE=master
ENV SPARK_HOME=/usr/local/spark
ENV PATH=$SPARK_HOME/bin:$PATH
ENV SPARK_MASTER_PORT=7077

USER root
RUN apt-get update && apt-get install -y \
    openjdk-8-jdk \
    && pip install psycopg2-binary

# Set the working directory for Jupyter
WORKDIR /home/jovyan/work

# Expose Jupyter and Spark UI ports
EXPOSE 8888 8080 7077

# Add PostgreSQL JDBC driver
RUN wget https://jdbc.postgresql.org/download/postgresql-42.7.4.jar -P /home/jovyan/work


# Start Jupyter notebook on container start
CMD ["start-notebook.sh", "--NotebookApp.ip='*'", "--NotebookApp.port=8888", "--NotebookApp.allow_root=True"]