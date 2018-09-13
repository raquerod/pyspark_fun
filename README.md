# funs
Things I never remember

### Jupyter

#### Plotly
```
from plotly.offline import download_plotlyjs, init_notebook_mode, iplot
import plotly.graph_objs as go
init_notebook_mode(connected=True)
```
### Columns for Pandas DF

```
import pandas as pd
pd.set_option('display.max_columns', 100)
pd.set_option('display.max_colwidth', -1) # gets rid of ...
pd.set_option('display.max_rows', 200) # first 100 last 100
```
### Docker

#### Clean images
```
docker rm $(docker ps -a -q)
docker rmi $(docker images -q)
```
### AWS

#### Copy one bucket into another one in S3
```
aws s3 sync s3://bucket1/path/to/file s3://bucket2/path/to/file
```
