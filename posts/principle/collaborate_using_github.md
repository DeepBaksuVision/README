# Github으로 협업하기

본 문서는 DeepBaksuVision Team이 GitHub을 이용하여 협업하는 방법에 대해서 기술합니다. 본 문서는 **프로젝트 구조 및 작업방식 개요**, **프로젝트를 달성하기 위한 개발 방법론**으로 구성됩니다.



## 1. 프로젝트 구조 및 작업방식의 개요

### 1.1 프로젝트 구조

프로젝트 저장소 구조는 아래 그림과 같이 Upstream Remote Repository / Personal Remote Repository / Personal Local Repository 로 구성됩니다. Upsream Remote Repository는 Github의 [DeepBaksuVision Team](https://github.com/DeepBaksuVision)에 있는 저장소 입니다. Personal Remote Repository는 Upstream Remote Repository를 Github의 Folk 기능을 이용하여 개인 Github으로 복제한 저장소를 말합니다. Personal Local Repository는 내 Github 계정의 저장소를 컴퓨터에 클론 받은 것을 말합니다. 



요약하면 그림에서 (A)는 공통 팀 저장소, (B)는 개인 원격 저장소, (C)는 개인 원격 저장소와 연결되어있는 지역 저장소(내 작업 컴퓨터의 소스코드)가 됩니다.



자세한 내용은 [우아한 형제 기술 블로그 "우린 Git-flow를 사용하고 있어요"](http://woowabros.github.io/experience/2017/10/30/baemin-mobile-git-branch-strategy.html)를 참조하시기 바랍니다.



![repository_structure](https://user-images.githubusercontent.com/13328380/65828567-2a7a1280-e2d7-11e9-9708-6fd272bc709d.png)

### 1.2 작업방식

#### 1.2.1 개발 방법론

##### 1.2.1.1 프로젝트 오너 / 스크럼 마스터 선정과 역활

작업 방식은 애자일을 따르며 아래 그림은 애자일 프로세스에 대해서 묘사합니다. 프로젝트가 시작하기 전에 팀원들은 프로젝트 오너 겸 스크럼 마스터를 선정합니다. 프로젝트 오너 겸 스크럼 마스터는 스프린트 계획 회의를 진행하며, 매 스프린트의 상황을 모니터링 하며 회의록을 작성합니다. 



##### 1.2.1.2 프로젝트 계획 회의

프로젝트가 시작하면 프로젝트 오너는 팀원들과 일정을 조율하여 프로젝트 계획 회의를 진행합니다. 프로젝트 계획 회의에서는 궁극적으로 나왔으면 하는 결과물과 결과물을 보여줄 데모 시연을 선정합니다. 또한 결과물이 나왔을 때 결과물이 성공적으로 나왔음을 측정할 수 있는 기준을 구체적으로 선정하여 결과물을 평가합니다. 결과물이 선정되었다면 그 결과물을 산출하는 과정에서 중간에 달성해야하는 중간 결과물을 선정합니다. 중간결과물은 예상되는 개발기간이 2\~4주 내외로 한 스프린트 기간 안에 달성될 수 있는 목표여야합니다. 만약 2\~4주를 초과할 것 같은 중간 결과물이라면 중간 결과물을 더 세분화합니다. 중간 결과물 또한 최종 결과물과 같이 데모 시연과 성공적으로 중간 결과가 나왔음을 측정할 수 있는 기준을 선정합니다. 중간 결과물은 매우 구체적이며 빈틈없이 선정되어야합니다. 만약 프로젝트 계획회의에 고려하지 못한 중간 결과물이 있다면 스프린트 도중에 놓친 중간결과물을 달성해야해서 일정관리가 어려워집니다.  프로젝트 오너는 이렇게 선정된 최종결과물에 대한 명세와 중간결과물 리스트를 Product Backlog에 정리합니다. 이로써 프로젝트 계획 회의는 마무리됩니다.



##### 1.2.1.3 스프린트 계획 회의

프로젝트 계획 회의가 마무리 되었다면 스프린트 계획 회의를 진행합니다. 스프린트란 짧은 한 사이클의 개발 주기르 이야기하며 스프린트의 한 사이클은 일반적으로 2주\~4주를 권장합니다. 스프린트 계획 회의란 한 사이클을 돌 때 어떠한 중간 결과물을 달성할지 계획하는 회의를 말합니다. 팀 멤버들은 Product Backlog를 확인하여 이번 스프린트에서 달성하고 싶은 중간결과물을 선택하여 자신의 업무에 할당합니다. 만약 스프린트 계획 회의 이전에 수행한 스프린트가 있다면 계획 회의를 진행하기 전에 코드 리뷰를 진행하고 스프린트 계획 회의를 진행합니다.

![agile_approach](https://user-images.githubusercontent.com/13328380/65828862-8abe8380-e2da-11e9-8853-3d520568f4af.gif)



##### 1.2.1.4 스프린트

이제 본격적으로 스프린트를 시작합니다. 스프린트 시작 전 각 업무 담당자들은 Upstream Remote Repository에 자신의 업무에 대한 Issue card를 발행합니다. 작업자들은 Issue card 번호 기반으로 브랜치를 분기하여 작업합니다(브랜치 분기에 대한 상세 내용은 추후 설명합니다). 이제 스프린트 기간 동안 작업자들은 해당 작업을 수행합니다. 작업자들은 작업 수행 시 항상 데모 시연을 염두하고 소스 코드를 작성해야합니다. 데모 시연 코드와 중간 결과물을 모두 달성했다면 이제 작업한 브랜치를 메인 브랜치에 병합할 준비를 합니다. 병합 작업은 Personal Remote Repository의 브랜치에서 Upsteram Remote Repository의 develop 브랜치로의 pull request를 말합니다. pull request 확인은 항상 모든 작업자들이 함께 해야하며 pull request를 확인하는 모든 작업자들은 다음 스프린트 이전에 해당 pull request에 대한 데모 확인 및 코드를 읽어 다음 스프린트에 있을 코드 리뷰를 준비합니다.



#### 1.2.2 브랜치 전략

내용 수정중...

#### 1.2.2.1 원격 저장소 Fork

공동으로 작업해올 저장소를 개인 저장소로 가져와야 합니다. fork의 경우 원격 저장소를 수정할 수 있습니다. 쉽게 설명드리면 프로젝트 저장소를 개인의 깃으로 가져오는 과정입니다. 이 과정을 거친 후에 로컬과 연결하는 작업을 진행할 수 있습니다. 프로젝트 저장소의 우측 상단부에 fork를 누른 후 개인 저장소로 복제해옵니다. 이를 공유 저장소라고 하겠습니다.

#### 1.2.2.2 깃 초기화 및 환경설정

공유할 저장소를 받아오기 위해서는 빈 디렉토리가 필요합니다. 새로운 폴더에 깃 저장소를 생성하고 개인저장소에서 공유저장소의 주소를 clone해옵니다. 
**반드시 clone or download에 있는 주소를 가져오셔야 합니다.*** 
또한 새로운 폴더와 프로젝트 저장소의 환경을 동일하게 하는 작업을 진행합니다.

순서는 다음과 같습니다.

1. 새로운 폴더를 만듭니다. 빈 폴더가 아니면 clone이 되지 않습니다.
2. 해당폴더에서 터미널로 **git init** 으로 저장소를 초기화 해줍니다.
3. 저장소를 만든 폴더에서 개인 저장소에 있는 공유 저장소를 가져옵니다. **git clone (clone에 있는 주소)** 으로 공유 저장소 정보를 가져옵니다.
4. 공유 저장소의 브랜치를 생성해줍니다. 보통 develop으로 이름을 지으며, 이는 프로젝트 저장소에서 풀리퀘를 할때 이름을 맞춰주셔야 실수로 merge하지 않기 위함입니다. **get add remote origin (공유 저장소 clone 주소)**
5. 프로젝트 저장소와 싱크를 맞추기 위해 upstream 브랜치를 추가합니다. 
   **git add remote origin (프로젝트 저장소 clone 주소)** 로 upstream 브렌치를 추가합니다.
6. **git remote -v** 명령어로 브랜치가 정상적으로 생성되었는지 확인해봅니다.
7. **git fetch upstream** 명령어로 프로젝트 저장소와 동일한 환경을 만들어줍니다. 이 과정을 생략하게되면 풀리퀘가 올라가도 정상적으로 등록할 수 없으니 필히 시행해주시기 바랍니다.

#### 1.2.2.3 파일 올리기 & commit 및 push

본인이 올릴 파일이나 폴더 디렉토리가 있을껍니다. 환경설정까지 진행한 폴더에 파일이나 폴더를 추가하고 이를 commit까지 하는 작업을 설명하겠습니다. commit은 되돌릴수 있으나, 작업을 간소화하기 위해 최대한 신중하게 해주는 편이 좋습니다. 실수했을 경우 환경설정부터 다시 다 해줘야 합니다.(commit을 취소했어도 git에서 새로운 파일을 인식하지 못하기 때문입니다.)

순서는 다음과 같습니다.

1. **git checkout -b develop** 명령어로 작업할 브랜치로 돌아와서 작업을 시행합니다. master 브랜치로 작업을 시행할 경우 **바로 merge가 될 수 있으니 주의해주시기 바랍니다**.
2. 환경설정이 완료된 폴더에 소스코드 파일이나 폴더를 복사/이동 해줍니다. 위에서 강조한대로 새로 업로드한 파일을 **한번더 검토** 해주시는 것이 좋습니다.
3. **git status** 명령어로 확인을 해봅니다. 새로운 (파일/폴더) 을(를) git이 감지합니다.
4. **git add (올릴 파일이나 폴더)** 으로 업로드할 준비를 합니다.
5. **git commit** 명령어로 어떤점이 변경되었는지 등에 대한 작업내용을 표기합니다. commit -m "변경된 내용" 으로 작업을 간소화 할 수 있으니 참고 바랍니다.
6. commit이 정상적으로 되었는지 확인하기 위해 **git status** 으로 확인을 합니다. 이상이 없으면 **git push origin develop** 으로 공유 저장소에 수정사항을 반영합니다.

#### 1.2.2.4 프로젝트 저장소에 pull request 작성하기.

공유 저장소에 push를 했으면 공유 저장소에 develop 브랜치에서 프로젝트 저장소의 develop으로 pull request를 보낼 수 있습니다. 

순서는 다음과 같습니다.

1. github.com으로 가셔서 본인의 공유 저장소로 접속합니다.
2. Compare & Pull request 버튼을 눌러 pull request 준비를 합니다.
3. Open a pull request 제목 밑에 프로젝트 저장소 브랜치와 공유 저장소의 브랜치가 보입니다. 두 브랜치를 develop으로 맞춰줍니다.
4. 제목과 내용을 기입하고 Create pull request를 눌러 작업을 마무리합니다.

### 1.1 프로젝트 시작

멤버들은 아래 절차를 따라 프로젝트 시작을 준비합니다.

1. Upstream Remote Repository를 생성
2. Upstream Remote Repository를 Personal Remote Repository로 Folk
3. Personal Remote Repository를 개인 컴퓨터에 Clone



### 1.2 프로젝트 작업 방식

작업 목록은 프로젝트 회의를 통해서 결정됩니다. 결정된 작업은 Personal Remote Repository와 Personal Local Repository에서 하는 것을 목적으로 합니다.







### 1.1 Folk DeepBaksuVision Repository    



## 1 Getting Start

### 





## Meeting

- 미팅을 마무리하기 전, `origin` repository를 `upstream` repository와 sync합니다.

​    

## Retrospective

스프린트를 종료하는 미팅에서는 `잘한 점` / `개선점`에 대한 내용에 대해서 회고합니다.

- 해당 스프린트의 task 스토리포인트에 대한 회고는 필수적으로 진행합니다.

​    

## Sprint

- sprint는 1주~2주를 기준으로 진행합니다.

  - sprint 기간은 1주, 2주 중 유동적으로 선택하여 진행합니다.
  - 미팅 요일은 수요일이며, 오프라인 미팅을 갖는 것을 원칙으로 합니다.

- sprint 관리는 Github의 project 보드를 적극적으로 활용합니다.

- sprint시 개인당 할당되는 task의 개수는 스토리 포인트에 기준하여 제한을 받습니다.

  - 스프린트 기간을 1주로 가정했을 경우, 실 작업일수는 6일로 산정합니다.
    - 미팅날짜 제외
  - 6일의 작업일수 중, 실효성이 있는 작업일수는 4일로 산정합니다.
    - 개인 일정 및 기타 이슈로 인해 작업을 수행할 수 없는 날짜 고려
  - 4일의 작업일수 중, 3일은 실제 task 수행이며 1일은 Pull Request를 검토하는 task로 산정됩니다.
  - 하루 작업시 사용할 수 있는 스토리 포인트는 3을 최대로 합니다.
    - 하나의 task가 9의 스토리포인트를 갖는다면, 해당 스프린트에서 개인의 수행해야할 task는 9점짜리 스토리포인트를 갖는 하나의 task로 제한됩니다.
    - 해당 스프린트를 초과하는 스토리 포인트의 경우에는 더 세분화하여 쪼개서 진행하는 방향으로 진행합니다.

  *스토리 포인트란 작업의 기본 단위로 상대적인 일의 크기(난이도)를 뜻합니다. 해당프로젝트에서는 스토리 포인트 산정을 [0~10]점 사이로 합니다. (0에 가까워질 수록 쉬움 / 10에 가까워질 수록 어려워짐)*

- 스프린트를 진행하면서 예측한 스토리포인트와 실제 작업시 느꼈던 스토리 포인트의 간극을 측정하여 `회고`하는 시간에 리포팅합니다.



## Project

- 미팅때 합의된 task는 Todo 컬럼에 할당합니다.
- 작업 도중 생기는 bug / hotfix는 해당 Hotfix & Bug & Dicussion 컬럼에 생성하고 issue를 생성합니다.
- 작업 도중 개선사항이나 도입했으면 좋겠는 아이디어 및 유틸리티등은 Discussion으로 라벨을 붙여 Hotfix & Bug & Discussion 칼럼에 생성하고 Issue를 생성합니다.
  - 이슈 생성시, `title(abstract), What`에 대한 내용을 상세히 적습니다.
    - 주기적인 미팅 혹은 해당 이슈가 홀딩된 경우, 추후 해당 내용의 문맥 흐름을 놓치는 경우를 방지하기 위함입니다.

​    

## Collaboration



### Repository Structure

- repository의 구성은 upstream / origin 으로 구성됩니다.
  - `upstream` : team repository를 의미합니다.
  - `origin` : 개인이 upstream repository를 `fork`한 repository를 의미합니다.
  - [다음글](<http://woowabros.github.io/experience/2017/10/30/baemin-mobile-git-branch-strategy.html> )을 참조하시면 좋습니다.

- 개인은 upstream repository를 `fork`하여 작업을 진행합니다.
- sprint에서 할당받은 task의 issue number를 이용하여 branch를 생성하여 작업을 진행합니다.
  - 이슈번호가 `#77`인 경우에는 `issue_77`이라는 branch를 origin에서 생성하여 작업
  - 각 branch에서 작업한 내용은 upstream 으로 PR합니다.
    - origin으로 merge를 금지합니다.
    - 예외적으로 Hotfix인 경우에는 hotfix 이슈카드를 프로젝트에 생성 후, origin으로 merge후 작업 및 hotfix PR를 동시에 진행합니다.

​    

### Pull Request

- Pull Request시, 한명의 리뷰어 검토를 필수로합니다.
  - 리뷰어에게 승인이 떨어지지 않으면 Merge를 금지합니다.


### Code Convention

- Coding Convention은 PEP8을 따릅니다.
  - Git hooks를 이용하여 commit시, Code Convention을 충족시키는 방향으로 제한합니다.
