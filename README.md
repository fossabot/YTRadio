# YTRadio
[![FOSSA Status](https://app.fossa.io/api/projects/git%2Bgithub.com%2Fswimmadude66%2FYTRadio.svg?type=shield)](https://app.fossa.io/projects/git%2Bgithub.com%2Fswimmadude66%2FYTRadio?ref=badge_shield)

__codenamed LifeBoat__

Each instance of Lifeboat represents a venue in which you and your friends can DJ to an audience all over the world. What makes Lifeboat different from other DJ'ing platforms of the past is that it is light enough to be hosted as an afterthought on almost any server.


The built in chat allows for lifeboat to serve as a fun substitute for a message board or irc room. Host an instance on your company website and let your customers chat while sharing music. Run multiple instances in a docker containers to turn one server in to a de facto music room for several genres


# How to Host

# Method 1 - __Docker__
_requires docker_

1. `Docker pull swimmadude66/ytradio`
2. `Docker run [OPTIONS] swimmadude66/ytradio`

`[OPTIONS]` is a placeholder for any number of docker options you may want to pass in order to make the app fit within your ecosystem. it is recommended that at a bare minimum, 
you define the environment variables for connecting to your database (via `-e` or `--env-file`) and expose the port under which you will run the app (3000 is the default, so use `-p"3000:3000"`).

Additionally, you can mount a volume at /https by passing the `-v {cert_location}:/https` option.


## Development
A `docker-compose` file has been included, which spins up a mysql instance with __unsafe__ defaults. __DO NOT USE THE DOCKER COMPOSE FILE IN PRODUCTION__

Instead, it can be used as a handy way to isolate development. Check out the code, Make your changes in the editor of your choice, then run `docker-compose up --build -d`

The app will be accessible at `localhost:3001` with your changes included. The app features live reload, so changes you make on your local filesystem will be instantly reflected in the app. NOTE: changes to server will trigger a server restart, so the app will disconnect momentarily, and your song will be interrupted.


Lastly, to access the mysql database being used for the containers, either exec in to that container (`docker exec -it ytradio-db mysql -u root -padmin`) or connect the database manager (eg MySQL Workbench, Datagrip) to `localhost:6033` and log in with the __unsafe__ default login.


# Method 2 - __Build from Source__
_requires git, node, and npm_

1. Clone this repo on to your host box (or just download the zip from github, I'm not your mom)
2. `cd` in to the cloned/downloaded repo
3. run `npm i`, then `npm run gulp`
4. `npm start` will host the app on the default port!

## Development
After cloning and installing, you can run `npm run dev` to create a live-reloading instance of the app. (note, you will need to run `npm start` or `npm start-dev` in a separate terminal to launch the api)

Additionally, you can configure the app by workspace by creating and editing a `.env` fle in the project root.  The contents of the file will be read as KeyValuePairs and overwrite `process.env` variables.



## License
[![FOSSA Status](https://app.fossa.io/api/projects/git%2Bgithub.com%2Fswimmadude66%2FYTRadio.svg?type=large)](https://app.fossa.io/projects/git%2Bgithub.com%2Fswimmadude66%2FYTRadio?ref=badge_large)