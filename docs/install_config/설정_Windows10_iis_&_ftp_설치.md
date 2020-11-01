---
layout: default
title: iis & ftp 기본 설치 및 설정
parent: Install and Config
---

# iis & ftp 기본 설치

1. 제어판 > 프로그램 > 프로그램 및 기능 > Windows 기능 켜기/끄기

2. "인터넷 정보 서비스" 박스를 한번 클릭하여 기본 설정 (박스안에 검은 정사각형 생김)

3. "인터넷 정보 서비스 > ftp 서버" 모두 체크

4. "World Wide Web 서비스 > 응용 프로그램 개발 기능" 다음 체크  
   (NET Extensibility 4.8, ASP, ASP NET 4.8, CGI, ISAPI 필터, ISAPI 확장)

5. "World Wide Web 서비스 > 일반적인 HTTP 기능"  
정적 콘텐츠 체크 확인

6. "웹 관리 도구" IIS 관리 콘솔 체크

<br>

# ftp 설정

1. 제어판 > 관리 도구 > 고급 보안이 포함된 Windows Defender 방화벽

2. 인바운드 규칙 : "FTP 서버 보안, FTP 서버 수동, FTP 서버"  
'규칙 사용' 선택

3. 아웃바운드 규칙 : "FTP 서버 보안, FTP 서버"  
'규칙 사용' 선택

4. IIS 관리자 : FTP 추가

<br>

# http error 500.24 - internal server error 
관리되는 통합 파이프라인 모드에 적용되지 않는 ASP.NET 설정이 있는 경우.

1. IIS 관리자 > 응용 프로그램 풀

2. "관리되는 파이프라인 모드" 클래식으로 모두 수정

<br>

# http error 404.3 - not found iis 10 aspx

1. 제어판 > 프로그램 > 프로그램 및 기능 > Windows 기능 켜기/끄기

2. "NET Framework 4.8 Advanced Services > WCF 서비스"  
'HTTP 활성화' 체크

<br>

# IIS에서 Microsoft Access 데이터베이스와 함께 클래식 ASP 사용

### 64 비트 시스템 작업 :  
아쉽게도 64 비트 ODBC 드라이버가 없으므로 64 비트 시스템에서는 응용 프로그램을 32 비트 모드로 실행해야한다.  
이렇게하려면 다음 단계를 실행한다.

>a) 인터넷 정보 서비스 (IIS) 관리자를 연다.  
b) 연결 창에서 '응용 프로그램 풀'을 선택한다.  
c) 작업칸에서 '응용 프로그램 풀 기본값 설정'에 들어가 지정 트루을 위한 '32 비트 응용 프로그램'을 활성화한다 .

참고 : ODBC 연결 관리를위한 64 비트 제어판 애플릿은 32 비트 ODBC 드라이버를 표시하지 않는다. 이 문제를 해결하려면 32 비트 ODBC 애플릿을 열어야한다.  
이렇게하려면 다음 단계를 실행한다.

>a) 시작을 클릭 한 다음 실행을 클릭 한다.  
b) 다음 명령을 한다.  "%windir%\syswow64\odbcad32.exe" + 엔터  
c) '추가'버튼 클릭  
d) 'Microsoft Access Driver(*.mdb)' 선택 후 마침 클릭  
e) 데이터 원본 이름 : "Gustave0510v2.mdb" 입력 후 확인  
f) 데이터베이스에서 선택 버튼 클릭  
g) 해당 디렉터리에 있는 Gustave0510v2.mdb를  선택하고 확인

<br>

# IIS FTP - 탐색기로 파일 업로드시 오류  

오류 내용
******************
220 Type set to I.  
227 Entering Passive Mode  
451 No mapping for the Unicode character exists in the target multi-byte code page.
******************

1. WIN+R  →  inetmgr : 인터넷 정보 서비스 (IIS) 관리자를 연다.
2. 사이트  →  FTP 사이트 이름에서 우클릭  →  FTP 사이트 관리  →  고급 설정
3. UTF8 허용 항목을 False로 변경.
4. FTP 서버 재시작.
