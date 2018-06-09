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
pd.set_option("display.max_columns", 100)
```
