# Docker Command

**Build**
`docker build -t image_name .`


**Run with specified environment**
`docker run -e ASPNETCORE_ENVIRONMENT=PreProduction image_name`


**Run with specified port**
`docker run -e ASPNETCORE_ENVIRONMENT=Development -p 8000:80 image_name`


**Run with specified cpu and memory**
`docker run -it --cpus="0.05" --memory="512Mi" image_name`


**Run with specified port and cpu and memory**
`docker run -e ASPNETCORE_ENVIRONMENT=Development -p 8080:80 -it --cpus="0.05" --memory="512Mi" image_name`


**Run**
`docker run -e ASPNETCORE_ENVIRONMENT=Development -p 8080:80 image_name`


**Show all images of docker**
`docker images`


**Dotnet Run Command**
`dotnet run ASPNETCORE_ENVIRONMENT=Development`