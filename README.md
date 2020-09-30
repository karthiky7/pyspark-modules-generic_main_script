# PySpark-Boilerplate
A boilerplate for writing PySpark Jobs

Pyspark project with modules having main-python.py script as generic for all EMR jobs:
1) go to C:\my-projects\python-modules-EMR\src\
2) zip -x main.py -r ./jobs.zip .
3)cd 3rdparty-libs &&  zip  -r ../libs.zip .  -- for using 3rd party python libraries
4)spark-submit --master yarn --deploy-mode cluster --num-executors 3 --executor-memory 2g --executor-cores 2 --py-files jobs.zip main.py --job wordcount
5)--py-files When you pass your zip/files with the --py-files flag, basically your resources will be transferred to temporary directory created on HDFS just for the lifetime of that application
  To add the dependencies to the PYTHONPATH so use if os.path.exists('jobs.zip'): sys.path.insert(0, 'jobs.zip') or  sc.addPyFile('jobs.zip')
      