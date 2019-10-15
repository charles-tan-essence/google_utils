# google_utils
Bunch of classes to make interacting with the official Google API Python Client even easier

## Step 1: Authentication

Start by getting the credentials.
Files needed:
- your keys in the json format
- the scopes in a list

For example:
```python
# first import the authenticator
from authentication.authenticator import Authenticator

keys = 'keys.json'
scopes = ['https://www.googleapis.com/auth/spreadsheets',
          'https://www.googleapis.com/auth/drive',]

authenticator = Authenticator(keys)
creds = authenticator.get_creds(scopes)

```

### SCOPES for OAuth 2.0
List of scopes can be found [here](https://developers.google.com/identity/protocols/googlescopes).
