# funs
Things I never remember

### Jupyter

#### Launching Pyspark locally in Jupyter
```
PYSPARK_DRIVER_PYTHON=jupyter PYSPARK_DRIVER_PYTHON_OPTS=notebook pyspark --packages org.apache.hadoop:hadoop-aws:2.8.1,org.postgresql:postgresql:42.1.3.
```

#### Plotly
```
from plotly import offline as py
import plotly.graph_objs as go
py.init_notebook_mode(connected=False)
```
#### Columns for Pandas DF

```
import pandas as pd
pd.set_option('display.max_columns', 100)
pd.set_option('display.max_colwidth', -1) # gets rid of ...
pd.set_option('display.max_rows', 200) # first 100 last 100
```
### Docker

#### Clean images
```
docker images
docker rm $(docker ps -a -q)
docker rmi $(docker images -q)
```
#### Build Image
```
docker build -t REPOSITORY_NAME:TAG /path/to/image
```
### AWS

#### Copy one bucket into another one in S3
```
aws s3 sync s3://bucket1/path/to/file s3://bucket2/path/to/file
```

### GIT

#### Remove the last commit
```
git reset --hard HEAD^
```
