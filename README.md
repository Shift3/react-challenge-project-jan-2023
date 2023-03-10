# Shift3 React Challenge Project
This project represents a challenge to test your git flow, programming, and troubleshooting fundamentals. Below you will find instructions on how to complete the challenge, as well as additional information on how to stand up and navigate this project.

## Challenge Instructions
You will begin by creating a fork of this repository to your own Github account. All work will be completed and reviewed within your own fork. Please do not create a Pull Request (PR) back into this repository.

Once you have created your fork, review the Issues labeled `challenge task` [HERE](https://github.com/Shift3/react-challenge-project-jan-2023/issues?q=is%3Aissue+is%3Aopen+label%3A%22challenge+task%22). Shift3's standard for branching is as follows:

- Maintain a `main` and development (`dev`) branch on your fork
- For each feature/task (Issue), create a new branch based off of your `dev` branch
- Once a task has been completed, create a Pull Request from the working branch to your `main` branch and reference the Issue you are working on. **These open PRs will be the final submission which Shift3 will review.**

Once you are ready to submit your work, send an email to your Shift3 contact with a link to your fork.

**Please apply the following Shift3 Standard Practices as you work on this project:**
- Each unit of work (Issue) should be completed within its own [branch](https://github.com/Shift3/standards-and-practices/blob/main/standards/branching.md).
- Use Karma-style formatting for your [Git Commit Messages](https://github.com/Shift3/standards-and-practices/blob/main/standards/commits.md).
- Generate a PR for each unit of work (Issue) which is completed. Keep the scope of these PRs as narrow as possible. Try not to create PRs which rely on or contain code from previous PRs unless there is truly a dependency between the two units of work.

## Project Information

This is a multi-container docker environment that utilizes Docker to create three seperate but linked containers:

- MongoDB database
- Node/Express Server
- React client

## Project Requirements

- Docker
    - For Mac Users: [Docker Desktop for Mac](https://docs.docker.com/docker-for-mac/install/)
    - For Windows 10 Home/Pro/Enterprise Users: [Docker Desktop for Windows](https://docs.docker.com/docker-for-windows/install/)
    - For Windows 7 Users: [Docker Toolbox](https://docs.docker.com/toolbox/toolbox_install_windows/)
    - For Linux Users (follow link and choose your Distro): [Docker Engine](https://docs.docker.com/engine/install/)
- Do not have anything running on the required ports (3000 for client, 4000 for server, 27017 for mongo.)

## Running the project

- After cloning the repo, go into the project's root directory. Run `docker compose up`. This will start up the database image and the server/
 - The first time running this the server will go through the build process, but this should only happen once.
- With the server running, open up a new terminal window and navigate to the `application` directory.
    - If this is your first time running the app, run `npm install`.
    - Run `npm start`.
- Your connection target on Mac and Linux is `localhost://`. 
- Database can be found at `(target):27017`, server at `(target):4000`, client at `(target):3000`.

## Development process

Shutting down the servers can be done with a Ctrl-C command from your terminal. Alternatively, you can load up Docker Desktop to close them as well. Ctrl-C also works for shutting down the client.

If you need to exec into one of the containers, Docker Desktop has a GUI to do that for you. Otherwise, you will need to run `docker ps`, find the container ID, and then run `docker exec (container_name) -it bash`.

Docker Desktop can also be useful for looking at the logs for one specific container, since all three are tailed in the terminal.

## Endpoint testing

The following backend endpoints can be queried via Postman for testing purposes:

- Login (POST) - `(server addr)/api/login` (Expects name/password in request body)
- Current Orders (GET) - `(server addr)/api/current-orders`
- Add Order (POST) - `(server addr)/api/add-order` (Expects ordered_by, quantity, menu_item in request body)
- Delete Order (POST) - `(server addr)/api/delete-order` (Expects id in request body)
- Edit Order (POST) - `(server addr)/api/edit-order` (Expects id in request body. Will look for ordered_by, quantity, menu_item.)
- Flush Orders (DELETE) - `(server addr)/api/delete-all` (This deletes all current orders in the DB)
- Live Mode (POST) - `(server addr)/api/live-mode` Starts a simulated "live order mode" where random orders will either be added or deleted at an interval declared in `time` in the request body (in seconds). Orders will be added/deleted a total of 12 times.
