# Rails

Rails is a web development framework optimized for programmer happiness. Rails
extends Ruby's English like syntax and uses conventions over explicit
configuration,

## Rails CLI

Find the guide to the Rails command line [here](http://guides.rubyonrails.org/command_line.html)

### Miscellaneous Commands

```
# Get a console
rails console
rails c

# Get a console in the test environment
rails console -e test
rails c -e test


# Serve the app in the test environment
rails server -e test
rails s -e test

# Open the database's console
rails dbconsole
rails db

# Open the database's console in the test environment
rails dbconsole -e test
rails db - test

```

### Create a new project

```
rails new APP_PATH [options]

# Create a app:
rails new app

# Create a new project wihout turbolinks:
rails new app --skip-turbolinks

# Create a new app without turbolinks and with postgres:
rails new --skip-turbolinks --database=postgresql

# Create a new api:
rails new api --api

# Create a new api with postgres:
rails new api --api --database=postgresql

```

### Generate

```
# Generate something
rails generate [type] NAME [args]
rails g [type] NAME [args]
```

#### New controller

```
rails generate controller CONTROLLER_NAME [actions]

# generate a new dashboard
rails generate controller dashboard settings profile transactions
```

#### New resource

```
rails generate resource RESOURCE_NAME [attribute:type]

# generate a new user profile
rails generate resource profile name:string age:integer male:boolean

```

#### New model

```
rails generate model MODEL_NAME [attribute:type]

# generate a new user profile
rails generate resource profile name:string age:integer male:boolean
```