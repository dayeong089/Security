## 정보보호 3요소
### 1. 기밀성(Confidentiality)
* 정보의 비밀이 유지되고 허가받지 않은 비인가자 또는 프로세스에게 정보가 노출되지 않음
* 접근통제, 암호화
### 2. 무결성(Integrity)
* 비인가자에 의한 정보의 변경을 보호하여 정보의 정확성을 보장
* 물리적 통제, 접근 통제, 인증, 해시
### 3. 가용성(Availability)
* 정보 자산에 대해 적절한 시간에 접근 가능한 것을 의미
* 사용자가 원하는 서비스를 계속 제공받을 수 있어야 한다 

## 정보보호 위협 요소
### 1. 비인가 접근
* 접근이 정상적으로 허락되지 않은 사용자의 접근 통제
* 요구되는 보안 요소(인증) - 정당한 사용자임을 확인, 송/수신자 확인, 제 3자의 위장 확인, 메시지 인증, 객체 인증
### 2. 데이터 도청
* 시스템에 제 3자가 중간에 정보를 보는 수법
* 요구되는 보안 요소(기밀성) - 정보의 비밀 보장
### 3. 데이터 가로막기(Interruption)
* 정보가 중간에 특정 이유로 인해 분실되거나 목적지에 도달하지 못하는 수법
* 요구되는 보안 요소(가용성) - 정보 자산에 대해 적절한 시간에 접근 가능한 것
### 4. 데이터 변조(Modification)/위조(Fabrication)
* 비인가 된 제 3자가 정상적인 데이터를 수정하거나 변조하는 행위
* 요구되는 보안 요소(무결성, 인증) - 비인가자에 의한 정보의 변경을 보호하여 정보의 정확성을 보장
### 5. 부인(Repudiation)
* 데이터의 송/수신 과정에서 자신이 메세지를 송신/수신했다는 사실을 부인(거짓으로)
* 요구되는 보안 요소(부인방지) - 전송 주체가 되는 송/수신자가 송/수신 사실을 부인하지 못하게 함
### 6. 서비스 방해(Denial of service)
* 대량의 서비스 요구를 필요 이상으로 발생시켜 서버가 정상 서비스를 못하도록 방해
* 요구되는 보안 요소(가용성, 인증)

## 보안 공격
* IT시스템에 정보보호를 저해하는 행위
### 1. 소극적 공격(passive attack)
* 전송되는 정보를 가로채서 알아내는 공격 방식, 실제 전달되는 메시지에 아무런 변경사항이 없어 자신이 공격받고 있는지 알 수 없음
* 도청, 가로채기, 트래픽 분석, 로그 분석 > 스니핑 등
### 1-1. 스니핑(sniffing)
* 네트워크 측면에서 네트워크 상에 돌아다니는 트래픽을 몰래 엿보는 행위
* 기밀성을 해치는 기법
* 공격 방법 - ping, ARP, DNS 등등
* 방지 기법 - 데이터의 암호화
### 2. 적극적 공격(active attack)
* 허가받지 않은 상태에서 파일의 삭제, 추가, 변경, 조작 등을 시도하는 공격으로 악의적 의도를 가진 이가 메시지를 조작
* 방해(가용성), 수정(무결성), 재전송, DOS > 스푸핑, 세션 하이재킹 등
### 2-1. 스푸핑(spoofing)
* TCP/IP의 구조적 결함을 이용하여 사용자의 정보를 훔치는 행위 > 중간자 공격(MITM)
* 공격 방법 - ARP, IP, ICMP, DNS
* 방지 기법 - 데이터의 암호화, 난수, 해시

## 네트워크 공격 기법
### 1. 스캐닝(Scanning)
* 스캐닝 - Port scanning > 해킹 공격 전 사전 준비작업으로 현재 서비스 포트의 상태를 확인하기 위해 각 시스템에 포트를 체크하는 공격 기법
* 스캐닝 유형 - ping, TTL, TCP
* 스캐닝 방법 - Sweeps, Open scan, Half open, stealth 등
* 방지 기법 - 필터링 규칙, 불필요한 서비스 중지, IDS 및 IPS 연동
* 본인 pc에 테스트 하는게 좋음 .. 불법 
* 가장 유명한 tool - nmap
* nmap -A [ip주소]
### 2. 무차별 대입 공격(Brute force)
* 특정한 암호를 풀기 위해 가능한 모든 값을 대입하는 공격 기법 = 전사공격 = 사전공격
* 방지 기법 - 필터링, 횟수 제한
### 3. 서비스 거부 공격(Denial of service = DOS 공격)
* 악의적인 목적을 지닌 제 3자가 시스템의 자원을 부족하게 하여 정상적인 서비스를 제공할 수 없도록 방해하는 기법
* 이후 분산 서비스 거부 공격(Distributed Denial of service = DDOS)로 발달
* ex) 한 서버에 엄청난 요청을 보내서 다운시키기
* <공격 기술>
* (1) ping of death(사이즈가 엄청 큰 ping packet을 잘라서 보냄, 사이즈가 엄청 크므로 잘린 패킷이 엄청 많음, 많은 패킷으로 서버 마비)
* (2) syn flooding(요청 패킷을 엄청 보내고 대답 안함, 서버 마비)
* (3) tear drop(자른 패킷을 서버가 조립 번호를 보고 순서대로 조립, 조립 번호를 똑같이 보냄 > 서버가 순서대로 조립 불가능)
* (4) smurf(출발지, 도착지 ip를 똑같이 보냄 > 응답하려고 하는데 출발지가 서버 주소와 같음 > 서버에 패킷이 쌓임)
### 4. 중간자 공격(Man in the middle attack)
* 두 사용자간의 네트워크 통신 사이에 중간자가 침입하여 상대를 속여 통신하는 공격, 원래 통신하던 두 객체는 서로에게 연결되어 있다고 생각
* (1) 송신자가 수신자에게 데이터 암호를 위해 공개키 요청
* (2) 공격자가 메시지 가로채고 자신의 공개키 보냄
* (3) 송신자는 공격자 공개키로 대칭키 전송 > 공격자가 대칭키 소유
* (4) 공격자가 수신자에게 공개키 요청
* (5) 수신자는 공격자에게 공개키 전송
* (6) 받은 공개키로 대칭키를 암호화하여 전송
* (7) 수신자는 대칭키를 얻음
* (8) 공격자는 송/수신자의 공개키, 대칭키를 모두 소유
### 5. 세션 하이재킹(Session hijacking)
* 두 사용자간의 연결을 세션이라고 부름, 이를 가로채는 행위
* 공격자가 인증 작업 등이 완료되어 정상통신을 하고있는 다른 사용자의 세션을 가로채서 별도의 인증 작업 없이 가로챈 세션으로 통신을 계속하는 행위
* 인증 작업이 완료된 세션을 공격하기 때문에 OTP, Challenge/Response 기법을 사용하는 사용자 인증을 무력화
* <Tcp 세션 하이제킹> 
* 서버와 클라이언트 간 통신에서 TCP 시퀀스 넘버를 제어하는데 발생하는 문제를 이용한 공격
* Non-blind attack/Blind attack이 있음
* hunt라는 툴을 이용하여 실습 가능 - 본인 pc로 연습해야 함
* 공격자는 중간자 공격(스니핑/스푸핑)을 통해 서버와 클라이언트의 통신을 엿보고 있음
* 중간에 tcp packet 중 RST 패킷을 서버에게 보내서 새로 연결을 맺자고 한 후 서버와 클라이언트 간 통신 끊음
* 공격자와 서버는 3 hand-shaking을 통해 establish(통신 연결)
* 통신 엿보고 있었으므로 client의 sequence number를 알고 있으므로 client와도 establish
* 이러한 방식으로 서버와 클라이언트 통신을 중간에 가로챔
