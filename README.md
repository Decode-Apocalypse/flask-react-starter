# Flask and `create-react-app`

## Requirements
1. `npm install`
2. `pip install -r requirements.txt`

## Run Application
1. Run command in terminal (in your project directory): `npm run build`. This will update anything related to your `App.js` file (so `public/index.html`, any CSS you're pulling in, etc).
2. Run command in terminal (in your project directory): `python3 app.py`
3. Preview web page in browser 'localhost:8081/' (or whichever port you're using)

------------------- Database Set up --------------------------
# For Mac users

## install homebrew
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"

## install postgresql
`brew install postgresql`

## start homebrew postgresql service
`brew services start postgresql`

## test postgresql by running
`psql -h localhost`

## to exit psql prompt type
`\q`

## install psycopg2 -- we won't be using this directly, but it will let you interact with local DBs if you ever need
`pip install psycopg2-binary`

## install Flask-SQLAlchemy
`pip install Flask-SQLAlchemy==2.1`


# For VM/Ubuntu/WSL users

## update your package index
`sudo apt update`

## install postgresql
`sudo apt install postgresql`

## to run the psql prompt
`sudo -u postgres psql`

## install psycopg2 -- we won't be using this directly, but it will let you interact with local DBs if you ever need
`pip install psycopg2-binary`

## install Flask-SQLAlchemy
`pip install Flask-SQLAlchemy==2.1`


-------- HEROKU DATABASE SET UP -------------
# Heroku DB Setup
1. Now we're going to create a database remotely with Heroku and connect to it with our code. Login and fill creds: `heroku login -i`
2. Create a new Heroku app: `heroku create`
3. Create a new remote DB on your Heroku app: `heroku addons:create heroku-postgresql:hobby-dev` (If that doesn't work, add a `-a {your-app-name}` to the end of the command, no braces)
4. See the config vars set by Heroku for you: `heroku config`. Copy paste the value for DATABASE_URL
5. Set the value of `DATABASE_URL` as an environment variable by entering this in the terminal: `export DATABASE_URL='copy-paste-value-in-here'` (mine looked like this `export DATABASE_URL='postgres://lkmlrinuazynlb:b94acaa351c0ecdaa7d60ce75f7ccaf40c2af646281bd5b1a2787c2eb5114be4@ec2-54-164-238-108.compute-1.amazonaws.com:5432/d1ef9avoe3r77f'`)
6. IF THE URL STARTS WITH `postgres:`, replace that with `postgresql:`!! If you're unable to change config variables for some reason (certain combinations of Windows setups and Heroku being grumpy), there's a Python workaround: https://help.heroku.com/ZKNTJQSK/why-is-sqlalchemy-1-4-x-not-connecting-to-heroku-postgres

---------- ENVIROMENT -----------

1. touch .env 
2. export DATABASE_URL = "your-actual-url-from-heroku"