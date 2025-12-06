# talkshop-final
# TalkShop USF Admin Portal

    Hey there, welcome to the Talkshop codebase. Talkshop is a peer to peer platform that allows potential college students and employees to connect with alumni and past employees of the schools and companies they’re looking at.

## Structure

    The structure of the repo is as follows: the top level has all of the environment dependencies (packages, env data, config files, etc.) and a few folders. If you’re looking to run the app locally then all of the necessary commands are listed in the package.json file. The folders that start with a . shouldn’t need to be opened as they are just for building the app and other executive functions that a user of the app doesn’t need. The most important directory is the src folder. It contains all of the driver code for the app and is where library functions, react components, and server actions all live.

## Information about TalkShop

    The app is built with NextJS and React to control all behavior, so the components directory within src is critical to the project as a whole. ALL React components live inside of it and are imported and used in web pages that are defined in the app directory.

    The app directory holds all of the routes for the site, as handled by NextJS. In the Next framework, file paths correspond to url paths so all urls for the site have matching folders here in the repo. The folders in parenthesis are route groups and are there to define the most fundamental features of the site (app, auth, and video-call). Most of our work was done in the (app) directory, as it contains most of the pages for the front facing site, including the admin portal which is where the bulk of our work was done. This folder contains a directory for each url path on the site and those all have their own sub-directories for dynamic pathing and such. The visible page at any given url is defined by “page.tsx” in its corresponding folder and because of this there are MANY instances of page.tsx hidden in the repo.

## Testing

    To run the app a couple of things are necessary. You’ll need all the packages before you begin so a simple “npm install” should pull all the dependencies and update/install them as necessary. With all the packages in place, the whole environment has behavior defined by the Talkshop Docker container. Details are in the docker-compose.yml at the top level of the repo. To start it make sure Docker is running on the host machine and simply run “docker compose up” in the shell.  Along with Docker, the database must be set up. We use a PostgresSQL database, so the docker container is attached to it (wherever it may be) and it’s good to go. Without any data though, nothing will be accomplished past admiring the login screen so we must first set up and seed it. This can be done with “npm run db:reset” in the shell which subsequently runs the drop, create, and seed commands to ensure there is usable data in the database. Once this is all set up and running, we can open another terminal window and run “npm run dev” which activates the app and lets us connect to it locally (port determined by whatever else you have running, but it defaults to localhost:3000). Once running we can open a browser and see the site.

    You can log in with any of the usernames and passwords defined in the database seeding file “src/db/” but be aware that the different users all have different permissions, so the admin user is your best bet (admin@talkshop.io password - “password”). This will take you to the site and you’ll have all functionality available. Don’t worry about safety as this is only running locally so nothing you do here will be reflected in the production site and its corresponding database. The different participant types (user, mentor, admin) will all see different pages, as they’re dynamically displayed depending on permissions.

    Testing was all done manually, as our sponsor has plans to implement their own testing architecture and explicitly stated “remove testing architecture from pull request” when we added our own test cases.
