**HISTORICAL INTEREST ONLY**

**Livia's fork at https://github.com/livialima/linuxupskillchallenge is now where the action happens.**
***


*Introduction to Linux Server Administration!*

This includes all the source material for the 20 lessons of what was previously a commercial online Linux server admin course - now free for you to learn with! (If you spot any typos or "dead links" simply raise a GitHub "issue").

* Website of the course: https://LinuxUpskillChallenge.org

* Monthly "Linux Upskill Challenge": https://www.reddit.com/r/linuxupskillchallenge/

* Lesson "source": https://github.com/snori74/linuxupskillchallenge

* Chat at: https://discordapp.com/invite/wd4Zqyk

You are free to use this under the terms of the license, but copyright remains with the author.
  
 - Steve

# Linux Command Challenge

Day 03 (03.md) - 보통 root 로 바로 Login 을 하는 것은 좋은 practice 가 아님, root 권한 필요 시 sudo 명령어를 입력 후 실행 되도록 하는게 좋은 방법
				현재 ubuntu 는 sudo 명령어 입력 시 마다 password 인증을 하여야 함
				

				ls /etc/shadow 같은 명령어는 root 권한 상관 없이 파일들을 볼 수 있지만 cat / vi / less 같은 명령어는 root 권한이 필요하여
				그냥 일반 명령어 만으로는 접근이 불가하다.
				
				만약 root 권한이 필요한 작업을 수행 시 sudo cat /etc/shadow 로 앞에 sudo 를 붙여주어 실행을 한다.
				
				timedatectl status 명령어를 통하여 현재 Server 에 셋팅 되어있는 시간 국가 설정 확인이 가능
				timedatectl list-timezones 명령어 입력하면 국가 시간 설정 가능한 List 데이터 출력
				sudo timedatectl set-timezone Asia/Seoul 해당 명령어 입력 시 서버 Setting 시간이 서울로 변경 됨
				
				Wrap

Day 04 (04.md) - sysadmin 으로써 가장 중요한 역할 중 하나는 소프트웨어를 설치하는 것임, 
				 app store 나 market 처럼 Linux 에서 apt 를 사용하여 소프트 웨어 다운로드가 가능
				 
				 apt search "midnight commander" 명령어 입력하여 해당 소프트 웨어 설치가능한지 확인
				 sudo apt install mc 입력하여 mc 소프트웨어를 설치
				 root 계정으로 로그인 한 것이 아니라면 소프트웨어 설치를 위하여 sudo 명령어 입력은 필수

Day 05 (05.md) - 항상 명령어 입력 시 tab 을 사용 하는 습관을 들이면 조금 더 정확하고 빠른 명령어 입력이 가능하다
				 위쪽 화살표를 입력 시 이전에 입력한 명령어 확인이 가능
				 history 명령어 입력 시 cached 된 명령어 확인 이 가능 (입력한 명령어)
				 ls -l : directory 안에 어떤 파일이 존재하는 지 확인 가능
				 ls -al : directory 안에 모든 파일 확인 가능 (. 으로 되어 있는 실행 파일들도 확인이 가능, 숨김 파일도 가능)
				 
Day 06 (06.md) - vim --version 입력 시 vim 에 관련 된 버전 확인 및 정보 확인이 가능
				 vi 는 생긴지 20년이 넘었지만 여전히 표준 에디터로 자리 잡고 있음
				 실습을 위하여 /etc/services 파일을 복사
				 cd
				 pwd
				 cp -v /etc/services testfile
				 vim testfile
				 
				 vi 에디터로 들어간 후 ESC 를 한번 클릭하면 Normal 모드로 돌아감
				 
				 

				 
				 