<h1>Cloudsite</h1>
microsoft azure project


<h2>Project Title:</h2>

<h3>Dockerization and Deployment of a Static Website on Azure Container Instances</h3>

<h2>Problem Statement/Opportunity:</h2>
Identify the specific problem or opportunity that this project aims to address. This could include issues related to scalability, portability, or efficiency in deploying and managing a static website.]

<h2>Project Description:</h2>
<h3>Objective:</h3>
The primary objective of this project is to demonstrate the process of creating a Docker image from an Azure Virtual Machine (VM) containing a static website, pushing the Docker image to Azure Container Registry (ACR), and deploying a container instance using the image stored in ACR.

<h3>Prerequisites:</h3>
 <h4>1. Azure subscription with access to Azure Portal.</h4>
 Container registries are repositories for storing and distributing container images. In the context of software development and deployment, a container is a lightweight, standalone, and executable software package that includes everything needed to run a piece of software, including the code, runtime, libraries, and system tools. Containers are often used for packaging and deploying applications in a consistent and reproducible way across different environments.

A container registry is a centralized storage system that allows you to upload, download, and manage container images. These images are typically used with container orchestration platforms like Kubernetes or container runtime environments like Docker. The registry serves as a hub for sharing and distributing container images among developers, teams, and systems.

<h5>Key features of container registries include:</h5>

<h5>Image Storage:</h5> 
Container registries store container images, which are essentially snapshots of a file system with metadata describing the image and its dependencies.

<h5>Distribution:</h5> 
Container registries provide a way to distribute container images to different environments or systems. This is crucial in a distributed and scalable architecture.

<h5>Versioning:</h5> 
Container registries support versioning of images, allowing developers to use specific versions of an application or service.

</h5>Access Control:</h5> 
Registries often have access control mechanisms to restrict who can push or pull images. This helps in managing permissions and securing the distribution process.

<h5>Integration with Orchestration Platforms:<h5> 
Container registries are often integrated with container orchestration platforms like Kubernetes, making it easy to deploy and manage containerized applications at scale.

<h5>Popular container registries include:</h5>

<h5>Docker Hub:</h5> 
A public registry hosted by Docker that allows users to share and access container images.

<h5>Google Container Registry (GCR):</h5> 
A private container registry service provided by Google Cloud Platform.

<h5>Amazon Elastic Container Registry (ECR):</h5> 
A private container registry service provided by Amazon Web Services.

</h5>Azure Container Registry (ACR):</h5>
A private container registry service provided by Microsoft Azure.

<h4>2. Azure Virtual Machine with a static website deployed.</h4>
<h4>3. Docker installed on the Azure Virtual Machine.</h4>

<h4>Step 1: Create a Dockerfile</h4>
Create a Dockerfile in the root directory of your static website on the Azure Virtual Machine. The Dockerfile specifies the steps to build the Docker image.

Example Dockerfile:

Use an official Nginx image as the base image
FROM nginx:latest

Copy the static website files to the Nginx default directory
COPY /path/to/your/static/website /usr/share/nginx/html

Expose port 80 for web traffic
EXPOSE 80

Command to run when the container starts
CMD ["nginx", "-g", "daemon off;"]


Step 2: Build the Docker Image
Open a terminal on the Azure Virtual Machine and navigate to the directory containing the Dockerfile. Run the following command to build the Docker image:

docker build -t your-image-name:tag .
Replace your-image-name with a meaningful name for your image, and tag with a version or label for the image.

Step 3: Azure Container Registry Setup
Navigate to the Azure Portal.
Create a new Azure Container Registry.
Note the ACR login server URL, username, and password.

Step 4: Login to Azure Container Registry
Run the following command on the Azure Virtual Machine to log in to the ACR using the credentials obtained in Step 3:

docker login <acr-login-server> -u <username> -p <password>
Replace <acr-login-server>, <username>, and <password> with your ACR details.

Step 5: Tag and Push the Docker Image
Tag the Docker image with the ACR login server and push it to the ACR:

docker tag your-image-name:tag <acr-login-server>/your-image-name:tag
docker push <acr-login-server>/your-image-name:tag

Step 6: Deploy Container Instance from ACR
Navigate to the Azure Portal.
Create a new Azure Container Instance.
Specify the ACR image URL (e.g., <acr-login-server>/your-image-name:tag).
Configure the necessary settings (e.g., resource group, networking, etc.).
Deploy the container instance.

<h2>Conclusion:</h2>
This documentation provides a detailed guide on Dockerizing a static website on an Azure Virtual Machine, pushing the image to Azure Container Registry, and deploying a container instance. Following these steps ensures a streamlined process for containerization and deployment on the Azure platform.
