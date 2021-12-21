# freelec-webservice

## 1장. intelliJ로 스프링 부트 시작하기
### 1.1 Eclipse에 비해 IntelliJ의 강점
```
- 강력한 추천기능
- 훨씬 더 다양한 리팩토링과 디버깅 기능
- 이클립스의 깃에 비해 훨씬 높은 자유도
- 프로젝트 시작할 때 인덱싱을 하여 파일을 비롯한 자원들에 대한 빠른 검색 속도
- HTML, CSS, JS, XML에 대한 강력한 기능 지원
- Java, Spring Boot 버전업에 맞춘 빠른 업데이트
```

### IntelliJ 설치
회사에서 라이센스를 할당 받았어서 IntelliJ Ultimate 버전으로 다운받고 activation code를 사용
![1_jetbrain](https://user-images.githubusercontent.com/55985137/146967277-e18942f7-afbb-43c3-980f-46075687ad7a.png)

### 1.4 gradle 프로젝트를 스프링부트 프로젝트로 변경하기

#### 에러 사항 정리
1번 코드
```java
apply plugin: 'java'
apply plugin: 'eclipse'
apply plugin: 'org.springframework.boot'
apply plugin: 'io.spring.dependency-management'
```
##### < 에러 >
![2_apply plugin 빌드 에러](https://user-images.githubusercontent.com/55985137/146971241-5645dba1-aa68-4915-890f-fbfae5850877.png)
##### < 해결 >
gradle에서 아래 코드를 삭제 후 다시 빌드
```java
plugins {
  id 'java'
}
```
***

2번 코드
```java
dependencies {
  compile('org.springframework.boot:spring-boot-starter-web')
  testCompile('org.springframework.boot:spring-boot-starter-test')
}
```
##### < 에러 사항 >
![3_빌드에러로그](https://user-images.githubusercontent.com/55985137/146974255-b382ca76-6e99-457c-acaf-88901af89396.png)

##### < 해결 >
책 기준의 gradle 버전과 현재 gradle 버전의 차이가 생기면서 compile 명령어가 사라진 것 같아서 gradle 버전을 [jojoldu님의 github](https://github.com/jojoldu/freelec-springboot2-webservice)를 참고하여 세팅을 변경

프로젝트 루트 > gradle > wrapper > gradle-wrapper.properties gradle 버전을 4.10.2로 변경 후 gradle 다시 빌드
![4_gradle properties 수정](https://user-images.githubusercontent.com/55985137/146974492-da0c3adf-8b97-4a7b-a9d9-b2b4d00fea9f.png)
