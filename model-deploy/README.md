- This is a template for creating a docker container to set up and run a flask app to serve a Python model
- Armed with the flask app, an external application can make API calls to my model (e.g., provide values of features to my model, and get prediction). Please review Flask.
- This is a standard way for some companies to deploy their model
- In Hareem's company, they have insurance companies as clients. Her company will create and deploy models that predicts whether someone is a smoker based on their response on a few questions.
- The analyst in the insurance companies will collect features values/information about a patient over the phone. She will input these values to an app (with user interface), and the front-end app will pass this information to the model via api calls. The model will return a prediction (smoker/non-smoker) back to the frontend in real-time.
- Using docker will make the deployment of the model very stable (thus suitable for external consumption by other apps)
- NOTE: I can actually push this image to Dockerhub and make it a new base image that other people can build on.


### Steps to run container:
  - Go to the model-deploy directory, open terminal
  - We need to first build the image from the dockerfile:
    - docker build -t model .
    - note that 'model' is the name/tag that I give to the image, can be anything else, '.' is the path to the dockerfile (which is my currently directory)
  - Once the image is built, I can create a container from the image
  - docker run -p 1000:80 model
  - I map port 1000 on my local machine to port 80 in my container.
  - Now, go to my local host: 1000
  - http://localhost:1000/isAlive
    - I should see "true"
  - http://localhost:1000/prediction?f=0.06
    - [ 209.09959979]
  
  - The way we are running the model right now is mostly to do testing (still treat this as a "dev paradigm", I am just testing my deployment using the container that has pretty much the same characterisitics as my prod environment)
  - I will deploy the model after testing it to AWS for example. The docker container will be a "template" for a EC2 that I will set up. I will run the flask app within the EC2 (which will be up continuously) to serve my model predictions. The logs of the flask app etc... will be written/stored in S3.
    
