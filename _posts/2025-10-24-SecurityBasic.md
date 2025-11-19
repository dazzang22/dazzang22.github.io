---

---

## 보안 3대 요소

기밀성  
무결성  
가용성  

# 공격 기법 

## DoS 공격 종류 - 직접 공격, 자원 고갈

* SYN FLOODING - SYN 패킷 대량 공격
* UDP FLOODING - 대량의 UDP 패킷으로 ICMP 패킷 대기
* Smurfing - ICMP Echo 패킷의 출발지를 공격대상의 주소로 위조 
* Ping of Death - ICMP 패킷의 사이즈를 매우 크게 만들어 부하 多
* Land Attack - 출발지 도착지 주소 same
* Tear Drop - IP fragment offset 중첩 이용해 재조립 오류
* Bonk - 패킷 똑같은 번호로 전송
* Boink - 패킷 번호 비정상적

DDoS 공격 - 공격 지시, 다수의 공격자

DRDos 공격 : 출발지 IP 변조로 echo 공격

## 애플리케이션 공격

## 네트워크 공격 종류

* Sniffing - 데이터만 훔쳐봄
* 네트워크 스캐너, 스니퍼 - 취약점 찾는 도구
* Password Cracking - 사전 크래킹(사전파일), 무차별 크래킹(랜덤), 패스워드 하이브리드 공격, 레인보우 테이블 공격(해시)
* IP Spoofing - IP 정보 위조
* ARP Spoofing - MAC 주소 위조
* ICMP Redirect - ICMP 를 스니핑함
* 트로이 목마 - 프로그램 실행 시 악성 코드

## 시스템 보안 위협

**버퍼 오퍼플로우 , 백도어** 

​	스택 버퍼 오버플로우
​	힙 버퍼 오버플로우 

대응 방안

​	스택가드

​	스택실드

​	ASLR

 

# 서버 인증

## 인증기술 유형

* Smth u knw
* Smth u have
* Smth u r
* Smth u do

## 접근 통제 유형 / 모델

### 유형

* DAC - Discretionaty Access Control (신분)
* MAC - Mandatory Access Control (Rule 기반)
* RBAC - Role Based Access Control (중앙관리자가 부여한 Role 기반)

### 모델

* 벨-라파듈라 모델 - MAC
* 비바 모델 - 벨라파듈라 보안한 MAC

## 3A - 인권계

* Authentication (인증)
* Authorization (권한 부여)
* Accounting (계정 관리) 

## 인증 관련 기술

* SSO - Single Sign One 
* 커버로스 - MIT, 대칭키 
* OAuth - 외부 계정 기반 토큰 인증

# 암호화 알고리즘

## 양방향 방식 - 대칭 / 비대칭

### 대칭키 알고리즘

* DES - IBM 개발 블록 64bit 키 56bit
* 3DES - DES 3번적용
* SEED - KISA 개발, 16개의 64bit 라운드키
* AES - DES 보완, 128bit 블록
* ARIA - 한국 블록암호화 알고리즘
* IDEA - DES 대체 스위스기반
* LFSR - 시프트 레지스터
* Skipjack - 

### 비대칭키 알고리즘

* 디피-헬만 : 최초의 공개키 알고리즘
* RSA : 소인수분해
* ECC : RSA 보완, 타원곡선
* ElGamal 

## 일방향 방식 - 해시

### 해시 알고리즘 종류

* MD5 - MD4 보완
* SHA -1 : 160bit hash생성
* SHA-256/384/51 
* HAS-160 : 국내표준서명알고리즘
* HAVAL : 메세지 1024비트

# 데이터 암호화 - 안전 전송

* PPTP - 2계층 데이터링크에서 IP 헤더로 캡슐화
* SSL/TSL - 4계층 전송, 7계층 응용에서 클라-서버 암호화 통신
* S-HTTP - http 애플리케이션 메세지 암호화 기술
