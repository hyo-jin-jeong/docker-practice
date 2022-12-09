FROM node:16-alpine

WORKDIR /app
# docker 컨테이너 안에서 어떤 경로에서 
# 실행 할 것인지 명시 app이라는 디렉토리 안에 실행하겠다는 의미
# 리눅스에서 cd와 같은 의미를 가짐 

COPY package.json package-lock.json ./
# 우리의 프로젝트 파일을 복사해온다. 

RUN npm ci 
# npm install은 3.x 이상의 버전은 다 괜찮다는 의미로
# 만약 그 이상의 버전이 나오면 버전 업데이트가 진행된다.
# but npm ci로 해놓으면 package-lock.json에 명시된
# 버전으로 설치를 하기 때문에 개발할 때 사용했던 동일한 버전으로 설치 가능하다. 

COPY index.js .

ENTRYPOINT ["node", "index.js"]

# docker file은 layer 형태로 작성하는 것이 좋다.
# 가장 자주 변경되는 것을 나중에 적는 것이 좋다. 
# 위에서부터 layer 0~시작 
# 나중에 소스코드 변경 후 이미지를 다시 만들어야 할 때
# 변경된 최상단 layer만 다시 만들어준다. 
# 나머지는 캐시 된 것을 재활용 
# 효율성 증가 