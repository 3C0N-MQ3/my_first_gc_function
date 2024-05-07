---
jupyter:
  jupytext:
    cell_metadata_filter: -all
    main_language: python
    text_representation:
      extension: .md
      format_name: markdown
      format_version: '1.3'
      jupytext_version: 1.16.1
---

# My first Google Cloud Function
<!-- #region -->
If you have a nice `base` environment in conda, you can clone it to create a new environment for this project.
To do so, open the `anaconda powershell prompt` and run the following command:

```bash
conda create --my-first-gcf --clone base
```

Then, activate the new environment:

```bash
conda activate my-first-gcf
```

Now, install the required packages:

```bash
pip install functions-framework flask
```

This packages will be managed by the `conda` environment, so you can deactivate it and activate it whenever you want.
<!-- #endregion -->
<!-- #region -->
Create a new folder for the project and create a new file called `main.py`.

```bash
mkdir my-first-gcf
cd my-first-gcf
touch main.py
```

In this new file, write the following code:
<!-- #endregion -->
```python
# Brief example of how to use the package `functions_framework` from Google
# Cloud Functions to create a simple HTTP function.
import flask
import functions_framework

# The idea is to translate a function without having to write the HTTP server
# or complicated request handling logic.

# class flask.Request(environ, populate_request=True, shallow=False)
# Default request object used by default in Flask. Remembers the matched
# endpoints and view arguments. 
def hello_world(request: flask.Request) -> flask.typing.ResponseReturnValue:
    """Show a `Hello, World!` message in the browser for each request.

    Args:
        request (flask.Request): The request object. Instantiated by Flask 
        when a request is received.

    Returns:
        flask.typing.ResponseReturnValue: The response object. Instantiated by
        Flask to send the response back to the client.
    """
    return "Hello, World!"
```

<!-- #region -->
To test locally, run the following command in the `anaconda powershell prompt`:

```bash
functions-framework --target hello_world --debug
```

Then, in a web browser, navigate to `http://localhost:port/` to see the output.
Each time you refresh the page, is like sending a new request to the server.
<!-- #endregion -->
Further reading:
- [`functions-framework` package](https://github.com/GoogleCloudPlatform/functions-framework-python)
- [`flask.Request` class](https://flask.palletsprojects.com/en/3.0.x/api/#incoming-request-data)
