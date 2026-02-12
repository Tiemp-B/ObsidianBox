## OSI(Open Systems Interconnection Reference Model) 7 계층
### OSI 7 계층의 개요
1. OSI 7 계층의 정의
	- 이기종 시스템 간 상호 통신을 위하여 국제 표준화 기구(ISO)에서 네트워크 프로토콜 디자인과 통신 계층을 구성함
2. OSI 7계층의 특징
	- 실제 구현에 대한 언급은 없고 실제 네트워크 구현 시 참조 모델로 사용
	- 캡슐화 : 상위 계층에서 하위 계층으로 데이터를 전달할 때 헤더와 트레일러를 추가 후 전송
	- 역캡슐화 :수신할 때, 헤더와 트레일러를 제거하고 분석하여 상위 계층으로 전달
### OSI 7 계층 세부 설명
1. 물리 계층 (Physical Layer)
	- 네트워크의 전기적 물리적 연결 담당
	- 유선: 케이블 종류
	- 무선: 무선 주파수 링크
	- 관련 장비: 허브, 리피터
2. 데이터 링크 계층 (Data Link Layer)
	- 2개의 노드가 직접 연결되어 있을 때 프레임 단위로 데이터 전송을 수행
	- 노드 간 식별을 위해 MAC(Medium Access Control) 주소 보유
	- 송수신 속도는 수신 노드의 속도에 맞춰져야 하며 이를 흐름제어라 한다
		- 정지-대기, 슬라이딩 윈도우 등의 방법이 있다
	- 오류 제어 기능 : 오류 검출과 재전송 수행
		- ARQ (Automatic Repeat Request)
			- 수신 측에서 오류를 감지하면 NAK 반환하고 전송 측에서는 패킷을 재전송
			- 정지-대기 ARQ
			- Go-Back-N ARQ
			- SR(Selective repeat) ARQ
		- FEC(Forward error control)
			- 직접 오류를 정정
	- 세부적 계층
		- 매체 접근제어(Media/Medium Acces Control, MAC ) 계층
		- 논리 연결제어(Logical Link Control, LLC) 계층
	- 관련 장비 : 브리지, 스위치
3. 네트워크 계층
	- 데이터를 패킷 단위로 분할하고 논리적 주소를 설정하여 전송하는 역할
	- 서로 연결된 노드 사이에 여러 노드가 존재하고 이들 사이의 경로 설정하는 라우팅 기능을 제공
	- 
























