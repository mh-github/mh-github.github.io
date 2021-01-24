## Build a React + Flask App that Suggests Novel Novels with a Python Graph

Jay Franck in his [article](https://towardsdatascience.com/build-a-react-flask-app-that-suggests-novel-novels-with-a-python-graph-9491e714bbdf) describes a recommendation application based on GoodReads data using a Python graph. The summary is:
* Build a Graph database of Users and the Books they read
* Develop a Flask App that serves up rare, interesting Books to Users based on their submitted favorites
* Implement a React App that integrates with Flask + our Graph to showcase to users their next favorite book

The code repository is at [https://github.com/franckjay/GoodReadsGraph](https://github.com/franckjay/GoodReadsGraph)


How to run\
<u>Terminal 1</u>\
The following steps are required only once after you have checked out the code.\
`$ npx create-react-app gwr`

Copy all the files from the `ReactApp` folder and paste them in `gwr` folder

<u>Terminal 2</u>\
`$ export FLASK_APP=api`\
`$ flask run`

Let the flask app complete building the graph and be ready to serve web requests. That is, wait until you see the following line at the prompt:\
\* Running on htpp://127.0.0.1:5000/ (Press CTRL+C to quit)

Then, go to Terminal 1

<u>Terminal 1</u>\
`$ cd gwr`\
`$ npm start`

Errors:
1. ./src/index.js\
Module not found: Can't resolve 'semantic-ui-css/semantic.min.css'\
Solution:\
`$ yarn add semantic-ui-css`

2. Error: [BABEL] /mnt/e/Code/Python/Flask Applications/GoodReadsGraph/gwr/src/index.js: Cannot find module '@babel/helper-builder-react-jsx'\
Solution:\
`$ yarn add @babel/helper-builder-react-jsx`

3. return jsonify({"image_url": ouput_URL}), 200\
NameError: name 'ouput_URL' is not defined\
Solution:\
api/app.py\
Line 58: change `ouput_URL` to `output_URL`\
Make the same change in lines 46 and 47.

For some reason, the book recommendation does not appear unless you refresh the page.\
That is, Enter 'Neuromancer' in the input text field and click Add.\
In the text field, you will see 'We found your favorite book!'.\
Then, refresh the webpage (F5 or Ctrl-R) and the recommended book will appear below the Add button.

The Python notebook having the whole application code also has errors.\
The path to the `ratings.csv` and `books.csv` had to be corrected by prepending with api/ as follows:\
`uir = pd.read_csv("data/goodbooks-10k-master/ratings.csv")`
`books = pd.read_csv("data/goodbooks-10k-master/books.csv")`
    
I have forked the repository and made the changes, you can check out and run the application without errors. It's available at:\
[https://github.com/mh-github/GoodReadsGraph](https://github.com/mh-github/GoodReadsGraph)

