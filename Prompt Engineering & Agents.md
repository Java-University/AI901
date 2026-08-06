Here are the high-density study notes for the AI-901 exam, focused on prompt differentiation and AI agent evaluation configurations.
------------------------------
## 1. Prompt Engineering: System vs. User Prompts
The exam heavily tests your ability to choose the correct prompt type to modify an AI's behavior, safety, or inputs.
## System Prompts (The "Guardrails")

* Definition: Static, high-priority instructions that define the model's persona, operational rules, safety boundaries, and constraints. [1, 2, 3, 4, 5] 
* Key Characteristics:
* Set before the conversation starts.
   * Hidden from or unalterable by the end-user.
   * Hard to override by user inputs (resists jailbreaking). [6, 7, 8, 9, 10] 
* Exam Scenario Keywords: "Set corporate persona," "enforce a professional tone," "restrict responses to medical topics only," "never mention competitors."
* Example: {"role": "system", "content": "You are a helpful customer service bot. Do not answer questions outside of product returns."}

## User Prompts (The "Inputs")

* Definition: Dynamic inputs or queries submitted in real-time by the human operator or end-user. [11] 
* Key Characteristics:
* Varies completely with every chat turn.
   * Asks questions, requests tasks, or provides local context. [12, 13, 14] 
* Exam Scenario Keywords: "User query," "dynamic question," "chat history input."
* Example: {"role": "user", "content": "How do I return a broken toaster?"}

------------------------------
## 2. AI Agents: Foundational Architecture
An AI Agent goes beyond simple chat by combining an LLM with memory, planning, and action tools to complete multi-step autonomous workflows. [15, 16] 

* Persona/Instructions: Configured via the System Prompt to define what the agent is allowed to do. [17] 
* Tools: Plugins given to the agent to interact with the outside world.
* Code Interpreter: Runs calculations or visualizes data in an isolated sandbox.
   * File Search: Automatically searches documents (built-in RAG).
   * Function Calling: Connects the agent to your company's custom databases or APIs. [18, 19, 20, 21, 22] 

------------------------------
## 3. Configuring AI Agent Evaluators
To test if your prompts and agents are performing safely and accurately, you must use Evaluators in Azure AI Foundry. [23] 
## Types of Evaluators

   1. AI-Assisted Evaluators: Uses a high-performing "judge" model (like GPT-4) to grade your agent's outputs based on complex, subjective human-like metrics.
   2. Quality Metrics: Evaluates performance using traditional data math (e.g., matching ground-truth answers).
   3. Risk & Safety Metrics: Specifically scans and rates outputs for toxicity, self-harm, hate speech, or jailbreak vulnerability. [24, 25] 

## Core Evaluation Metrics to Know

* Groundedness: Measures how well the agent's response aligns only with the source context data provided (e.g., did it make things up or hallucinate?).
* Relevance: Measures how directly the agent's answer addresses the specific question asked by the user.
* Coherence: Evaluates the grammatical correctness, flow, and structural readability of the agent's text.
* Fluency: Assesses linguistic quality and natural phrasing. [26, 27, 28, 29, 30] 

## The Configuration Process

* Step 1: Define a Test Dataset containing sample user prompts, context documents, and expected ground-truth targets.
* Step 2: Select the target model or agent deployment you want to benchmark.
* Step 3: Choose your evaluators (e.g., checking for Groundedness and Relevance).
* Step 4: Run the evaluation batch to generate a standardized quality score (typically on a scale from 1 to 5) alongside detailed defect logs. [31] 

------------------------------
Would you like to try a mock practice quiz on differentiating system/user prompts and configuring evaluators, or do you want to review Azure Content Understanding?

[1] [https://blog.ehoneahobed.com](https://blog.ehoneahobed.com/system-prompts-and-guardrails-in-ai-models)
[2] [https://www.dsstream.com](https://www.dsstream.com/post/prompt-secrets-ai-agents-and-code)
[3] [https://medium.com](https://medium.com/devnavigator/ai-agent-skills-5-powerful-reasons-prompts-and-tools-alone-fall-short-60d480ba075e)
[4] [https://www.lyzr.ai](https://www.lyzr.ai/blog/what-is-prompt-engineering/)
[5] [https://www.projectpro.io](https://www.projectpro.io/article/context-engineering-in-ai/1152)
[6] [https://medium.com](https://medium.com/@the_manoj_desai/beyond-basics-contextual-role-prompting-that-actually-works-bd75a0c5086b)
[7] [https://ai.plainenglish.io](https://ai.plainenglish.io/the-prompt-engineering-guide-part-2-5d6b72cd9d81)
[8] [https://kgateway.dev](https://kgateway.dev/blog/ai-gateway-prompt-enrichment/)
[9] [https://www.rapidflowapps.com](https://www.rapidflowapps.com/rapidflow-ai/uipath-ai-agent-prompts-best-practices/)
[10] [https://evalics.com](https://evalics.com/blog/system-prompt-vs-user-prompt)
[11] [https://tetrate.io](https://tetrate.io/learn/ai/system-prompts-guide)
[12] [https://www.width.ai](https://www.width.ai/post/n8n-ai-agents-tutorial-master-system-user-prompts-2026)
[13] [https://www.linkedin.com](https://www.linkedin.com/pulse/understanding-system-prompts-vs-user-guide-effective-ai-wolzak-speqe)
[14] [https://www.llamaindex.ai](https://www.llamaindex.ai/blog/context-engineering-what-it-is-and-techniques-to-consider)
[15] [https://www.scaler.com](https://www.scaler.com/topics/what-is-agents-in-ai-complete-guide/)
[16] [https://medium.com](https://medium.com/@meisshaily/ai-agents-breakthroughs-02d9f1105ebb)
[17] [https://elevenlabs.io](https://elevenlabs.io/docs/eleven-agents/best-practices/prompting-guide)
[18] [https://ai.plainenglish.io](https://ai.plainenglish.io/breaking-down-ai-agents-layer-by-layer-without-hype-d40f37638dd6)
[19] [https://fme.safe.com](https://fme.safe.com/guides/ai-agent-architecture/ai-agent-tools/)
[20] [https://blog.n8n.io](https://blog.n8n.io/llm-agents/)
[21] [https://www.ibm.com](https://www.ibm.com/think/insights/top-ai-agent-frameworks)
[22] [https://medium.com](https://medium.com/@sathishkraju/10-concepts-that-will-make-agentic-ai-finally-click-for-you-fb40a08d4b65)
[23] [https://medium.com](https://medium.com/@adnanmasood/a-taxonomy-of-agentic-observability-for-large-scale-ai-deployments-a4b87574a4f5)
[24] [https://zapier.com](https://zapier.com/blog/improve-ai-agents/)
[25] [https://www.instagram.com](https://www.instagram.com/reel/DaiQmowji11/)
[26] [https://www.mypminterview.com](https://www.mypminterview.com/p/ai-and-machine-learning-concepts-3)
[27] [https://autessa.com](https://autessa.com/blog/evaluating-ai-agents-in-production/)
[28] [https://www.instagram.com](https://www.instagram.com/reel/DVgxzDSCdTQ/)
[29] [https://devcom.com](https://devcom.com/tech-blog/ai-agent-testing/)
[30] [https://qawerk.com](https://qawerk.com/blog/ai-agent-evaluation-metrics/)
[31] [https://orq.ai](https://orq.ai/platform/evaluation)
