# ASTS Server

### 실행 방법

1. [Docker](https://docs.docker.com/docker-for-windows/install/) 다운로드 
2. docker를 실행하고 준비가 완료 되었는지 확인
3. docker-compose up -d 명령어를 프로젝트 디렉토리에서 실행
4. docker ps 명령어를 실행해서 프로세스가 현재 잘 올라가 있는지 확인

아래 포트 번호를 사용해서 app과 kibana에 접속 할 수 있습니다.

예시) http://localhost:5601/ <-- kibana 접속

현재 app에 접속하면 자동으로 값이 Postgresql DB에 저장되어 동기화 되고있는 Elasticsearch 에도 값이 저장됩니다. 

##### DB에 저장 하는 방법
1. http://localhost:8000/api 접속
2. department url 클릭
3. Title 에 넣고싶은 이름 기입후 POST 버튼 클릭
4. http://localhost:8000/api로 다시 접속
5. Fullname과 Department는 필수 필드이기 때문에 기입후 POST 버튼 클릭
6. 저장 완료

##### DB에 수정과 삭제 하는 방법
1. http://localhost:8000/api/id/  << 직원의 id 값을 추가

`예시) http://localhost:8000/api/1/` 
2. 저장과 유사한 방식으로 진행
3. Fullname 과 Department는 필수 필드이기 때문에 항상 기입
4. 수정,삭제 완료

##### 확인하는 방법
1. http://localhost:8080 접속
2. 부서를 추가하고 직원을 추가
3. http://localhost:5601 키바나 접속
4. 키바나 페이지에서 dashboard 로 이동
5. Check for new data라는 문구가 뜨면 데이터가 삽입될 때까지 기다리고 Check for new data 클릭
6. Index Pattern에 * 작성
7. Time Filter field name에 `I don`t want to use the Time Filter` 선택, 없으면 스킵
8. 실시간으로 데이터가 동기화


##### Port
* app : 8000
* elasticsearch : 9200,9300
* postgresql : 5432
* kibana : 5601
* logstash : 

---
### Docker 모두 삭제

1. docker rm -vf $(docker ps -a -q) 컨테이너 삭제
2. docker volume rm $(docker volume ls -q) 볼륨 삭제 ,기존 데이터는 전부 삭제 됩니다.
3. docker rmi -f $(docker images -a -q) 이미지 삭제


