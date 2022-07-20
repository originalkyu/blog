---
title: "Nodejs Lecture2"
date: 2022-07-17T22:10:19+09:00
type: 
draft: false
---

## NPM
* Node.js 프로젝트를 관리하는 필수적인 도구이다. 
* 온라인 저장소와 커맨드라인 도구로 구성
#### NPM 온라인 저장소
* 수많은 오픈소스 라이브러리와 도구들이 업로드되는 저장소
* 거대한 생태계를 보유하고 있고, 필요한 라이브러리나 도구를 손쉽게 검색 가능
#### 커맨드라인 도구
* 프로젝트 관리를 위한 다양한 명령어를 제공
* 저장소에서 라이브러리, 도구 설치
* 프로젝트 설정/관리
* 프로젝트 의존성 관리

## NPM 실행
#### 프로젝트 생성하기
```JS
npm init
```
* 프로젝트 디렉터리를 생성하고, 해당 디렉터리 안에서 npm init 명령어를 사용한다

---

## 실습
```JS
1. 디렉토리를 만들어서 이동한다
2. npm init 
3. 전부 엔터를 눌러서 기본 설정을 함
4. cat package.json
5. npm install dayjs
6. cat package.json // dayjs 를 확인할 수 있다
7. ls node_modules
8. cat package-lock.json // dependency를 확인할 수 있다
9. rm -r node_modules/
10. npm i // 삭제한 모듈이 다시 설치된다
11. npm i cowsay --save-dev
12. cat package.json // devDependencies가 추가된 것을 확인할 수 있다
13. ls node_modules/ // cowsay 뿐만이 아니라 다양한 패키지가 추가되었음을 확인할 수 있다
14. cat package-lock.json // 많은 패키지가 추가된 것을 확인 가능하다. cowsay를 찾아보면 다양한 모듈을 
    // 요구하고 있는데, 그 모듈들은 다시 다른 모듈을 필요로하기 때문이다
15. cat package.json // scripts 에 아직 test가 정의되지 않았음을 확인할 수 있다
16. vi package.json 하고, scripts에 "say-hi": "cowsay\"HI|"" 추가한다.
    // test에서 줄바꿈하기 전에 , 를 넣는 것에 주의
17. npm run say-hi를 하여 실행할 수 있다
18. npm remove cowsay
19. cat package.json // devDependecies가 비어있는 것을 확인 가능
20. ls node_modules // cowsay 패키지 뿐만이 아니라 cowsay가 의존하던 패키지들도 전부 삭제된 것을 확인 가능
```