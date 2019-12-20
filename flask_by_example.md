<u>20-Dec-2019</u>

The [Flask by Example](https://realpython.com/flask-by-example-part-1-project-setup/) is a full-stack tutorial that is very useful to beginners. It integrates Redis and machine learning tasks to provide a comprehensive learning exercise.

This is an old-<i>ish</i> article; I've seen comments that are marked as posted six years ago. So I guess it was written in 2013. It was updated in 2015 and 2016 to Python3.

I worked out the whole application, which is explained in seven parts, on my laptop and am sharing my experience here.

My environment is:
* Windows 10
* Cmder
* Python

I use Chocolatey package manager to install the software I need. Once you have Choco, you need to check on their website if a particular software is available with them and if yes, use the command choco install <your software>. I've installed git, Cmder and Atom with the following commands.

```
choco install -y git
choco install -y Cmder
choco install -y Atom
choco install -y heroku-cli
```
The cool thing about the Cmder prompt is that you can issue both Windows as well as Linux commands. Here is the commands & action sequence that I had to do to get Part-1 of the tutorial working:

Create a working directory and initialize git
```
mkdir flask-by-example && cd flask-by-example
git init
```

Setup virtual environment
```
python -m venv env
env\Scripts\activate.Bartender
```

Create files
    touch app.py .gitignore README.md requirements.txt

Update the contents of the file .gitignore in notepad
`notepad .gitignore`
Copy the contents of [repo](https://raw.githubusercontent.com/realpython/flask-by-example/master/.gitignore) into notepad, save and close.

Install Flask. I did not give any version number
`pip install Flask`

Add installed libraries to requirements.txt
`pip freeze > requirements.txt`




My Python version was 3.7.3. The list of supported Python runtimes, https://devcenter.heroku.com/articles/python-support#supported-runtimes has Python 3.7.5. Therefore, I had to upgrade my Python version. I did that with

`conda update anaconde`
at the Anaconda prompt.
