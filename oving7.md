# Lesson 7

In this lesson we will look at how we can use Heroku to achieve our gaols of immutable artifacts,
environment parity and consistent builds.

You can use this repository as a starting point.

# Setup your environment

Set the two required environment variables in your shell

* GITHUB_TOKEN (Personal access token)
* HEROKU_API_KEY  

The Heroku key can be found in your user profile @ Heroku. The GITHUB token is a [personal access
token](https://help.github.com/articles/creating-a-personal-access-token-for-the-command-line/)

NB! Please note that you need to unset the Heroku API Key environment if you want to login with ```heroku login```

## Use Terraform to create the pipeline

Clone  the repositories, make your own - and copy the contents - as usual

- https://github.com/PGR301-2018/heroku-pipeline-infra
- https://github.com/PGR301-2018/heroku-pipeline-app

Then in the infra

- modify the two provider files
- modify the variables.tf file to make it your own.

run Terraform apply. You should now have a pipeline in your heroku account with 3 apps

## Conenct the "ci" app to yor application reopository

You need to add the Heroku application as a github "remote" for your application. To do this

- Login with heroku on the command line ```heroku login```
- Navigate to the directory of the application
- Run the command
```
heroku git:remote -a <application-name>
```
Where application-name is the 'dev' or 'ci' version, ie: gb-pipeline-app-cifomr the demo

## Chekc for environment parity

You should be able to start the app by running

```heroku local```

in the application repository

you can now push your application to thre "CI" stage of the pipeline with ```git push heroku master```

# BONUS / EXRTA

Take a loook at the concourse directory in the infra repo. You should be able to get a CI build of your app running in Concourse from there.
