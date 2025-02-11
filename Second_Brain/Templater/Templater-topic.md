<%_*
// OpenAI API 키 설정
const OPENAI_API_KEY=""_%>

<%_*
// 프롬프트 정의 - 토픽 생성을 위한 프롬프트
const topics_prompt = `You are an expert in generating an appropriate topics properties that will be used in Obsidian Note. Your mission is to generate one or more topics suitable for given content.
Your generated output must be comma-separated values.

### Example Output:

[[📚 214 Document Parser]], [[📖 200 AI & Data]], [[📚 601 Enterprise Outsourcing Projects]]

Here's a list of possible substitutions for topics.
You must use these topics listed below:

### Topics:
- [📖 100 연구](📖%20100%20연구.md)
	- [📚 101 RAG 연구](📚%20101%20RAG%20연구.md)
	- [📚 102 LLM 연구](📚%20102%20LLM%20연구.md)
	- [📚 103 AI 트렌드](📚%20103%20AI%20트렌드.md)
	- [📚 104 AI 활용 사례](📚%20104%20AI%20활용%20사례.md)
	- [📚 105 최신 논문](📚%20105%20최신%20논문.md)

- [📖 200 AI & 데이터](📖%20200%20AI%20&%20데이터.md)
	- [📚 201 Concepts](📚%20201%20Concepts.md)
	- [📚 202 Prompt](📚%20202%20Prompt.md)
	- [📚 203 Retriever](📚%20203%20Retriever.md)
	- [📚 204 Embedding](📚%20204%20Embedding.md)
	- [📚 205 LLM](📚%20205%20LLM.md)
	- [[📚 206 LocalModels / Ollama]]
	- [📚 207 Vector DB](📚%20207%20Vector%20DB.md)
	- [📚 208 Reranking](📚%20208%20Reranking.md)
	- [📚 209 Knowledge Graph](📚%20209%20Knowledge%20Graph.md)
	- [📚 210 Hybrid Search](📚%20210%20Hybrid%20Search.md)
	- [📚 211 Evaluation](📚%20211%20Evaluation.md)
	- [📚 212 HuggingFace](📚%20212%20HuggingFace.md)
	- [📚 213 Agent](📚%20213%20Agent.md)
	- [📚 214 문서파서](📚%20214%20문서파서.md)
	- [📚 220 Fine-Tuning](📚%20220%20Fine-Tuning.md)
	- [[📚 221 LangChain / LangGraph]]
	- [📚 222 vLLM](📚%20222%20vLLM.md)
	- [📚 230 데이터 분석](📚%20230%20데이터%20분석.md)
	- [📚 231 머신러닝](📚%20231%20머신러닝.md)
	- [📚 232 딥러닝 (pytorch)](📚%20232%20딥러닝%20(pytorch).md)
	- [📚 233 데이터 엔지니어링](📚%20233%20데이터%20엔지니어링.md)
	- [📚 250 AI 서비스 구축](📚%20250%20AI%20서비스%20구축.md)

- [📖 300 개발](📖%20300%20개발.md)
	- [📚 301 Python](📚%20301%20Python.md)
	- [📚 302 Web 개발](📚%20302%20Web%20개발.md)
	- [📚 303 AWS](📚%20303%20AWS.md)
	- [📚 304 Docker & Kubernetes](📚%20304%20Docker%20&%20Kubernetes.md)
	- [📚 305 시스템 설계](📚%20305%20시스템%20설계.md)
	- [📚 306 MLOps & 배포](📚%20306%20MLOps%20&%20배포.md)
	- [📚 307 Git](📚%20307%20Git.md)
	- [📚 308 ngrok](📚%20308%20ngrok.md)
	- [📚 309 FastAPI](📚%20309%20FastAPI.md)
	- [[📚 310 가상환경/패키지관리(PYPI, Poetry, UV)]]

- [📖 400 콘텐츠 & SNS](📖%20400%20콘텐츠%20&%20SNS.md)
	- [📚 401 YouTube 테디노트](📚%20401%20YouTube%20테디노트.md)
	- [[📚 402 SNS 운영]]

- [📖 500 프로젝트](📖%20500%20프로젝트.md)
	- [[📚 601 기업 외주 프로젝트]]
	- [[📚 602 사이드 프로젝트]]

- [📖 600 지식관리 & 생산성](📖%20600%20지식관리%20&%20생산성.md)
	- [📚 601 세컨드브레인](📚%20601%20세컨드브레인.md)
	- [📚 602 메모 & 노트](📚%20602%20메모%20&%20노트.md)
	- [📚 603 나의 생각 정리](📚%20603%20나의%20생각%20정리.md)
	- [📚 604 업무 자동화](📚%20604%20업무%20자동화.md)

- [📖 700 Personal & 성장](📖%20700%20Personal%20&%20성장.md)
	- [📚 701 커리어](📚%20701%20커리어.md)
	- [📚 702 네트워킹 & 커뮤니티](📚%20702%20네트워킹%20&%20커뮤니티.md)


####

Example Output:

[[📚 214 Document Parser]], [[📖 200 AI & Data]], [[📚 601 Enterprise Outsourcing Projects]]

####

[Note] Write your Final Answer in Korean. DO NOT narrate, just write the output without any markdown formatting of wrapping.
Generated topics must be related to the content. Otherwise, you will be penalized.
`
_%>
 
<%_*
// frontmatter의 topics 속성을 업데이트하는 함수
// @param file: 대상 파일 객체
// @param newTopics: 새로운 토픽 문자열 (쉼표로 구분된 값)
const processTopics = async (file, newTopics) => {
  await tp.app.fileManager.processFrontMatter(file, (frontmatter) => {
    // 쉼표로 구분된 토픽을 배열로 변환하고 각 항목의 앞뒤 공백 제거
    const topics = newTopics.split(',').map(topic => topic.trim());
    // frontmatter의 topics 속성 업데이트
    frontmatter.topics = topics.map(topic => `${topic}`);
  });
};
_%>

<%_*
// 현재 노트의 내용을 가져옵니다
const fileContent = tp.file.content;

// OpenAI API를 호출하여 토픽을 생성하는 함수
async function generateTopics(content) {
    try {
        const response = await tp.obsidian.requestUrl({
            method: "POST",
            url: "https://api.openai.com/v1/chat/completions",
            contentType: "application/json",
            headers: {
                "Authorization": `Bearer ${OPENAI_API_KEY}`,
            },
            body: JSON.stringify({
                model: "gpt-4o",
                messages: [
                    { "role": "system", "content": topics_prompt },
                    { "role": "user", "content": `Here is the content of the note:\n${content}` }
                ]
            })
        });
        
        return response.json.choices[0].message.content;
    } catch (error) {
        console.error('토픽 생성 중 오류 발생:', error);
        return '토픽 생성 실패';
    }
}

// 토픽을 생성하고 파일에 적용
const topics = await generateTopics(fileContent);
const file = tp.config.target_file;
await processTopics(file, topics);
_%>