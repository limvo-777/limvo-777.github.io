---
title: "Network Protocol"
date: 2021-01-28
categories: Network
---
o Telnet :
Application 계층
인터넷이나 로컬 영역 네트우크 연결에 쓰이는 네트워크 프로토콜
프로토콜의 클라이언트 일부 기능이 추가된 소프트웨어
telnet의 보안 문제로 인해 원격 제어를 SSH로 대체
23번 포트를 주로 사용
o FTP :
Application 계층
파일전송프로토콜
TCP/IP 프로토콜을 가지고 서버와 클라이언트 사이의 파일 전송을 위해 사용하는 프로토콜
ㅁ 명령/데이터전송 연결
명령 연결 : 제어 포트인 서버 21번 포트로 사용자 인증, 명령을 위한 연결 생성 후 여기를 통해 클라이언트에서 지시하는 명령어 전달
데이터 전송용 연결 : 실제 파일 전송은 필요할 때 새로운 연결
ㅁ 능동/수동(Acitive/Passive) 모드
능동모드 : 서버가 자신의 데이터 포트인 20번 포트에서부터 클라이언트가 지정한 지점으로 데이터 연결 (1023<클라이언트 포트)
           클라이언트가 방화벽, NAT(IP 마스킹) 등을 사용하는 환경일 때 동작 x (거의 대부분 사용 -> 능동모드 사용 거의 x)
수동모드 : 클라이언트가 서버의 지정한 포트로 연결, 보통 양쪽 포트 모두 1023보다 큰 포트를 사용한다
TCP stream => 연결 시작부터 끝까지 보여줌
ftp-data 는 데이터를 보낼때마다 세션 생성 -> TCP stream으로 보면 다 짤려서 보임
exe 파일 헤더 MZ으로 시작
o ARP/ICMP:
Network 계층
ㅁ주소 결정 프로토콜(Address Resolution Protocol, ARP)
네트워크 상에서 IP 주소를 물리적 네트워크 주소로 대응(bind)시키기 위하여 사용되는 프로토콜
ㅁ방식
호스트 A가 호스트 B에게 IP 패킷 전송 (호스트 B의 물리적 네트워크 주소 모름)
ARP 프로토콜 사용 (호스트 B주소, 브로드캐스팅 물리 주소 ARP 패킷 전송)
호스트 B는 자신의 IP 주소가 목적지에 있는 ARP 패킷을 수신
자신의 물리주소를 A에게 응답
ㅁARP Table
각 IP 호스트의 ARP 캐시라 불리는 메모리에 테이블 형태로 저장
패킷을 전송할 때 다시 사용
ㅁRARP
ARP와는 반대로 IP 호스트가 자신의 물리 네트워크 주소는 알지만 IP 주소를 모르는 경우, 서버로부터 IP 주소를 요청하기 위해 RARP 사용
ㅁICMP
ㅁICMP의 필요성 (IP 신뢰성 x 때문)
IP는 최선형 전달 서비스만 지원하기 때문에 IP 패킷이 전송되는 목적지에 전달되지 못함 (결과를 모름)
전달되더라도 원하는 서비스 IP가 존재하지 않는 경우도 발생
오류에 대한 보고 기능과 네트워크 상태 진단 기능을 통해 IP를 보조하는 기능을 수행
ICMP는 IP로 캡슐화되며 IP헤더의 프로토콜 필드값을 1로 설정하여 ICMP 메시지임을 나타냄
o HTTP/DNS :
Application 계층
ㅁ HTTP
HyperText Transfer Protocol : www 상에서 정보를 주고 받을 수 있는 프로토콜
주로 html 문서를 주고 받는데에 쓰임
주로 TCP 80번 포트 사용
HTTP는 클라이언트와 서버 사이에 이루어지는 요청/응답(Request/Response) 프로토콜
전달되는 자료는 http:로 시작되는 URL(인터넷 주소)로 조회
o 메소드
GET, HEAD, POST, PUT, DELETE, TRACE, OPTIONS, CONNECT, PATCH
PUT, DELETE : 해당 웹 서버 페이지 임의 생성 삭제 가능 (위험)
GET : URL 해당하는 자료 전송 요청 (header)
POST : body에 데이터를 담아서 요청  (header+body) - 메일, 민감한 정보 등 body에 담겨져 전송
ㅁDNS
Domain Name System
호스트의 도메인 이름을 호스트의 네트워크 주소로 바꾸거나 그 반대의 변환 수행
도메인 이름을 숫자로 된 식별 번호(IP 주소)로 변환
IP 주소로 변환하고 라우팅 정보를 제공하는 분산형 데이터베이스 시스템
o Recursive Query : 
DNS 서버 : 캐시 정보 저장 (refreshing 수행)
DNS 서버에 IP 정보가 없으면 DNS (Root Server)
-> DNS (.com, Name Server) -> DNS (example.com, Name Server)
A : ipv4, AAAA : ipv6
o SMB:
Server Message Block
도스나 윈도우에서 파일이나 디렉터리 및 주변 장치들을 공유하는데 사용되는 메시지 형식
NetBios는 SMB 형식에 기반을 두고 있으며, 많은 네트워크 제품들도 SMB를 사용
(랜매니저, 윈도우 포 워크그룹, 윈도우 NT, 랜 서버 등)
서로 다른 운영체제 사이에 파일을 공유할 수 있도록 하기 위해 SMB를 사용
SMB는 대부분 마이크로소프트 윈도우를 실행하고 있는 컴퓨터에서 이용
윈도우 2003, win7, vista 이상
o 워너크립토 유포 PCAP 분석
SMB 접속을 위한 3 way Hand Shake
