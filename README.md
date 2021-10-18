# Tutorial: Deploying a basic Blitz app on Jekyo

Demo app [here](https://blitz-demo.jekyo.app/)

### Prerequisites

Make sure you have [NodeJS](https://nodejs.org/en/download/), [npm](https://docs.npmjs.com/downloading-and-installing-node-js-and-npm) and [git](https://github.com/git-guides/install-git) installed.

If it's your first time using **Jekyo**, you can **install** it by running the following command in your terminal:

`npm install -g jekyo`

### Sign in to Jekyo

You can sign in to Jekyo by running `jekyo user:signin`

```
➜  ~ jekyo user:signin
Your email?: **************
Your password?: **********
You have successfully signed in!
```

If you don't have a Jekyo account, you can create one in the terminal by running `jekyo user:signup`.

## 1. Create a basic Blitz app

You can start your Blitz project by using `jekyo create`

Using the **arrows** on your keyboard, select **blitz** and press **enter**.

```
? Select template
  None Creates only the application
  expressjs A basic app skeleton using [Express](https://expressjs.com/)
  nuxt-js A boilerplate SSR application using [Nuxt.js](https://nuxtjs.org/)
❯ blitz A basic starter app using [Blitz](https://blitzjs.com/)
```

When prompted, enter the desired name for your Blitz app.

`Application name?: blitz-tutorial`

This will create a basic Blitz app in the current directory by cloning this [Blitz starter app](https://github.com/jekyo/blitz-getting-started) repository.

```
Cloning source code... OK
Application created!
```

### Deploy the Blitz app on Jekyo

To deploy the app, first navigate to the newly created directory:

`cd blitz-tutorial`

Now you can deploy this app to Jekyo by running:

`jekyo deploy`

After a while, you should see something like this:

```
➜  Fetching source code ... OK
➜  Building application, this might take a while ... OK
➜  Publishing application, this might take a while  ... OK
➜  Deploying application ... OK
➜  Waiting for application to start ... OK
➜  Visit your app on: https://blitz-tutorial.jekyo.app ... OK
```

You can now browse to your Blitz app on https://blitz-tutorial.jekyo.app (replace 'blitz-tutorial' with your app name)

## 2. Deploying an existing Blitz app

Navigate to your local Blitz app directory

`cd my-blitz-app`

Initialize a git repository if you haven't already done so by running `git init`.

### Edit package.json

In your `"scripts"` section of your **package.json**, your `"start"` line should include Jekyo's `$PORT` and `$HOST` variables:

```
"start": "blitz start --port=$PORT --hostname=$HOST",
```

### Edit .env

In the root directory of your app, your **.env** file (not .env.local) should include the db URL and a session secret key that's at least 32 characters long:

```
DATABASE_URL="file:./db.sqlite"
SESSION_SECRET_KEY="this-is-a-33-char-long-secret-key"
```

### Create an empty Jekyo app:

`jekyo create`

Select 'none' using the **arrows** on your keyboard and press **enter**. This will create an app using your current directory.

```
? Select template (Use arrow keys)
❯ None Creates an application from your current directory
```

Name your app:

`Application name?: my-blitz-app`

Run `jekyo link` to link your local app to the remote Jekyo app. Select 'my-blitz-app' using the **arrows** on your keyboard and press **enter**.

```
? Select application (Use arrow keys)
❯ my-blitz-app
```

### Now you can deploy this app to Jekyo by running:

`jekyo deploy`

After a while, you should see something like this:

```
➜  Fetching source code ... OK
➜  Building application, this might take a while ... OK
➜  Publishing application, this might take a while  ... OK
➜  Deploying application ... OK
➜  Waiting for application to start ... OK
➜  Visit your app on: https://my-blitz-app.jekyo.app ... OK
```

You can now browse to your Blitz app on https://my-blitz-app.jekyo.app (replace 'my-blitz-app' with your app name)

## Pushing local changes to Jekyo

Add the newly modified file(s) to the git index by using [git add](https://www.atlassian.com/git/tutorials/saving-changes)

`git add filename`

Create a [git commit](https://github.com/git-guides/git-commit)

`git commit -m "your commit message"`

Now, simply deploy your app again:

`jekyo deploy`

You will see your changes on your live app after a short while.
