---
name: env
description: 작업 환경 점검 (OS, 런타임, 패키지 설치 가능 여부, 인터넷, git, 자원). 사용자가 직접 부를 때만 쓴다.
---

현재 작업 환경을 점검해줘. 아래를 실행하고 결과를 표로 정리해.

1. OS와 위치: `uname -a`, `cat /etc/os-release`, `pwd`, `ls -la`
2. 런타임: `python3 --version`, `pip3 --version`, `node -v`, `npm -v`
3. 패키지 설치 가능 여부: 실제로 설치하지 말고 확인만 (`pip3 install --dry-run six`, `npm view lodash version` 등). `sudo -n true`로 sudo 가능 여부
4. 자원: `free -h`, `nproc`, `df -h .`
5. 인터넷: `curl -sI https://github.com | head -1`, `curl -sI https://pypi.org | head -1`. 샌드박스 때문에 막힌 것인지, 환경 자체가 막힌 것인지 구분해서 적어
6. git: `git --version`, `git rev-parse --is-inside-work-tree`. 저장소가 아니면 `git init`과 첫 커밋을 제안해
7. LLM API 키가 환경변수에 있는지: 값은 출력하지 말고 **존재 여부만** 확인

마지막에 이 **개발 환경**에서 쓸 수 있는 스택 후보를 정리해. 결과물이 실행될 **사용자 환경**은 이 점검으로 알 수 없으니 스택을 확정하지 말고, 업무 담당자에게 물을 질문(OS, 프로그램 설치 가능 여부, 인터넷, 브라우저, 배포 방법)을 함께 적어줘.
