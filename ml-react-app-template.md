## Create a complete Machine Learning web application using React and Flask

Karan Bhanot in his article on [towardsdatascience.com](https://towardsdatascience.com/create-a-complete-machine-learning-web-application-using-react-and-flask-859340bddb33) describes a nice template of serving machine learning functionality over a Flask web application that has a React front end.

The code repository is [https://github.com/kb22/ML-React-App-Template](https://github.com/kb22/ML-React-App-Template).

In order to run the example use case of iris flowers prediction, you clone the repository. Open two terminals; in both of them, cd into example/iris-data-classifier/ML-React-App-Template and run the following commands:\
Terminal 1
```
$ cd ui
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

After executing the command 'npm run build' in Terminal 1 and starting the servers in both the terminals, you can access the application at\
http://localhost:3000

I have forked the repository and made the changes, you can check out and run the application without errors. It's available at:\
[https://github.com/mh-github/ML-React-App-Template](https://github.com/mh-github/ML-React-App-Template)