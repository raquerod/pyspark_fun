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
aws s3 sync s3://bucket/path/to/file s3://bucket2/path/to/file
```

#### Remove keys
```
aws s3 rm s3://bucket/path/to/file --recursive
```

### GIT

#### Remove the last commit
```
git reset --hard HEAD^
```

### Google Sheets
```
import pygsheets

def gsheets_client() -> pygsheets.client.Client:
    client_secret = '{ "installed":{"client_id":"",
                       "project_id":"",
                       "auth_uri":"https://accounts.google.com/o/oauth2/auth",
                       "token_uri":"https://accounts.google.com/o/oauth2/token",
                       "auth_provider_x509_cert_url":"https://www.googleapis.com/oauth2/v1/certs",
                       "client_secret":"",
                       "redirect_uris":["urn:ietf:wg:oauth:2.0:oob","http://localhost"]}}'
    open('/tmp/client_secret.json', 'w').write(client_secret)
    return pygsheets.authorize(outh_file='/tmp/client_secret.json', outh_nonlocal=True)

def write_google_sheet(url, *, df, title, mode='overwrite'):
    gs = gsheets_client()
    spreadsheet = gs.open_by_url(url)

    header = [str(x) for x in df.columns]
    values = df.rdd.map(lambda row: [str(x) if x else '' for x in row]).collect()

    if mode == 'overwrite':
        try:
            worksheet = spreadsheet.worksheet_by_title(title)
        except WorksheetNotFound:
            worksheet = None
    else:
        worksheet = None

    if worksheet is None:
        worksheet = spreadsheet.add_worksheet(title=title, rows=1, cols=len(header))

    worksheet.resize(rows=1, cols=len(header))
    worksheet.update_row(index=1, values=header)
    worksheet.insert_rows(row=1, values=values, inherit=True)
    return worksheet
```
