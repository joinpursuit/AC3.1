## Heroku
Heroku is a hosting service that runs your application and exposes it to the internet. When hosting through Heroku, you'll receive a free domain name that'll correspond to the name of your application. However, it'll take some time for the application to load up because it's free(we'll discuss ways to avoid this later).

- [Getting Started on Heroku with Node.js](https://devcenter.heroku.com/articles/getting-started-with-nodejs#introduction)
- [Sequelize Docs for Heroku](http://docs.sequelizejs.com/en/1.7.0/articles/heroku/)

### Setup
- Sign up for a [Heroku account](https://www.heroku.com/home)
- Install the [Heroku CLI](https://devcenter.heroku.com/articles/heroku-cli#download-and-install), formerly known as the Heroku Toolbelt
- Log into your account in the terminal by running `heroku login` and providing your credentials
- Create an application on the Heroku website. Alternatively, you can run `heroku create` in the terminal. This creates a random application name that you'll have to replace later anyways.

### `package.json`
Add the right versions of `node` and `npm` under `engines`.
```js
{
  "name": "application-name",
  "version": "0.0.1",
  "private": true,
  "scripts": {
    "start": "node app.js"
  },
  "dependencies": {
    "express": "3.1.1",
    "jade": "*"
  },
  "engines": {
    "node": "0.8.x",
    "npm": "1.1.x"
  }
}
```
You can also add a `"heroku-postbuild"` field which will get run after `npm install`. Here you can add things like `webpack` or run `seed` files - basically anything you'd want to run before `npm start`.


### config.json
Most of your projects used the Sequelize CLI to generate an `index.js` within the models folder. This will automatically detect the environment changes. However, you will need to edit the `production` category and set the database field to `DATABASE_URL`.

### Sequelize connection
```js
if (process.env.NODE_ENV === 'production') {
  var sequelize = new Sequelize(process.env.DATABASE_URL);
}
```

### server.js
Your Express app within your `server.js` can no longer listen in on a localhost port. You'll need to reconfigure it to listen in on `process.env.PORT`

### Spawn a PostgreSQL database
Run `heroku addons:add heroku-postgresql:hobby-dev` in your terminal.

### Deployment
- To link your project to Heroku, you'll need to retrieve the git link from the settings of your Heroku project and add a heroku remote.
- To deploy new code, run `git push heroku master`.
- Heroku usually takes a while to take effect(30 minutes). Eventually, you'll be able to navigate to the URL specificed again in the settings of your Heroku application and see your application up and running.

### Heroku Logs
Run `heroku logs` inside of your project folder to see if anything is going wrong with your application.




## Cloudinary Image Upload
Heroku and most hosting services will not allow you to save files. We have to find another solution. Amazon Web Services is confusing and difficult to use. Luckily, there's Cloudinary!

### Steps
- Sign up for a Cloudinary account.
- When you have an account, go to the settings to configure an upload preset. You'll have to click on the upload tab.
- You'll need your account name and the upload preset to save images.

### Resources
[Scotch.io](https://scotch.io/tutorials/%E2%80%8Bleveraging-react-for-easy-image-management-with-cloudinary)
