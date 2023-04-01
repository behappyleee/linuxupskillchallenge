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

Day 07 (07.md) - Apache2 Webserver install 하기, sudo apt install apache2 명령어 입력하여 apache2 설치
				 Apache2 Webserver 를 설치 후 http://나의ip 로 접속을 하면 WebServer Config 페이지가 처음에 로딩이 된다.
				 서버상에서 Apache2 작동 중인지 확인하기 위하여서는 sudo systemctl status apache2 명령어를 입력하면 작동 중인지 확인이 가능
				 맨처음 로딩 index pag 는 /var/www/html/index.html 이 맨 처음 loading 이 된다. 맨 처음 loading page 를 수정하고 싶을 시
				 index.html 파일을 vi 에디터를 이용하여 편집 한다.
				 Server 관리자로써 공격 가능성을 염두해 두어야 한다. apahce2 웹서버를 설치하면서 22 번 port 에 80 port 에도 취약적이 생겼다.
				 
				 sudo apt update / sudo apt upgrade 최신 보안 사항을 업데이트 하여주기도 한다.
				 
Day 08 (08.md) - 현재 서버는 2개의 서비스가 돌고 있다 sshd / Apache2 해당 2개의 서비스는 logs 를 생성한다. 
				 Plain Text files 는 쉽게 edit 을 할 수 있는 툴들이 몇가지 있다 (grep / cat / more / less / cut / awa / tail)
				 grep 명령어는 powerful 하면서 다루기 쉽기로 유명 하다.
				 
				 cat /var/log/apache2/access.log 명령어를 입력 시 해당 log 전체가 출력이 된다.
				 less /var/log/apache2/access.log 명령어를 입력 후 화살표를 위아래로 움직이면 해당 log 를 볼 수 있다. q 를 누르면 에디터가 종료 된다.
				 sudo less /var/log/access.log 명령어를 입력 시 서버에서 로그인 한 기록 로그 확인이 가능하다.
				 tail /var/log/apache2/access.log 해당 파일의 끝에서 부터 10줄 을 볼 수 있다.
				 tail -f /var/log/apache2/access.log tail 명령어 에서 -f 옵션을 붙일 시 현재 실시간 log 끝을 볼 수 있다.
				 
Day 09 (09.md) - Ports Open and Close
				 TCP/IP ports 22 / 80 
				 Sysadmin 으로써 server 에서 무슨 port 가 열려있는 지 이해를 하고 있어야 한다. 왜냐하면 열려있는 Port 마다 공격 가능성이 있다.
				 열려 있는 Port 는 적절한 Monitoring 이 필요 하다.
				 현재 서버에는 2개의 서비스가 돌고 있다. 22 port 와 80 port 가 돌고 있다. sshd 는 for remote login, apache2 는 for web access 이다.
				 
				 서버에서 열려있는 Port 를 확인하기 위하여서는
				 ss 명령어를 입력 한다 (netstat 은 old version)
				 nmap (nmap 명령어는 default 로 설치 되어 있지는 않다. sudo apt install nmap 명령어를 입력하여 설치를 한다.)
				 
				 ss 를 입력 시 wide range 검색이 가능하지만 우선 ss -ltpn 명령어를 입력한다.
				 80 과 22 open 는 모든 PC 의 Local IP Address 이다. 53 port 는 DNS 서버이다 오직 특별한 Local Address 에서만 열려있다.
				 nmap 을 사용할 시 1000 개 이상의 port 가 확인이 가능하다. nmap 은 유명 하면서도 다루기 쉬우며 Server 에 상태를 scanning 하는 데도 많은 도움이 된다.
				 
				 22 번 Port 는 SSH Service 를 제공하여 준다. connect 를 시도할 시 open 될 것이다. 만약 Apache 가 80/http 도 열릴 것이다.
				 모든 열려있는 Port 는 공격 받을 가능성을 높여준다. 최고의 방식은 사용하지 않는 서비스는 Close 상태를 시키는 것이다.
				 
				 하지만 localhost (127.0.0.1) 은 loopback network device 이다. bound Service 는 오직 local machine 에서만 이용이 가능하다.
				 실제로 무슨 Port 가 외부에 노출 되어 있는지 확인을 하려면 ip a command 명령어를 사용한다.
				 ip a - command to find the IP address 실제 네트워크 그리고 nmap 을 사용한다.
				 
				 Host Firewall
				 Linux Kernel 은 built-in netfilter 라는 Firewall 이 제공 된다. 우리는 이 netfilter 를 다양하게 구성이 가능하다.
				 low-level 은 iptables 이고 그 다음 새로 나온 것은 nftables 이다. nftables 는 매우 강력하지만 또한 매우 복잡하다.
				 또한 가장 사용하기 쉬운 것은 ufw 이다 (uncomplicated firewall)
				 
				 1.
				 `sudo iptables -L` 명령어를 입력한다.
				 
				 2. 
				 `sudo apt install ufw` 명령어를 사용하요 ufw 를 설치 한다.
				 `sudo ufw allow ssh` 
				 `sudo ufw deny http`
				 ! 주의 할 점은 항상 ssh 는 절대 deny 를 하면 안된다 !!! 모든 Server 에 커넥션을 잃을 것이다 !!
				 `sudo ufw enable`
				 
				 `sudo iptables -L` 명령어를 입력 하면 
				 “DROP       tcp  --  anywhere             anywhere             tcp dpt:http” 
				 
				 http 를 deny 하였으니 아까는 Apache webserver 를 설치하여 http 로 접근을 하였지만 http 를 deny 로 설정하여 현재는 접근이 불가하다.
			     ApacheWebserver 가 여전히 구동 중 이지만 outside 에서는 지금은 접근이 불가능 하다. 모든 incomming traffic 은 destination port of http/80 being DROPed.
						
				 `sudo ufw allow http`
				 `ufw enable`
				 
				 때떄로 non-standard port 를 사용이필요 할 떄가 있다.
				 이것은 부분적으로 ssh/22 common advice 이다.
				 `/etc/ssh/sshd_config` 를 설정하는 것을 고려를 해봐야 한다.		

Day 10 (10.md) - Linux 는 Shedule tasks 를 수행 할 여러가지 기능들 이 있다. Schedule Task 를 수행할 수 있는 기능 중 하나는 crontab 이다
				 crontab 은 `crontab -l`  명령어를 입력 시 설정 해 놓은 crontab list 를 확인할 수 있다.
				 
				 `sudo vi /etc/crontab` 명령어를 입력 시 정의 해 놓은 crontab 확인이 가능하다.
				 `# m h dom mon dow user  command` column 을 따라 crontab 정의가 가능하다.
				 
Day 11 (11.md) - locate / find  / grep / which 명령어를 통하여 파일을 찾을 수 있다.
				 `locate access.log` locate 명령어를 통하여 access.log 파일 경로 위치를 알 수 있다.
				 `find /var -name access.log`  find 명령어를 통하여 해당 위치에서 access.log 이름을 가진 파일을 검색 할 수 있다.
				 `find /home -mtime -3` find 명령어를 통하여 /home directory 안 에 3일 안에 변경 된 파일만 조회를 한다. 
				 find 는 특정 구역을 설정하여 해당 구역을 파일이 존재하는 지 검색 할 수 있다.
				 `grep -R`  	
				 `which` which 명령어는 매우 유용한 명령어이다. 해당 명령어는 어떤 프로그램이 어디서 돌 고 있는지 알고 싶을 때
				 매우 유용한 명령어이다.
				 `which nano` 명령어는 해당 파일이 어디서 실행 되는 지 알수가 있다.

Day 12 (12.md) - File 을 다른 시스템과 주고 받는 것을 실습할 것이다.
				 Linux 서버에서 File 을 주고받을 수 있는 여러 프로토콜이 존재한다.
				 (SMB / AFP / WebDAV / FTP / scp / rsync / SFTP)
				 File 을 복사하는 프로토콜은 여러 프로토콜이 존재하지만 SFTP 를 파일 전송에 사용시 많은 이점이 존재한다.
				 (No extra setup is required on your server / Top quality security / Allows browsing through the directory structure / You can create and delete folders)
				 SFTP 프로콜을 사용하여 Linux 에 있는 파일 중 Local Desktop 으로 복사를 해보겠다.

				 Filezila 를 이용하여 ubuntu server 로 접속하였다.
				 	
Day 13 (13.md) - Linux 에 File 시스템은 항상 permission 과 관련이 있다. 
				 ordinary user 로 Login 을 하였을 시 File 을 바로 Linux system 에 upload 를 하지 못하였을 것이다.
				 Linux Permission System 은 꽤 simple 하다.

				-rw------- 	1 steve  staff  	4478979  6 Feb  2011 private.txt
				-rw-rw-r-- 	1 steve  staff  	4478979  6 Feb  2011 press.txt
				-rwxr-xr-x 	1 steve  staff  	4478979  6 Feb  2011 upload.bin	

				user 는 steve 이고 group 은 staff 이다. (r-read, w-write)
				- private.txt => steve 는 rw 를 가지고 있고 staff 와 other people 은 아무것도 가지고 있지 않다.

				- press.txt => steve 는 rw 가 가능하며 group 중 staff 는 rw 가능하다 그 외는 r (read) 만 가능하다.

				- upload.bin => x(execute) steve 는 rwx 가 가능하다 group staff 는 rx 그 외도 rx 만 가능하다.

				chmod 를 이용하여 Permission 변경도 가능하다. 

				user 와 group 으로 나뉜다.
				 '-rw-r--r--" Permission 은 File 을 소유한 User 와 gorup 과 other people 에게 줄 수 있다
				Test 를 위하여 tueseday.txt 파일을 생성 하겠다. (vim tuesday.txt)
				처음 생성시 권한은 -rw-rw-r-- 1 ubuntu ubuntu 
				chmod u-w tuesday.txt	--> user 에 w 권한을 뻇는다.
				chmod g-w tuesday.txt   --> group 에 w 권한을 뻇는다.
				chmod o-r tuesday.txt	--> other user 에 r 권한을 뻇는다.

				group 을 보고 싶으면 그냥 groups 를 타이핑 한다.
				최신 Linux System 은 group 를 생성한다. group 은 요청에 따라 더해질 수 도 있다.

				chmod u+w tuesday.txt	--> user 에 w 권한을 추가한다.
				chmod g+w tuesday.txt   --> group 에 w 권한을 추가한다.
				chmod o+r tuesday.txt	--> other user 에 r 권한을 추가한다.

Day 14 (14.md) -  오늘은 User 를 추가하는 실습을 진행할 것이다.
				  df -h 를 타이핑하여 용량을 확인한다.	
				  Linux user 는 case-sensitive 하다.
				  sudo add user helen 을 타이핑하여 helen user 를 추가한다.
			      Linux 에서는 user 를 추가하면 비밀번호를 바로 묻지않으므로 수동으로 비밀번호를 추가해주어야 한다.

				  user 를 추가하게 되면 /home/ 경로에 생성한 user 에 디렉토리가 자동으로 생성이 된다. 		

Day 15 (15.md) - software 를 apt install 을 이용하여 다운로드를 받았을 것이다. 
				 Linux Model 에서 소프트웨어 설치는 app store 와 매우 유사하다.
				 Package Manager 는 Debian 과 Ubunti Distributions 에서 사용되었다
				 Package Manager 는 apt 명령어를 사용한다.
				 Fedora 와 RHEL CentOS 에서 yum 과 dnf 와 비슷하다.
				 
Day 16 (16.md) - System 관리자로써 archives 파일들을 잘 다루어야 한다.
				 가장 중요한 책임으로는 소프트웨어 설치와 backup 관리를 주요하게 하게 된다.
				 window 에서는 zip 파일이 쓰이지만 Linux System 은 약간 다르다. Linux System은
				 파일들을 모으고 압출하는 것을 한번에 끝내 버린다.
				 현재 Linux 파일들을 snapshop 처럼 만들 수 있다.<br />
				 ```
				 tar  -cvf  myinits.tar  /etc/init.d/
				 ```
				 해당 명령어는 현재 directory 에 tar 압축파일을 만들어 준다.
				 옵션 -v(verbose) 는 feedback 을 포함하는 거다. 전통적으로 압축을 실패하더라도 feedback 을 주지 않았지만 해당 명령어는 압축 실패시 피드백을 준다.
				 -f 옵션은 the output should go to the filename which follows, so in this case the order of the switches is important.
				 
				 tar 확장자는 tape archive 를 줄인거다.
				 GnuZip 파일을 다음 명령어로도 만들 수 있다.
				 ```
				 gzip myinits.tar
				 ```
				 
				 -c 옵션은 creating archive 
				 -v 옵션은 verbose command 를 만들기 위함
				 -z 옵션은 결과를 압축함
				 -f 옵션은 output을 특정함
				 
				 ```
				 tar -cvzf myinits.tgz /etc/init.d/
				 ```

Day - 17 (17.md) - 일반적으로 project 파일들은 source file 들을 제공한다. 
				   installed a standard bundle of common compilers and similar tools. On ubuntu (build-essential)
				   ```
				   sudo apt install build-essential
				   ```
				   nmap 이 설치 되어있는지 확인한다.
				   ```
				   nmap -v 
				   ```
				   어떤것이 executable 이 되었는지 해당 명령어로 확인
				   ```
				   which nmap
				   ```
				   wget 을 이용하여 nmap 7.70 버전을 다운 받는다
				   ```
				   wget -v https://nmap.org/dist/nmap-7.70.tar.bz2
				   ```
				   파일이름의 제일 끝은 확장자이다. 
				   해당 명령어를 통하여 압추된 파일을 풀어준다.
				   ```
				   tar -j -x -v -f nmap-7.70.tar.bz2
				   ```
				   압축 풀기를 완료한 후에 ls -ltr 로 파일 목록을 확인한다.
				   압축이 풀린 파일이 확인 될 것이다.
				   nmap 을 설치하기 위하여서는 
				   cd nmap-7.70 디렉 토리로 이동 후
				   ./configure (Server 를 체크 하는 명령어 ARM 인지 Intel 인지 ... )를 실행시켜 준다.
				   그 다음 make (software 를 compile 한다. 보통 GNU compiler gcc 라고 한다.)를 입력하여 준다.
				   그 다음 make install (file 들을 compile 하며 문서나 그 외다른 시스템.. scheduled tasks 들을 실행 한다)명령어를 입력하여 준다.

Day - 18 (18.md) - Remote Server 를 관리하는 관리자라면 Log 가 굉장히 중요한 요소이다.
				   하지만 disk 공간이 최대 적이다. 그래서 Log 는 굉장히 효율있게 사용해야 한다.
				   logrotate 어플리케이션은 Log 기한 설정 및 Log 상황을 항상 확인하여 주며 server 공간을 위하여 압축도 해주고 굉장히 유용하다.

				   Log 디렉토리는 /var/log 이다 예를 들어 apache2 Log 는 Subdirectory 로 /var/log/apache2 이다.
				   System Log 는 /var/log/syslog 에 기록 되며 압축 된 System 예전 Log 는 /var/log/syslog.1.gz 에 서 볼 수 있다.

				   Rotate 돌리는 방법은 /etc/cron.daily 에서 cron 설정을 한다. 해당 파일에서 logrotate 를 cron 설정을 해주면 된다.


Day - 19 (19.md) -  Linux 는 다양한 FileSystem 을 지원한다. 
					Linux 는 filename 과 실제 data 에 실제 외부 Layer 를 하나 더 가지고 있다 이것을 inode 라고 한다.
					이것은 숫자 벨류이며 가장 쉽게 2가지 방법으로 확인이 가능하다.
					
					ls 명령어에 -i 옵션을 사용한다.
					```
					ls -li /etc/hosts
					```
				   
					273 -rw-r--r-- 1 root root 221 Jan 31 08:37 /etc/hosts
					가 출력 된다.

					그 다음 방법은 stat 명령어를 사용한다
					```
					stat /etc/hosts
					```

					File: /etc/hosts
					Size: 221             Blocks: 8          IO Block: 4096   regular file
					Device: ca01h/51713d    Inode: 273         Links: 1
					Access: (0644/-rw-r--r--)  Uid: (    0/    root)   Gid: (    0/    root)
					Access: 2023-04-01 14:36:48.351552052 +0000
					Modify: 2023-01-31 08:37:12.000000000 +0000
					Change: 2023-01-31 15:52:25.965836000 +0000
					Birth: -

					가 출력 된다.

					모든 filename 에는 points 가 inode 에 있다. (실제 데이터를 가르키는)
					이 의미는 몇몇 파일 이름들은 같은 inode 를 가르킬 수 도 있다.
					
