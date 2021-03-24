## Docker có 3 thành phần chính
* Docker client
* Docker Host
* Docker Registry (Docker Hub)
## Docker image
*Liệt kê các image*   
` docker images `
## Chạy một contaniner
*Chạy một contaniner từ images*  
` docker run <image:tag> `  
*Kiểm tra các container đang chạy*  
` docker ps`  
*Liệt kê tất cả các container đang chạy và đã dừng*  
`docker ps -a`  
*Liệt kê container vừa dừng*  
`docker ps -l`  

## Vòng đời của docker
![alt](docker_life.png)  
*  `docker run`  nhận đầu vào là image và nhận đầu ra là container
* `docker commit` nhận đầu vào là một container và đầu ra là một image
*Tạo một images từ một container đã dừng*  
`docker commit <container id> <name>:<tag>`  
*Liệt kê các images*  
`docker images`  
*Gắn tag cho image*  
`docker tag <image id> <name>:<tag>`