# Pondr: an online publishing platform.
Pondr is an exemplar microservice system that accompanies the paper: *Communication, Security and Virtualisation with the Microservice Architecture*.

### Repositories
Pondr is made up of multiple components, and therefore separate repositories have been created.
- [Single Page Application (SPA)](https://github.com/Joshgallagher/fyp-client)
- [Infrastructure](https://github.com/Joshgallagher/fyp-infrastructure)
- [API Gateway](https://github.com/Joshgallagher/fyp-api-gateway)
- [Login and Consent Provider](https://github.com/Joshgallagher/fyp-login-provider)
- [Article microservice](https://github.com/Joshgallagher/fyp-article-service)
- [Comment Microservice](https://github.com/Joshgallagher/fyp-comment-service)
- [Rating Microservice](https://github.com/Joshgallagher/fyp-rating-service)
- [User Microservice](https://github.com/Joshgallagher/fyp-user-service-v3)
- [Bookmark Microservice](https://github.com/Joshgallagher/fyp-bookmark-service)
- [Rating Microservice Worker](https://github.com/Joshgallagher/fyp-rating-service-worker)
- [Comment Microservice Worker](https://github.com/Joshgallagher/fyp-comment-service-worker)
- [Bookmark Microservice Worker](https://github.com/Joshgallagher/fyp-bookmark-service-worker)

### Setup Instructions
Pondr is very easy to run. All you need is **Docker (Engine)** installed, and the repositories (above) cloned.

**[How to install docker.](https://docs.docker.com/engine/install/)**

##### Step 1
Create a folder named `fyp` (it must be called this). For example:

```bash
.
├──fyp
    ├── fyp-api-gateway
    ├── fyp-article-service
    ├── fyp-bookmark-service
    ├── fyp-bookmark-service-worker
    ├── fyp-client
    ├── fyp-comment-service
    ├── fyp-comment-service-worker
    ├── fyp-infrastructure
    ├── fyp-login-provider
    ├── fyp-rating-service
    ├── fyp-rating-service-worker
    └── fyp-user-service-v3
```

##### Step 2
In the repositories that contain a `.sample.env` file, run the following command in their folder: `cp .sample.env .env`.

##### Step 3
***NOTE:** This step can take approximately 10 minutes to complete. So leave it running and make yourself a cup of tea (or anything of your choosing)!*

Once you have set up the `.env` files in the repositories that need them, `cd` into the `fyp` folder and run the following command:

```bash
docker-compose -f docker-compose.yml -f docker-compose.api-gateway.yml -f docker-compose.article-service-db.yml -f docker-compose.article-service.yml -f docker-compose.bookmark-service-db.yml -f docker-compose.bookmark-service.yml -f docker-compose.hydra-db.yml -f docker-compose.hydra.yml -f docker-compose.login-provider.yml -f docker-compose.oathkeeper-api.yml -f docker-compose.oathkeeper-proxy.yml -f docker-compose.user-service-db.yml -f docker-compose.user-service.yml -f docker-compose.rating-service.yml -f docker-compose.rating-service-db.yml -f docker-compose.comment-service-db.yml -f docker-compose.comment-service.yml -f docker-compose.rabbitmq.yml -f docker-compose.bookmark-service-worker.yml -f docker-compose.comment-service-worker.yml -f docker-compose.rating-service-worker.yml up
```

##### Step 4
Now, you should be able to access RabbitMQs dashboard, and view the events taking place in response to your actions: `localhost:15672`.

##### Step 5
Once Pondr is up and running, you can start the SPA. `cd` into the `fyp-client` folder, and run `npm run serve` to start the application. Then, navigate to `localhost:8080` to view the SPA.

You should be able to start performing actions! It's a bit empty, so create a user and try writing an article! Maybe delete that article and view the RabbitMQ dashboard to see the data propagation in action.

##### Step 6
You have now started Pondr and performed some actions on the SPA (hopefully). You can now shut it all down!

Once you have finished running the project, press `ctrl+c` in the terminal you are running Pondr in, and then run the following command:

```bash
docker-compose -f docker-compose.yml -f docker-compose.api-gateway.yml -f docker-compose.article-service-db.yml -f docker-compose.article-service.yml -f docker-compose.bookmark-service-db.yml -f docker-compose.bookmark-service.yml -f docker-compose.hydra-db.yml -f docker-compose.hydra.yml -f docker-compose.login-provider.yml -f docker-compose.oathkeeper-api.yml -f docker-compose.oathkeeper-proxy.yml -f docker-compose.user-service-db.yml -f docker-compose.user-service.yml -f docker-compose.rating-service.yml -f docker-compose.rating-service-db.yml -f docker-compose.comment-service-db.yml -f docker-compose.comment-service.yml -f docker-compose.rabbitmq.yml -f docker-compose.bookmark-service-worker.yml -f docker-compose.comment-service-worker.yml -f docker-compose.rating-service-worker.yml down
```

The SPA can be simply stopped by pressing `ctrl+c` in the terminal you are running it in.

Hope you enjoyed Pondr!
