# Nginx를 시용한 정적 페이지 서버 만들기
1. Ref : https://hub.docker.com/_/nginx/ 
2. Docker Image : nginx:latest
3. Port : 80
4. index.html 경로 : /usr/share/nginx/html
5. index.html 

  &lt;html&gt;
    &lt;head&gt;
      &lt;title&gt;도커 이미지 예제&lt;/title&gt;
      &lt;meta http-equiv="Content-Type" content="text/html; charset=utf-8"/&gt;
    &lt;/head&gt;
    &lt;body&gt;
      &lt;h1&gt;Nginx 서버를 도커 이미지로 만들었습니다.&lt;/h1&gt;
    &lt;/body&gt;
  &lt;/html&gt;

6. dockerfile
  FROM nginx:latest

  WORKDIR  /usr/share/nginx/html
  COPY    index.html  ./

  EXPOSE   80
