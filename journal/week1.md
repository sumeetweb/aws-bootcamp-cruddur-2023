# Week 1 — App Containerization

I went through cantrill.io's Docker Fundamentals course and setting up Docker in my system.

Created a Dockerfile in Backend Flask:

```
FROM python:3.10-slim-buster

WORKDIR /backend-flask

COPY requirements.txt requirements.txt
RUN pip3 install -r requirements.txt

COPY . .

ENV FLASK_ENV=development

EXPOSE ${PORT}
CMD [ "python3", "-m" , "flask", "run", "--host=0.0.0.0", "--port=4567"]
```

I launched the backend app in Gitpod and got the JSON successfully in "/api/activities/home" path.  

![image](https://user-images.githubusercontent.com/25149022/227739689-15f313a9-5328-4340-984e-e63b63a6b5e7.png)  
![image](https://user-images.githubusercontent.com/25149022/227739709-f964ba0c-affd-495f-a832-a20f499452bd.png)  

Then successfully built the image using 

```
docker build -t  backend-flask ./backend-flask
```

![image](https://user-images.githubusercontent.com/25149022/227740096-617e68fb-1fa1-4f60-943b-21774d400b36.png)

By deafult docker uses a default tag.
Add tags to docker images by following the format: name:tag
```
docker build -t  backend-flask:v1 ./backend-flask
```
This will set the tag as v1

To pass env vars into backend-flask app, we used -e parameter  
`docker run --rm -p 4567:4567 -it -e FRONTEND_URL='*' -e BACKEND_URL='*' backend-flask`

Run in background  
`docker container run --rm -p 4567:4567 -d backend-flask`

Full command now looks like:  
`docker container run --rm -p 4567:4567 -e FRONTEND_URL='*' -e BACKEND_URL='*' -d backend-flask`

App now runs successfully:  
![image](https://user-images.githubusercontent.com/25149022/227741192-70653f64-4cd9-4e44-94dc-55e667a3b00c.png)

Using docker-compose.yml, we are building and running multiple containers in a go.

```
version: "3.8"
services:
  backend-flask:
    environment:
      FRONTEND_URL: "https://3000-${GITPOD_WORKSPACE_ID}.${GITPOD_WORKSPACE_CLUSTER_HOST}"
      BACKEND_URL: "https://4567-${GITPOD_WORKSPACE_ID}.${GITPOD_WORKSPACE_CLUSTER_HOST}"
    build: ./backend-flask
    ports:
      - "4567:4567"
    volumes:
      - ./backend-flask:/backend-flask
  frontend-react-js:
    environment:
      REACT_APP_BACKEND_URL: "https://4567-${GITPOD_WORKSPACE_ID}.${GITPOD_WORKSPACE_CLUSTER_HOST}"
    build: ./frontend-react-js
    ports:
      - "3000:3000"
    volumes:
      - ./frontend-react-js:/frontend-react-js

# the name flag is a hack to change the default prepend folder
# name when outputting the image names
networks: 
  internal-network:
    driver: bridge
    name: cruddur
```

![image](https://user-images.githubusercontent.com/25149022/227741719-66352088-485f-474b-bd35-addee618ec2a.png)

