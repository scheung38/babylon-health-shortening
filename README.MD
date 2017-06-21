# Build a url shortener

Your primary task is to build a url shortener api using python.

## Requirements

- Your webservice should have a `POST /shorten_url` endpoint that receives a json body with the url to shorten. A successful request will return a json body with the shortened url. 
- If a get request is made to the shortened url then the user should be redirected to the the original url, or returned the contents of the original url.
- Perform appropriate validation on the url to be shortened, and return appropriate error responses if the url is not valid
- Contain a `README.md` file with instructions on how to run your service.

## Note:
This task is simple and straight forward but we will be assessing you on your implementation of web service / python / software engineering best practices. 
So please use this as an opportunity to demonstrate how your write code and solve problems. You should also build your webservice in a way that a devops enginer (or you) could configure your backend in a way that your webservice could handle high traffic (eg. 1000 rps). 
Please explain in your `README.md` file how to configure your backend for scale.

## Example usage:

1)

`www.helloworld.com` -> <html><body> hello world </body> </html>

2)
```
Request:
    POST www.your_service.com/shorten_url

    body:
    {
        "url": "www.helloworld.com"
    }

Response: 
    Status code: 201
    response_body:
    {
        "shortened_url": 'http://www.your_service.com/ouoYFY48'
    }
```
3)

`http://www.your_service.com/ouoYFY48` -> <html><body> hello world </body> </html>

- To generate initial database

    $ sqlite3 urls.db

    $ pip install -r requirements.txt

    $ python main.py

For scaling, this is going to be deployed to AWS ECR via Docker and Kubernetes.
 
- Build the docker Image

Run the following command to build the docker image babylon-health-shortening from web directory

    $ docker build -t babylon-health-shortening:latest .

- Run the Docker Container

    $ docker run -d -p 5000:5000 babylon-health-shortening

You can find the container runtime details as shown below
    $ docker ps -a


CONTAINER ID        IMAGE                                   COMMAND                  CREATED             STATUS                      PORTS                                                                                         NAMES
21f772cd8149        babylon-health-shortening               "python app.py"          11 seconds ago      Exited (2) 10 seconds ago       