# 1. node 이미지 사용
FROM    node:12-alpine

# 2. 패키지 우선 복사
COPY    server.js /app/

# 3. WEB 서버 실행 (Listen 포트 정의)
EXPOSE 8080
CMD    node server.js