# django-api-serverless
Django API in lambda function using zappa as deployment tool

# Usage Instructions

### First of all, install and create virtual environment:

```
> virtualenv venv
```

In Windows type:

```
> .\venv\Scripts\activate
```

In Mac/Linux type:

```
> source venv/bin/activate
```

### Install required packages

```
(venv) > pip install -r requirements.txt
```

### If you are using VSCode

Install Official Python extension for VSCode

https://marketplace.visualstudio.com/items?itemName=ms-python.python

Then, in VSCode type: 

On PC:
```Shift``` + ```Control``` + ```P```

On Mac:
```Shift``` + ```Command``` + ```P```

Type : Python: Select Interpreter

Choose your virtual env.

#### Debug it!

Click Debug button e choose Add configuration...

Select Python as environment and Django as debug configuration.

Hit play button to start debugging.

Note: If never-ending load occurs, just remove the option ```--nothreading``` from ```.vscode\launch.json``` file.

### Or if you're in plain command line

Just type:

```
> python manage.py runserver
```

### Check if it is working

Open your web browser and type:

```
http://localhost:8000/v1/endpoint
```

### Now, lets deploy it!

First you need to configure ```~/.aws/configure``` credentials. So create a ```configure``` file into ```.aws``` directory under your user's home folder with following content:

```
[default]
aws_access_key_id = YOURACCESSKEYGOESHERE
aws_secret_access_key = YourSecretAccessKeyGoesHere
```

In zappa_settings.json file update domain item to reflect your domain configuration:

Change it here:

```
"domain": "api-dev.yourdomain.com",
```

Now simply execute:

```
(venv) > zappa deploy dev
```

Or for production:

```
(venv) > zappa deploy production
```

Finally go to your DNS configuration and create a new CNAME configuration pointing to where API Gateway tells you to.

#### More Info

https://github.com/Miserlou/Zappa
