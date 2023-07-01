장고 개발순서
-뼈대만들기 : 필요한 파일생성 
-모델 코딩 : 테이블 사항들 개발 - models.py   
-URLconf : url 및 뷰 매핑관계 정의 -urls.py
-템플릿코딩 : 화면 UI개발,html - templates

- settings.py : 프로젝트 설정파일임, 데이터베이스 설정, 애플리케이션등록,템플릿 항목 설정, 정적파일 항목 설정, 타임존 지정
- models.py : 


1. 뼈대 
1.1 프로젝트 생성 : django-admin startproject <프로젝트 이름>

1.2 - settings.py 설정하기
    - Allowed_host: 개발모드, 운영모드 설정과 도메인 설정 공간
    - INSTALLED_APPS : 생성한 앱 등록 공간  
    - TMEPLATES - DIRS[사용할 탬플릿 위치] : 생성한 템플릿 등록 공간 
    - DATABASES: 데이터베이스 엔진과 버전관리 공간
    - TIME_ZONE: 시간대 설정 공간
    - STATIC_URLS : 정적파일(이미지, CSS 등)위치 설정 공간  
    - MEDIA_URL: 미디어관련 사항 설정 공간 # VS코드에선 본 적없음

1.3 기본 테이블 생성 
    - python manage.py migrate: 데이터 베이스의 변경사항을 반영해주는 명령어 git 커밋이랑 비슷함 버전관리

1.4 슈퍼유저 생성
    - python manage.py createsuperuser: 어드민사이트 관리자 생성

1.5 애플리케이션 생성 및 등록
    - python manage.py startapp <앱이름>: 애플리케이션 생성 명령어,  앱디렉토리와 필요한 하위 디렉토리 생성해줌
    - settings.py/INSTALLED_APPS에 등록: 앱이름 혹은 앱의 설정 클래스(앱이름.apps.앱이름Config) 입력해주기
        - 애플리케이션 설정 클래스란: 앱이름, 라벨, 별칭, 경로등을 설정함 앱이름만 설정파일에 등록할 시 AppConfig 자동으로 설정됨

2. 모델: 데이터베이스 테이블을 생성하는 작업
2.1  테이블 정의 models.py 
    - 하나의 클래스로 테이블을 정의 : django.db.models.Model을 상속받아 정의함 from django.db import models,  class 클래스명(models.Model)
    - 테이블의 컬럼(세로)을 클래스변수로 정의함

2.2 Admin사이트에 테이블 반영
    - <테이블 클래스명>Admin 클래스는 어드민 사이트에 어떻게 보여줄지 정의하는 클래스임
        # 테이블 생성시 models.py, admin.py 가 항시 수정해야함

2.3 데이터베이스 변경사항에 반영
    - python manage.py makemigrations 앱이름: 해당 앱 디렉토리에 마이그레이션을 생성함, git init과 비슷함
    - python manage.py migrate : 로그를 남김 git commit과 비슷함

3. URLconf - urls.py : url을 매핑해주는 작업 모든 주소를 프로젝트의 url.py에 정의 가능하나 나중에 코드가 길어지고 관리하기 힘들어져 앱마다 urls.py를 만들어 관리함

    - url.py에 urlpatterns =[path(위치, view 함수 혹은 클라스(as_view), name = ''] : as_view는 진입메소드임 장고가 url을 함수로 해석해서 클래스사용시 사용해줘야함

4. view정의
    - 






