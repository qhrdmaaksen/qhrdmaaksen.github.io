---
layout: single
title: "리눅스 이론01"
---

## 대학 리눅스 이론정리 

```js
vmware install , vmware-config setting ( spec )
VMware 특징
  - 1대의 컴퓨터만으로 실무 환경과 거의 비슷한 네트워크 컴퓨터 환경의 구성이 가능
  - 운영체제의 특정 시점을 저장하는 스캡숏 기능을 사용할 수 있다
  - 하드 디스크 등의 하드웨어를 내 맘대로 여러 개 장착해서 테스트할 수 있다
  - 현재 컴퓨터 상태를 그대로 저장해 놓고 다음 사용할 때 현재 상태를 이어서 구동 가능

cmd ipconfig 에서 ip check, 만약 원하는 ip 있다면 vmware workstation pro 에서 edit 에서 ip 변경 설정가능

서버 고정 ip 지정을 안해주면 DHCP 서버에서 자동으로 IP 할당
```

![vmwareNetworkDetail.png](../img/vmwareNetworkDetail.png)

```js
vmware install
- installFile Folder create
- installFile Folder in vmware workstation download
- vmware workstation pro edit network ip setting
- installFile Folder in fedora download
- Server, Server(B), Client Folder create
- vmware Player create && spec setting
- fedora cd room use install
- vmware execute
- Server = 설치 요약 -> 소프트웨어 선택-> development and creative select 누른 후 왼쪽 위 완료 선택
-- 설치대상-> 하드클릭해서 체크된상태 확인 후 완료 선택 ->  설치옵션 계속하기전 내 디스크 -> 파티션 스키마 표준선택 ->
-- 플러스버튼 누른후 마운트 지점에 swap 선택 원하는 용량 4g 선택 -> 플러스누르고 마운트 슬레쉬 선택 원하는 용량 선택안함 -> 완료 선택 -> 설치시작 -> 아이디 암호 설정 -> 완료되면 재부팅 -> 로그인 후 오른쪽 위 사용자 정보 설정-> 디스플레이설정-> 디스플레이설정후 왼쪽 위 현재활동에 제일 아래 클릭 후 모두 클릭 -> 유틸리티 선택-> 터미널 즐겨찾기추가-> 다음 소프트웨어 클릭-> 왼쪽 위 소프트웨어 눌르고 최신 끄기-> 재클릭 전용 끄기-> 재클릭 소프트웨어 공급원 클릭 업데이트확인 하지않기 선택-> 현재활동에 터미널 선택-> cd /etc/yum. repos. d/ -> mkdir backup -> ls -> mv fedora-up* backup -> ls-> backup fedora.repo 확인-> yum -y install system-config-network-> system-config-network -> 네트워크설정 엔터 ->DHCP사용 없음 ->고정IP 입력 ->넷마스크설정 ->게이트웨이설정 ->DNS SERVER 설정 -> 저장 -> 저장&종료 -> terminal 에 systemctl restart network  -> ifconfig -> gedit /etc/sysconfig/selinux -> selinux=disabled 변경 -> 저장 후 닫기 -> 오른쪽위 사용자 설정 ->전원 절전 안함으로변경 -> 전원끄기 ->

스냅샷잡기
-workstation pro 에서 파일 누르고 오픈으로 Server 선택 -> 위에 vm 옵션에 스냅샷 ->take snapshot -> 이름및셋팅 -> 스냅샷지점으로 이동하려면 vm에 스냅샷에 스냅샷 매니저에서 지정한이름으로 위치로 goto  -> player 에서 부팅후 정상작동확인

Client mode 에서 manager mode 변경 = terminal 에서 su - 입력

text mode
- 초기설정을 영어로 쓴다
- 자원을 적게사용한다
- 소프트웨어설정에서 minimal install 선택
- 파티션은 swap 4g
- 필수 패키지2개 = 명령어 yum -y install net-tools system-config-network-tui
- system-config-network -> 네트워크 설정(dhcp 끄기)
- vi text mode 명령어 = vi /etc/sysconfig/selinux -> selinux = disabled 변경(i 누르면 insert mode)-> esc -> :wq(console mode)

-- 해상도 변경
- vi /boot/grub2/grub.cfg -> :set nu -> 75행 -> gfxpayload=800x600x16, 800x600 -> esc :wq

- 재시작 reboot
- 비번 변경 passwd
- 파일 옮기기
-- cd /etc/yum. repos. d/ ->mkdir backup -> ls -> mv fedora-up* backup -> ls-> backup fedora.repo 확인

- 필수 패키지5개 = 명령어 yum -y install bind-utils ncftp wget unzip tar

WinClient 설치
-

```
