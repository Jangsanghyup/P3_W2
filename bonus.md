1. 사용한 명령어들의 설명을 history 기록 기준으로 문서
사용한 명령어들의 설명 (history 기준)

sudo nano /lib/systemd/system/david.service
systemd 서비스 파일을 생성하거나 수정하기 위해 nano 편집기를 관리자 권한으로 실행하는 명령어입니다.

Ctrl + O (nano 편집기 내)
nano 편집기에서 작성한 내용을 저장하는 단축키입니다.

Ctrl + X (nano 편집기 내)
nano 편집기를 종료하는 단축키입니다.

sudo systemctl daemon-reload
systemd에 새로 작성하거나 변경한 서비스 파일을 다시 읽도록 알려주는 명령어입니다.

sudo systemctl enable david.service
시스템 부팅 시 david.service가 자동으로 시작되도록 활성화하는 명령어입니다.

sudo systemctl start david.service
david.service 서비스를 즉시 시작하는 명령어입니다.

systemctl is-active david
david 서비스가 현재 실행 중인지 상태를 확인하는 명령어입니다. (출력으로 active가 나오면 정상 작동 중임을 의미합니다.)

sudo systemctl stop david.service
david.service 서비스를 중지하는 명령어입니다.

2. 가상머신에서 사용 가능한 네트워크 종류와 차이점
   
- NAT	: 기본 설정, 외부 인터넷 접근 가능, 외부에서 접근 불가 웹 개발, 일반 테스트
- Bridged	: 물리 네트워크에 직접 연결, 외부에서 접근 가능	서버 호스팅, 포트 포워딩
- Host-only : 호스트와 가상머신 간 통신만 가능, 내부 테스트, 보안 테스트
- Internal : 가상머신 간 통신만 가능,	격리된 환경 테스트

3. init과 systemd의 차이
   

init : 전통적인 초기화 시스템으로, 매우 오래된 Linux/UNIX 시스템에서 사용되었습니다. 시스템 부팅 시 /etc/inittab 파일을 참조해 실행할 서비스나 런레벨을 결정하고, 필요한 데몬이나 스크립트를 순차적으로 실행합니다.

특징:
- 직렬 처리 방식이라서 모든 서비스가 하나씩 순서대로 실행됩니다.
- 서비스 간 의존성 관리가 불편하거나 불가능합니다.
- 로깅 기능이 제한적이며, 상태 확인이나 재시작 관리가 수동적입니다.
- 유지보수가 어렵고 현대적 시스템에는 비효율적입니다.

systemd : 현대적인 초기화 시스템으로, 대부분의 최신 Linux 배포판(Ubuntu 16.04 이후, CentOS 7 이후 등)에서 기본으로 사용됩니다. 병렬로 서비스를 실행하며, 부팅 속도를 향상시키고, 다양한 관리 기능을 제공합니다.

특징:
- 병렬 처리가 가능하여 부팅 속도가 빠릅니다.
- 서비스 간 의존성을 자동으로 파악하고 관리할 수 있습니다.
- 서비스 상태 확인, 로깅(journalctl), 자동 재시작 등 다양한 기능이 통합되어 있습니다.
- .service 파일을 통해 설정이 직관적이고 관리가 쉬워졌습니다.


- 간단히 말해, init은 전통적이고 단순한 초기화 시스템이고, systemd는 더 빠르고, 강력하며 현대적인 시스템 관리 도구입니다. systemd는 init의 많은 한계를 보완하기 위해 설계되었으며, 현재는 대부분의 Linux 배포판에서 표준으로 채택되고 있습니다.