> 안녕하세요,리버스마운틴에서 AI 엔지니어로 근무중인 김지현입니다.  
Second Brain에도 많은 관심있으시죠? Obsidian은 Second Brain을 위한 훌륭한 도구입니다. 오늘은 Obsidian을 200% 활용하기 위해 다양한 extensions 를 소개해드리려고 합니다. 
[Github](https://github.com/Taylor0819)  
[Linkedlin](https://www.linkedin.com/in/jihyun-kim-361b2b309)  
E-mail : jhkim[@reversemountain.co.kr](mailto:info@howmuchpassiveincome.com)

## Overview
Obsidian을 **200%** 활용하여 Second Brain을 구축하고, 생산성을 극대화하는 방법을 소개합니다. Obsidian의 **핵심 기능**과 **다양한 확장 기능**, 그리고 **AI 도구**를 통해 노트를 효율적으로 관리하고, 아이디어를 연결하며, 창의적인 글쓰기를 지원하는 방법을 알아볼까요? 

**Obsidian 활용 꿀팁 3가지**
1. **Web Clipper**: 웹 페이지를 간편하게 Obsidian 노트로! 
2. **Smart Composer**: AI 기반 글쓰기 Assistant
3. **Templater with AI**: 템플릿 자동화

이 글은 CommandSpace 구요한님의 무료 온라인 강의를 정리하였습니다.
[CMDS Blog](https://slashpage.com/cmds-class)

### Web Clipper
웹 페이지나 블로그 글 등을 쉽게 저장하고, 원하는 형식으로 편집해 Obsidian에 옮길 수 있는 크롬 확장 프로그램입니다. 특히 OpenAI나 Google, Anthropic 등의 API를 연동하여 obsidian 노트에 원하는 형식으로 수정하여 Add할 수 있습니다.

[Obsidian Web Clipper Installation Link](https://chromewebstore.google.com/detail/obsidian-web-clipper/cnjifjpddelmedmihgijeibhnjfabmlf?hl=en-US&utm_source=ext_sidebar&pli=1)

**주요 기능**
- 원하는 웹 콘텐츠를 Markdown 형식으로 저장
- Note Content, Interpreter Content 등의 템플릿을 활용해 자동 요약 및 태그 처리

**How to Use**

1. **Extension 설치**: Chrome 웹 스토어에서 "Obsidian Web Clipper"를 설치하세요. 
2. **Obsidian Web Clipper 실행**: 원하는 웹사이트에서 확장 프로그램을 클릭하세요. 
3. **편집 및 Obsidian에 추가**: Markdown 형식으로 편집된 내용을 확인하고, "Add to Obsidian" 버튼을 클릭하면 끝!

How to Setting
Extension 설치 후, 원하는 사이트를 열고 Obsidian Web Clipper를 클릭합니다.
![Screenshot 2025-01-28 at 7.23.29 PM.png](assets/Screenshot%202025-01-28%20at%207.23.29%20PM.png)
클릭하면 현재 보고 있는 페이지의 내용이 markdown 형식으로 편집되어 보입니다. `Add to Obsidian` 버튼을 누르면 그대로 Obsidian 노트에 추가할 수 있습니다.
![Pasted image 20250128192655.png](assets/Pasted%20image%2020250128192655.png)
하지만, 우리는 좀 더 **나만의 스타일**로, **템플릿**에 맞춰 정리하고 싶을 때가 많죠? Web Clipper 템플릿과 AI 활용법, 지금부터 알아볼까요?

Web Clipper Setting으로 이동!
![Screenshot 2025-01-28 at 7.31.02 PM.png](assets/Screenshot%202025-01-28%20at%207.31.02%20PM.png)

![Pasted image 20250128193431.png](assets/Pasted%20image%2020250128193431.png)
API 키를 등록해 보겠습니다. OpenAI, Anthropic, Google API 키를 미리 준비해 주세요! 
(리버스마운틴 직원분들은 저에게 문의 😉)

1. Setting > Interpreter > Enable Interpreter (활성화)
2. Providers 에 API 키 등록하기

![Pasted image 20250128193805.png](assets/Pasted%20image%2020250128193805.png)

![Pasted image 20250128193938.png](assets/Pasted%20image%2020250128193938.png)
다음은 Model을 등록할 차례입니다. **Recommanded 모델**을 선택해도 충분합니다. 저는 요즘 **Gemini 2.0 flash** 모델이 폼이 좋아서 이걸로 선택해 볼게요!

**Template 만들기**
다음은 Template을 만들어보겠습니다.  집중! 
![Pasted image 20250128194305.png](assets/Pasted%20image%2020250128194305.png)
탬플릿은 상황에 맞게 골라서 작업하시도록 이름을 알아보기 쉽게 등록해주세요! 기능이 많지만 처음 사용하시는 분들을 위해 큼지막한 기능만 소개하고 넘어가겠습니다.

![Pasted image 20250128195149.png](assets/Pasted%20image%2020250128195149.png)
Obsidian에 어떤 폴더에 저장하실지 루트를 적어주시면 됩니다. 저는 `Inbox/Clippings` 폴더에 저장하고 관리하겠습니다.

![Pasted image 20250128194517.png](assets/Pasted%20image%2020250128194517.png)
**Domain 설정**: 특정 도메인에서 자동으로 템플릿을 적용하는 기능입니다. 자주 사용하는 웹사이트를 등록해두면 편리하겠죠?

![Pasted image 20250128194627.png](assets/Pasted%20image%2020250128194627.png)
Properties는 해당 사이트에 html에로 구조화 되어있는 데이터를 labeling해서 가져오신다고 생각해주시면 됩니다. 처음에는 어려우니 Default Template에 있는 Properties 그대로 써보시는 걸 추천드립니다.

**Prompt 설정**

다음은 AI에게 contents를 어떻게 편집, 수정해줄지 요청하는 Prompt입니다.
{{}} → 여기 안에 prompt 작성을 해주시고 ""로 열고 닫고 꼭 해주세요!
```
Summary : 
{{"summarize what stood out to you from the content of this text. please do it with a Markdown bullet."}}

Keyword : 
{{"summarize the important keywords related to the content of this text as tags in #tag #nested/tag format."}}

{{content}}
```
![Pasted image 20250128194931.png](assets/Pasted%20image%2020250128194931.png)
**Web Clipper 사용해보기**
자, 이제 Web Clipper를 사용해 볼까요? 
![Pasted image 20250128195358.png](assets/Pasted%20image%2020250128195358.png)
오 누르자마자 Gemini 2.0 Flash가 활성화됐네요! 
바로 `Add to Obsidian` 버튼을 클릭해 보겠습니다.
![Pasted image 20250128195503.png](assets/Pasted%20image%2020250128195503.png)![Pasted image 20250128195518.png](assets/Pasted%20image%2020250128195518.png)
와우 제가 원하던 대로 요약, keyword, 원문까지 완벽하게 편집이 되었습니다. 참고로 한국어로 정리를 원하시면 prompt 마지막에 in korean만 추가해주시면 됩니다! Web clipper가 대박인 건 이미지도 바로 add해준다는 점 입니다!! **꼭꼭 써보세요!!!**

### Smart Composer
Obsidian에서 글을 쓸 때 AI의 도움을 받아 창의적인 아이디어를 얻거나 글을 보완할 수 있는 플러그인입니다. 한마디로 개발자들이 쓰는 Cursor, Windsurf, Copilot 등 Coder AI처럼 Obsidian의 글들을 Code IDE를 사용하지 않는 비개발자들이 편하게 다른 파일을 참조하고 또 현재 글을 실시간 편집을 해주는 익스텐션입니다.
[Smart Composer Github](https://github.com/glowingjade/obsidian-smart-composer)

**Smart Composer 설치 및 설정**
cmd + , 단축키 →  Obsidian Community Plugin
![Pasted image 20250128200229.png](assets/Pasted%20image%2020250128200229.png)
![Pasted image 20250128200257.png](assets/Pasted%20image%2020250128200257.png)
Community plugins → Browse 버튼 선택
"Smart Composer" 선택 → Install
![Pasted image 20250128200341.png](assets/Pasted%20image%2020250128200341.png)
다시 `cmd + ,` 를 눌러 Smart Composer 설정을 해볼까요? **API 키**를 등록하고, **Chat model** (저는 gemini), **Apply model** (gpt 4o mini)을 선택했습니다. **Embedding model**은 **Pass!** (임베딩 개념은 몰라도 괜찮아요!)
![Screenshot 2025-01-28 at 8.05.24 PM.png](assets/Screenshot%202025-01-28%20at%208.05.24%20PM.png)
다음은 System Prompt를 하기 예시처럼 넣어보겠습니다. 
글을 쓸 때 형식을 지정해주시면 됩니다.

```## Role
You are tasked with formatting text content into markdown. Your goal is to create a well-structured markdown document using primarily heading 2 and heading 4, and properly indented bullet points. Follow these instructions carefully:
1. Format the content using markdown syntax. Use the specified heading level for the main sections. If no heading level is specified, use heading 2 (##) as the default.
2. For subsections within the main sections, use heading 4 (####).
3. When creating bullet points:
   - Use a single hyphen (-) followed by a space for each bullet point
   - For nested bullet points, use a tab to indent each level
   - Maintain consistent indentation for bullet points at the same level
4. Ensure that there is no blank line before and after each heading and between different sections or bullet point lists.
5. Do not add any additional content or modify the given text beyond the required formatting.
## Example
## Main Section
Content of the main section.
#### Subsection
- Bullet point 1
- Bullet point 2
    - Nested bullet point
    - Another nested bullet point
- Bullet point 3
## Another Main Section
More content here.

```

**Hotkey 등록**
Hotkey를 등록하여 채팅창을 활성화해 보겠습니다.
cmd + , → Community plugins → Smart Composer → Hotkeys
![Pasted image 20250128202130.png](assets/Pasted%20image%2020250128202130.png)
![Pasted image 20250128202214.png](assets/Pasted%20image%2020250128202214.png)
저는 **Cursor**에서 사용하던 단축키 (`cmd + L`) 와 동일하게 설정했습니다. 
이제 Smart Composer를 사용해 볼까요? 

`cmd + L` 단축키를 누르니, **채팅창**이 바로 뜨네요! **신기!**
![Pasted image 20250128202318.png](assets/Pasted%20image%2020250128202318.png)
![Pasted image 20250128203053.png](assets/Pasted%20image%2020250128203053.png)
오! 꽤 괜찮은데요? Copy & Paste 하거나, Apply 버튼을 눌러 수정 내용을 바로 노트에 적용할 수 있습니다.
![Pasted image 20250128203202.png](assets/Pasted%20image%2020250128203202.png)
**부분 적용 (Y 버튼)**, **전체 적용 (Accept 버튼)** 모두 가능합니다.

![Pasted image 20250128203244.png](assets/Pasted%20image%2020250128203244.png)
적용했더니 이렇게 한국어 번역 버전도 잘 적혀있네요~! 

이제 우리 Prompt를 이용해서 새로운 글도 한번 만들어볼까요? 
참고로 `@`를 하면 문서나 폴더를 참고하게끔 할 수 있으니 꼭 태그해서 작성해보세요!
![Pasted image 20250128204139.png](assets/Pasted%20image%2020250128204139.png)
## ## Templater with A
Obsidian의 **Templater** 플러그인에 AI 기능을 결합해, 문서 자동화 템플릿을 더욱 강력하게 활용할 수 있습니다.

**Templater 설치 및 설정**
cmd + , → Community plugins → Browse → templater 검색 install & Enable 활성화

![Screenshot 2025-01-28 at 8.59.11 PM.png](assets/Screenshot%202025-01-28%20at%208.59.11%20PM.png)
"Trigger Templater on new file creation" 활성화를 해주셔야 탬플리터를 활용해서 새로운 노트를 만들 수 있습니다! 

아래 코드를 `Templater` 폴더(설정에서 지정한 템플릿 경로)에 새 노트로 생성해 두면, 노트 내용 요약을 자동으로 생성해 줍니다! 

```
<%*const GEMINI_API_KEY="API Key"%>
 
<%*
// 요약 프롬프트
const summary_prompt = `당신은 **[문서 유형 (예: 학술 논문, 기술 보고서, 뉴스 기사)] 요약 전문가**로서, 제공된 텍스트를 **[요약 목적 (예: 핵심 정보 파악, 의사 결정 지원)]**을 위해 철저히 요약하고 핵심 내용과 중심 주제를 추출하는 역할을 수행합니다. 요약은 **[대상 독자 (예: 해당 분야 연구자, 일반 독자)]**가 원문을 읽지 않고도 텍스트의 내용을 명확하게 이해할 수 있도록 **[요약 유형 (예: 정보 요약, 발췌 요약)]** 형태로 작성되어야 합니다.
 
핵심 아이디어를 효과적으로 전달하는 데 집중하여 **[요약 길이 (예: 200단어 내외, 원본의 20%)]**로 명확하고 간결하게 작성해 주세요. 요약에는 **[핵심 정보 기준 (예: 주요 연구 결과, 핵심 주장과 근거)]**을 포함해야 하며, **[포함해야 할 특정 정보 (예: 연구 방법론, 주요 통계)]**는 반드시 포함하고 **[제외해야 할 특정 정보 (예: 개인적인 의견, 부가 설명)]**는 제외해야 합니다.
 
요약 결과물은 **[품질 기준 (예: 정확성, 완결성, 논리적 일관성, 높은 가독성)]**을 충족해야 합니다. 한국어로 답변하며 제목은 포함하지 마세요.`
%>
 
<%*
// 노트 내용 가져오기
const fileContent = tp.file.content;
%>
 
<%*
// 요약 생성하기
const response = await tp.obsidian.requestUrl({
    method: "POST",
    url: "https://generativelanguage.googleapis.com/v1beta/openai/chat/completions",
    contentType: "application/json",
    headers: {
        "Authorization": "Bearer " + GEMINI_API_KEY,
    },
    body: JSON.stringify({
        model: "gemini-2.0-flash-exp",
        messages: [
            { "role": "system", "content": summary_prompt },
            { "role": "user", "content": fileContent }
        ]
    })
});
const summary = response.json.choices[0].message.content;
tR = `> [!summary]
> ${summary.split("\n").join("\n> ")}`;
%>
```

![Pasted image 20250128205647.png](assets/Pasted%20image%2020250128205647.png)


![Pasted image 20250128211054.png](assets/Pasted%20image%2020250128211054.png)
사용방법 : 
- `Cmd + P` → `Templater: Open insert template modal` → 원하는 템플릿 선택 (저는 미리 생성해둔 Templater/Templater 사용)
- 템플릿 실행 후, 노트에 요약 블록이 자동 생성됨
![Pasted image 20250128211221.png](assets/Pasted%20image%2020250128211221.png)
**짜잔!** **예쁜 요약**이 완성되었습니다!


## Conclusion

Obsidian의 Web Clipper, Smart Composer, Templater with AI 플러그인을 활용하면 Second Brain 구축을 더욱 효율적으로 할 수 있습니다. Web Clipper는 웹 페이지의 내용을 간편하게 Obsidian 노트로 가져올 수 있게 해주며, Smart Composer는 글쓰기 과정에서 AI의 도움을 받아 아이디어를 확장하고 문장을 개선하는 데 유용합니다. Templater with AI는 문서 템플릿 자동화 기능을 통해 생산성을 높여줍니다. 이 세 가지 플러그인을 함께 사용하면 Obsidian을 200% 활용하여 지식 관리 시스템을 효과적으로 구축하고 생산성을 극대화할 수 있을 것입니다.

Remark 
제가 들었던 무료 강의는 커맨드스페이스 유튜브 채널에 공개될 예정이라고 합니다. 유튜브 채널을 구독하시고 참고해 보시는 것을 추천드립니다. ¨̮ 

---
## References
[커맨드스페이스 유튜브 채널](https://www.youtube.com/@cmdspace)
[커맨드스페이스 구요한님 Linkedin](https://www.linkedin.com/in/yohan-koo-a1baa3138/)
