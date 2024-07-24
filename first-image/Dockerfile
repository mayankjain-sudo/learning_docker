FROM ubuntu:latest
# Setting working directory in the image
WORKDIR /app
# copy the files from the host fs to image fs
COPY . /app

RUN apt-get update && apt-get install -y python3-pip

# Set environmant variables
ENV NAME World
# Run command to start the application
CMD ["python3", "app.py"]
