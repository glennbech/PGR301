# Lesson 7

In this lesson we will look at how we can use Heroku to achieve our gaols of immutable artifacts,
environment parity and consistent builds.

You can use this repository as a starting point.

# Part A

Get to know heroku pipelines 

## Setup your environment

Set the two required environment variables in your shell

* GITHUB_TOKEN (Personal access token)
* HEROKU_API_KEY  

The Heroku key can be found in your user profile @ Heroku. The GITHUB token is a [personal access
token](https://help.github.com/articles/creating-a-personal-access-token-for-the-command-line/)


## Make repos

Create a repository for your application 

## Change and apply terraform files

Log into heroku 

```
heroku login
```

Copy [this repo](https://github.com/PGR301-2018/heroku-pipeline-app) and [this repo](https://github.com/PGR301-2018/heroku-pipeline-infra) and make them your own. 

In the infra repo. 
- modify the provider file
- modify the variables.tf file to suit your own needs.
- run terraforma apply 

This will create the required repositories and Heroku resources for you.



