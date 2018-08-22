# pyspark_fun
Things I never remember

### Plotly for Jupyter

```
from plotly.offline import download_plotlyjs, init_notebook_mode, iplot
import plotly.graph_objs as go
init_notebook_mode(connected=True)
```
### Columns in Jupyter for Pandas DF

```
import pandas as pd
pd.set_option('display.max_columns', 100)
pd.set_option('display.max_colwidth', -1)
pd.set_option('display.max_rows', 200) # first 100 last 100
```
### Clean docker
```
docker rm $(docker ps -a -q)
docker rmi $(docker images -q)
```
