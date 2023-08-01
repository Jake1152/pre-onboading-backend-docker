# from yubin and I add comment to alomost every line 
// 도커 이미지 pull 받아오기 (httpd)
// docker hub로부터 image를 가져온다
docker pull httpd

// 이미지 잘 받아와졌는지 확인하기, image 목록을 볼 수 있다
docker images

// index.html 만들기
echo "Hello World" > index.html

// 홈에 있는 test 폴더를 마운트 시킬것임
docker run -p 8888:80 -v ~test:/usr/local/apache2/htdocs httpd

// 현재 실행중인 도커 컨테이너 목록 확인
docker ps 

// 나온 컨테이너 id 를 exec 한다 (/bin/sh는 exec 명령어로 접속시 사용하는 로그인쉘을 지정하는 명령어)
Exec -it {{컨테이너 id}} /bin/sh

// 도커 파일 만들기
cat > Dockerfile
FROM httpd:latest
COPY  index.html /usr/local/apache2/htdocs/index.html
EXPOSE 80
Ctrl + D

// 도커 이미지 만들기
// -t는 tag image에 이름을 만들어준다
docker build  -t my-httpd .

// 도커 이미지 만들어졌는지 확인하기
docker images

// 빌드한 이미지 실행하기
docker run -p 8888:80 my-httpd
```
