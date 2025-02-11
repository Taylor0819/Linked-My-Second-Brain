---
index:
  - "[[🏷️ 개발]]"
  - "[🏷️ 개발 블로그](🏷️%20개발%20블로그.md)"
topics:
  - "[📚 307 Git](📚%20307%20Git.md)"
  - "[📚 302 Web 개발](📚%20302%20Web%20개발.md)"
---
> 리버스마운틴  AI 엔지니어 김지현입니다. 요즘 회사에서 프론트도 해보고있고 여러가지 git협업을 해보고있습니다. 깃을 활용한 꿀팁을 공유해보겠습니다 ¨̮ 
[Github](https://github.com/Taylor0819)  
[Linkedlin](https://www.linkedin.com/in/jihyun-kim-361b2b309)  
E-mail : jhkim[@reversemountain.co.kr](mailto:info@howmuchpassiveincome.com)

## Overview

## PR(Pull Request)란?
- PR(Pull Request)은 개발자가 자신의 브랜치에서 작업한 내용을 다른 브랜치에 병합(merge)하고자 할 때 먼저 검토할 수 있는 기능이다. 
- PR을 통해 코드 변경 내용을 다른 팀원들에게 알리고, 코드 리뷰와 피드백을 받을 수 있다. PR이 승인되면 해당 브랜치의 내용이 `**main**` 브랜치에 병합된다

## PR TEMPLATE 만들기

### pull_request_template.md 파일 생성

`pull_request_template.md`는 Base repository에 있어야 적용되며 대소문자를 가리지 않는다.
아래 중 한 곳에 생성하면 된다.
- `.github/pull_request_template.md`
![](Pasted%20image%2020250211195642.png)
직접 github에서 `Create new file` 을 선택해서 생성해도되고, 작업하던 Code IDE에서 작업하고 commit & push 해도 된다. 

## PR TEMPLATE (Creator Version)
Pull request를 생성하는 사람 기준으로 Template 생성

```
## #️⃣ Issue Number

  

ex) #이슈번호, #이슈번호

  

- 버그나거나 이슈생기면 이슈를 먼저 생성 → 버그 픽스 후 pr 날릴때 이슈 번호 태깅

- #하면 우리 github 레포에 있는 이슈, 디스커션 등의 넘버를 태깅할수있어요.

- conflict 나거나 꼬였을때 pr을 다시 오픈하는 경우에는 그 전 pr을 태깅해줘야함!

  

## 📝 요약(Summary)

  

- 변경 사항 및 관련 이슈에 대해 간단하게 작성해주세요. 어떻게보다 무엇을 왜 수정했는지 설명해주세요.

  

## 🛠️ PR 유형

  

어떤 변경 사항이 있나요?

  

- [ ] 새로운 기능 추가

- [ ] 버그 수정

- [ ] CSS 등 사용자 UI 디자인 변경

- [ ] 코드에 영향을 주지 않는 변경사항(오타 수정, 탭 사이즈 변경, 변수명 변경)

- [ ] 코드 리팩토링

- [ ] 주석 추가 및 수정

- [ ] 문서 수정

- [ ] 테스트 추가, 테스트 리팩토링

- [ ] 빌드 부분 혹은 패키지 매니저 수정

- [ ] 파일 혹은 폴더명 수정

- [ ] 파일 혹은 폴더 삭제

  

## 📸스크린샷 (선택)

  

## 💬 공유사항 to 리뷰어

  

- 리뷰어가 중점적으로 봐줬으면 좋겠는 부분이 있으면 적어주세요.

- 논의해야할 부분이 있다면 적어주세요.

- ex) 메서드 XXX의 이름을 더 잘 짓고 싶은데 혹시 좋은 명칭이 있을까요?

  

## ✅ PR Checklist

  

PR이 다음 요구 사항을 충족하는지 확인하세요.

  

- [ ] 커밋 메시지 컨벤션에 맞게 작성했습니다.

- [ ] 변경 사항에 대한 테스트를 했습니다.(버그 수정/기능에 대한 테스트).
```

## Peer Review TEMPLATE (Reviewer Version)
## ✅ 리뷰어 체크리스트
```markdown
- [ ] PR이 참조하는 이슈 번호가 올바르게 태깅되어 있는가?
- [ ] PR 요약 및 설명이 명확하고 충분한가?
- [ ] PR 유형(기능 추가, 버그 수정 등)이 변경 사항과 부합하는가?
- [ ] 코드 스타일 및 네이밍 컨벤션을 준수하고 있는가?
- [ ] 관련 테스트 코드가 추가되었거나 업데이트되었는가?
- [ ] UI/디자인 변경 사항(해당 시)이 명확하고 일관적인가?
- [ ] 문서 및 주석이 충분하며, 변경 사항을 반영하고 있는가?
- [ ] 의문점, 개선 사항, 추가 논의가 필요한 부분에 대해 명확한 피드백을 남겼는가?
- [ ] 코드 실행 시, Error 및 Conflict 는 없는가? 
{기타 Commet}
```


## Create Pull Request
![](Pasted%20image%2020250211200705.png)
오 제가 만든 파일이 자동으로 뜨네요! 

해당 pr 의 리뷰가 끝나면 아래와같이 리뷰와 함께 approve & merge 를 진행해주시면 됩니다. 
![](Pasted%20image%2020250211201214.png)


## References
[GitHub PR template 만들고 사용하기](https://mynamesieun.github.io/git/GitHub-PR-template-%EB%A7%8C%EB%93%A4%EA%B3%A0-%EC%82%AC%EC%9A%A9%ED%95%98%EA%B8%B0/)