# pyspark-on-macos

This is an walk-through of pyspark installation on MacOS. Steps are performed following the article here: [https://kevinvecmanis.io/python/pyspark/install/2019/05/31/Installing-Apache-Spark.html#home](https://kevinvecmanis.io/python/pyspark/install/2019/05/31/Installing-Apache-Spark.html#home)  
Didn’t follow only few steps, like JAVA_HOME was already set in my Mac. I was using miniconda instead of a plain python installation like mentioned in the article.

1. Downloaded and extracted the following packages under: /Users/lisan/server directory
* [spark-2.4.7-bin-hadoop2.7.tgz](https://www.apache.org/dyn/closer.lua/spark/spark-2.4.7/spark-2.4.7-bin-hadoop2.7.tgz)
* [scala-2.11.12.tgz](https://downloads.lightbend.com/scala/2.11.12/scala-2.11.12.tgz)
* [sbt-0.13.17.tgz](https://github.com/sbt/sbt/releases/download/v0.13.17/sbt-0.13.17.tgz)

2. These are the added environment variables in .bash_profile (/Users/lisan/.bash_profile) file  
>* export JAVA_HOME=`/usr/libexec/java_home -v 1.8`
>* export SPARK_HOME="/Users/lisan/server/spark-2.4.7-bin-hadoop2.7"
>* export SBT_HOME="/Users/lisan/server/sbt"
>* export SCALA_HOME="/Users/lisan/server/scala-2.11.12"
>* export PATH="/usr/local/sbin:$PATH"
>* export PATH=$JAVA_HOME/bin:$SBT_HOME/bin:$SCALA_HOME/bin:$SCALA_HOME/lib:$PATH
>* export PATH=$AVA_HOME/bin:$SPARK_HOME/bin:$SPARK_HOME/sbin:$PATH
>* export PYSPARK_PYTHON=python3
>* export PYTHONPATH=$SPARK_HOME/python/:$PYTHONPATH
>* export PYSPARK_DRIVER_PYTHON="jupyter"
>* export PYSPARK_DRIVER_PYTHON_OPTS="notebook"

3. Additionally installed py4j (needed to run java application from python) using *condo install* py4j from base environment. Also installed *findspark* (pip3 install findspark), just in case needed. Pip3 was used to install findspark as the package was not found when I tried *condo install findspark*. Findspark was not required as my import pyspark worked in Jupyter notebook anyway.

4. Verify JAVA_HOME and python3  
   >(base) Lisanuls-MacBook-Air:pyspark-on-macos lisan$ java -version  
   >java version "1.8.0_191"
   >Java(TM) SE Runtime Environment (build 1.8.0_191-b12)
   >Java HotSpot(TM) 64-Bit Server VM (build 25.191-b12, mixed mode)  
     
    >(base) Lisanuls-MacBook-Air:~ lisan$ which python3  
    >/Users/lisan/miniconda3/bin/python3
   
5. Type `jupyter notebook` to start the notebook.

6. import pyspark works both in pyspark shell and Jupyter notebook! Done!  
  
  
Additional references:  
[conda.io](https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html#removing-an-environment)  
[https://janakiev.com/blog/jupyter-virtual-envs/](https://janakiev.com/blog/jupyter-virtual-envs/)  
