## Create a complete Machine Learning web application using React and Flask

Karan Bhanot in his article on towardsdatascience.com describes a nice template of serving machine learning functionality over a Flask web application that has a React front end.

The code repository is [github.com/kb22/ML-React-App-Template](github.com/kb22/ML-React-App-Template).

In order to run the example use case of iris flowers prediction, you clone the repository and run the following commands:\
Terminal 1
```
$ cd using
$ yarn install
$ sudo npm install -g serve
$ npm run build
$ serve -s build -l 3000
```

Terminal 2
```
$ cd service
$ FLASK_APP=app.py flask run
```

The run command throws an error:\
from werkzeug import cached_property\
Import_Error : cannot import name 'cached_property'

To fix this error, two changes are required.\
1) requirements.txt\
change flask-restplus==0.12.1\
to flask-restx==0.2.0

$ pip3 install -r requirements.txt

2) app.py\
In the line: from flask_restplus import Api, Resource, fields\
change flask_restplus to flask_restx

I have forked the repository and made the changes, you can check out and run the application without errors. It's available at:\
[https://github.com/mh-github/ML-React-App-Template](https://github.com/mh-github/ML-React-App-Template)