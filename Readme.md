
# Angular Dev environment created with docker-compose



## Dev environment:

This environment contains an online vscode version, and a mongo container

  

To start dev environment:

Go to Compose/Dev and run:

```bash

docker-compose  up

```

Once the containers are up, go to http://localhost:8080/

If a password is required, use the password in ~/.config/code-server/config.yaml

```bash

cat  ~/.config/code-server/config.yaml

```

  

--- Start debug environment :

Inside the vscode editor, to setup the node-express server, open the terminal and run:

```bash

cd  project/angular-15-node-js-mongodb-example/node-express-server

node  server.js

```

  

Now to start the angular app, open another terminal and run:

```bash

cd  project/angular-15-node-js-mongodb-example/angular-15-client

ng  serve

```

  

Then if you go back to the other terminal, you can launch the angular app by ctrl + left click on the link:

```http://localhost:4200/```

It will redirect you to the angular app at http://localhost:8080/proxy/4200/tutorials

  

In the app, you can test if the connection to the node-express server is working by going in the "Add" tab and adding a tutorial.

You can then go back to Tutorials and see the tutorial you just added.

  

## Prod environment:

nginx server, Node express server, mongo

  

Some modifications are needed to make it work:

In the Project/angular-15-node-js-mongodb-example/angular-15-client/src/app/services/tutorial.service.ts file, change the url from 
```javascript
const baseUrl = 'http://localhost:8080/proxy/8081/api/tutorials'; 
``` 
to:

```javascript

const baseUrl = 'http://localhost:8081/api/tutorials';

```

Remove --serve-path=/proxy/4200/ from the ng serve configuration in the package.json file:

```json

"start": "ng serve"

```

Then refresh the docker image:

go to Project/angular-15-node-js-mongodb-example/angular-15-client and run:

```bash

docker  build  .  --tag  'angularprod'

```

  

Now to start the prod environment:

Go to ./Compose/Prod and run:

```bash

docker-compose  up

```

  

Once the containers are up, go to http://localhost/
You can test the connection to the database by adding a tutorial in the Add tab
