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
*Chạy nền một container (Detach)*  
`docker run -d <image:tage>`  
*Kiểm tra các container đang chạy*  
` docker ps`  
*Attach một container đang chạy nền*  
`docker attach <container id>`  
*Để Detach trở lại ấn tổ hợp phím Ctrl+P hoặc Ctrl+Q*  
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
## Cơ chế lưu trữ của docker
* Cơ chế lưu trữ copy-on-write
* Tạo một hệ thống mới ngay lập tức mà không cần copy tất cả file hệ thống
* Hệ thống lưu trữ lưu lại mỗi thay đổi
## Chạy các tiến trình trong container
* Container có tiến trình chính
* Container dừng khi tiến trình chính kết thúc
* Container có thể được đặt tên `docker run --name <name container> <image>`  
## Docker exec
* Khởi tạo một process khác bên trong container đã có
* Tiện lợi cho việc debug 
* Không thể thêm port, volume,...
` docker exec -it <container id> <process>`
## Docker create
*dùng để tạo container với các config tương tự như docker run, container không chạy ngay từ đầu mà phải dùng lệnh `docker start`*  
`docker create <image>`
## Docker start/stop/restart
`docker stop <container id>` dùng stop một container  
`docker restart <container id>` dùng khởi chạy lại container đã dừng
## Docker cp
* dùng để copy dữ liệu từ container tới local machine và ngược lại
* dùng được cho cả container stop và running
`docker cp <file local> <dockername>:<đường dẫn file hoặc folder>  
## Docker inspect
* Kiểm tra các thiết lập của Docker (network, driver)
* Các thông tin được trả về dưới dạng json
`docker inspect <container id>`  
## Docker rm
* Dùng để xóa các container dựa theo tên hoặc id
`docker rm <container id>`
* Xóa toàn bộ các container đã stop
`docker rm $(docker ps -a -q)` 
 ## Docker logs
 * Xem output của container
 `docker logs <container id hoặc name>
 * Không nên để cho dung lượng phình quá to
 ## Dừng và xóa container
 * khi không dùng tới container ta nên dừng và xóa nó đi
 `docker kill <container>` dừng container  
 `docker rm <container>` xóa bỏ container  
 ## Giới hạn tài nguyên 
 * Giới hạn memory
 `docker run --memory <total-memory-limit> <image> <command>`  
 *ví dụ*  
 `docker run --memory 512M ubuntu bash`  
 * Giới hạn CPU
 ** Tương đối
 `docker run --cpu-shares=<limit> <image> <command>`  
 *ví dụ:* `docker run --cpu-shares=20 ubuntu bash`  
 ** Thời lượng mà hạn mức
 `docker run --cpu-period=<period-limit> --cpu-quota=<quota-limit> <image> <command>`  
 *ví dụ:* `docker run --cpu-period=40000 --cpu-quota=20000 ubuntu bash`  
 => nếu 1 cpu, thì container chiếm 50% cứ mỗi 40ms
 ## Một số lưu ý:
 * Hạn chế việc để container lấy dependency khi khởi động container
 * Tránh để các file quan trọng trong container không tên



