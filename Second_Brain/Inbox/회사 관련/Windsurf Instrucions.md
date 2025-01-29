### 채팅 맨처음 prompt 
Each time you are assigned a task, check the @Instructions.md file again before proceeding so you are performing the tasks accordingly.

### Instructions.md
```
# Application Development Instructions

## Required Actions for Every Cascade Session

### If there are changes to any of the mentioned markdown files (@cascade_tracking.md, @development_log.md, @project_status.md), open them and edit accordingly.

Update Cascade Tracking

- Open and read @cascade_tracking.md

- Add new entry for each cascade with:

- Feature/component being worked on

- Number of iterations

- Success/failure status

- Any blockers encountered

Update Development Log

- Record all major changes in @development_log.md

- Include new prompts used

- Update current status

- List next steps

Update Project Status

- Keep @project_status.md current

- Mark completed items

- Add new pending items

- Update progress percentages

If there are changes to any of the mentioned markdown files (@cascade_tracking.md, @development_log.md, @project_status.md), open them and edit accordingly.

## File Locations

@cascade_tracking.md - Tracks all cascade interactions

@development_log.md - Records development progress

@project_status.md - Current project status

/core folder/ - Main application code

## Important Requirements

- Always maintain educational content

- Focus on accessibility

- Follow brand guidelines

- Always specify the exact modifications made and provide a clear "before and after" - comparison at the end of each response.

- Response in "Korean"

- Ensure that only the portions of the code directly related to the user's requirements are modified. Do not remove or suggest modifications for unrelated code or functionality.

- Do not modify any commented-out sections of code. Leave all commented code unchanged.

## Note to Future Cascades

Please read this file at the start of each session and follow the instructions meticulously.

Each time you are assigned a task, check the @Instructions.md file again before proceeding so you are performing the tasks accordingly.

The user should include this file in their prompt by referencing:
```
이 instruction 바탕으로 파일 세개 생성하고 거기에 log 기록
`@cascade_tracking.md`, `@development_log.md`, `@project_status.md`
- cascade_tracking.md : cascade 추적 로그 
- ![[Pasted image 20241204154337.png]]
- development_log.md : 개발 주요 변경사항 로그 
- ![[Pasted image 20241204154305.png]]
- project_status.md : 프로젝트 상태 업데이트 , 진행상황체크 및 앞으로 해야할  todo list 작성 해줌 
- ![[Pasted image 20241204154235.png]]

주의 자동으로 작성하게끔 했으나, 로그기록 까먹을수도있어서 중요한 기능이 있으면 @Instructions.md 한번 더 태깅해서 읽게끔 해보세용 !

###  주요사항
- 한국어 대답 
- 주석 처리 해놓은 코드 수정하지말기
- 사용자 요구사항에 해당하는 코드만 수정하고 외의 코드는 지우거나 수정금지

그 외에 필요한 사항은 수정해서 커스터마이징 해보면 될거같아요! 

