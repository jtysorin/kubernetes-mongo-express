# MongoDB and Mongo Express Kubernetes Demo Project

This is a demo Kubernetes project that sets up a MongoDB database and deploys the Mongo Express web interface to interact with the database.

## Project Structure

The project consists of the following Kubernetes YAML files:

1. `mongo-express-configmap.yaml`: This ConfigMap contains configuration settings for the Mongo Express application.

2. `mongo-express-deployment.yaml`: The deployment configuration for the Mongo Express web interface.

3. `mongo-express-service.yaml`: A Kubernetes service that exposes the Mongo Express application within the cluster. This service allows external access to the Mongo Express web interface.

4. `mongodb-deployment.yaml`: Deployment configuration for the MongoDB database.

5. `mongodb-secret.yaml`: A Secret containing sensitive information like database credentials.

6. `mongodb-service.yaml`: A Kubernetes service for accessing the MongoDB database. This service allows other components in the cluster to connect to the MongoDB database.

## Project Description

### MongoDB Deployment

The `mongodb-deployment.yaml` file sets up a MongoDB deployment within the Kubernetes cluster. It defines the desired replica count and specifies the MongoDB Docker image to use. The data is stored within persistent volumes.

### MongoDB Service

The `mongodb-service.yaml` file creates a Kubernetes service to expose the MongoDB deployment within the cluster. This service allows other components in the cluster, including the Mongo Express application, to access the MongoDB database. The service is accessible within the cluster using the DNS name `mongodb-service`.

### Mongo Express Deployment

The `mongo-express-deployment.yaml` file deploys the Mongo Express web interface. It connects to the MongoDB database using the MongoDB service DNS name (`mongodb-service`) and port (`27017`) specified in the `mongodb-service.yaml` file.

### Mongo Express Service

The `mongo-express-service.yaml` file creates a Kubernetes service for exposing the Mongo Express web application to external users. It uses a LoadBalancer type service to make the Mongo Express application accessible externally via a node port (`30000`) on the Kubernetes cluster nodes. Users can access the Mongo Express web interface via the cluster's external IP address and the node port `30000`.

### MongoDB Secret

The `mongodb-secret.yaml` file defines a Kubernetes secret that stores sensitive information, such as the MongoDB username and password.

## Usage

To deploy this project in your Kubernetes cluster, follow these steps:

1. Apply the MongoDB Secret:

`kubectl apply -f mongodb-secret.yaml`

2. Deploy the MongoDB database:

`kubectl apply -f mongodb-deployment.yaml`

3. Create the MongoDB service:

`kubectl apply -f mongodb-service.yaml`

4. Apply the Mongo Express ConfigMap:

`kubectl apply -f mongo-express-configmap.yaml`

5. Deploy the Mongo Express application:

`kubectl apply -f mongo-express-deployment.yaml`

6. Create the Mongo Express service:

`kubectl apply -f mongo-express-service.yaml`


After completing these steps, you should have MongoDB and Mongo Express up and running in your Kubernetes cluster. You can access the Mongo Express web interface externally using the cluster's external IP address and node port `30000`.

## Maintenance

Remember to periodically check for updates to MongoDB and Mongo Express Docker images and update your deployment configurations accordingly.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

