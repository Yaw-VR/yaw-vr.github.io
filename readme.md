# This repository is no longer maintained, instead use https://github.com/ItsVRK/yawvr

## How to contribute

This project uses:

1. git flow branching methodology https://www.youtube.com/watch?v=Aa8RpP0sf-Y
2. Material for mkdocs https://squidfunk.github.io/mkdocs-material/

## How to make changes (so you can test your changes before submission)

Developing locally allows you to fully test changes before submitting a pull request on github.

### Prerequisites (via terminal):

1. git `git --version`<br>Install: https://git-scm.com/downloads<br>Configure: https://git-scm.com/book/en/v2/Getting-Started-First-Time-Git-Setup
2. Python 3.7+ `python --version`<br>Install: https://realpython.com/installing-python/
3. pip `pip --version`<br>Install: https://pip.pypa.io/en/stable/installation/
4. pyenv `pyenv --version`<br>Install: https://github.com/pyenv/pyenv?tab=readme-ov-file#installation
5. pipenv `pipenv --version`<br>To install: https://pipenv.pypa.io/en/latest/installation.html

### Begin development:

1. Open terminal
2. cd to where you want to download the project
3. Fork the repository, clone your fork locally.
4. cd into cloned directory `cd yawvr-documentation`
5. Enable the pipenv shell `pipenv shell`
6. Install project requirements `pipenv install`
7. Run the mkdocs server by executing the following in your terminal `mkdocs serve`
8. Open an issue in the parent project and take note of the issue number
9. Create a feature branch locally to implement the change <br>`git checkout -b feature/[issue number]-[short description]`<br>Example: `git checkout -b feature/3-add-new-section-to-readme`
10. Make required changes and view them in browser locally until you are happy with changes
11. Commit the changes to your feature branch and push to your fork
12. Submit a pull request.

### Adding a dependency: You shouldn't really need to do this

make sure you have already run step 5 of Begin development section above

1. Open terminal in the project directory
2. Add the new requirement `pipenv install [package name]`
