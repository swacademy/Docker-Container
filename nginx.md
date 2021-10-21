# Nginx를 시용한 정적 페이지 서버 만들기
1. Ref : https://hub.docker.com/_/nginx/ 
2. Docker Image : nginx:latest
3. Port : 80
4. index.html 경로 : /usr/share/nginx/html
5. index.html 

  <html>
    <head>
      <title>도커 이미지 예제</title>
      <meta http-equiv="Content-Type" content="text/html; charset=utf-8"/>
    </head>
    <body>
      <h1>Nginx 서버를 도커 이미지로 만들었습니다.</h1>
    </body>
  </html>

6. dockerfile
  FROM nginx:latest

  WORKDIR  /usr/share/nginx/html
  COPY    index.html  ./

  EXPOSE   80
