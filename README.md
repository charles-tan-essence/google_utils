# google_utils
Bunch of classes to make interacting with the official Google API Python Client even easier. Is this a wrapper?

## Step 1: Installation

(To-do: make the repo installable as a package via pip)

Until then:
1. Clone the repository
```
$ git clone https://github.com/cetyz/google_utils
```
2. Use this directory as the working directory.
```
$ cd google_utils
```
3. Use Pip to install the required packages.
```
$ pip install -r requirements.txt
```
4. Use it! Refer to the next steps.

## Step 2: Authentication

Start by getting the credentials.
Files needed:
- your keys in the json format
- the scopes in a list. Scopes can be found [here](https://developers.google.com/identity/protocols/googlescopes).

```python
# first import the authenticator
from authentication.authenticator import Authenticator

keys = 'keys.json'
scopes = ['https://www.googleapis.com/auth/spreadsheets',
          'https://www.googleapis.com/auth/drive',]

authenticator = Authenticator(keys)
creds = authenticator.get_creds(scopes)

```

The credentials (creds) will then be used when initializing the other tools.

## Step 3: Using the Classes

Use the creds to initialize the Classes that you need. Do make sure the creds have been created with the necessary scopes.
For instance, the spreadsheets scopes will be needed to use the SheetManager class found in the sheets folder.

```python
from sheets.sheetmanager import SheetManager

# initialize the sheets_manager with the creds we obtained above from authenticator.get_creds(scopes)
sheets_manager = SheetManager(creds)

# example usage
spreadsheetId = 'xxxxxxxxxxxxxxxxxx'
data_range = 'Sheet!A1:b4'

# returns values as a dataframe with first row as column names
sheet_values = sheets_manager.get_values(spreadsheetId=spreadsheetId, data_range=data_range) 
```