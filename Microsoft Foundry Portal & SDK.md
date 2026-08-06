The Microsoft Azure AI Foundry portal and SDK make up 55–60% of the AI-901 exam. This section requires practical familiarity with the portal interface, basic Python SDK patterns, and model deployments. [1, 2] 
------------------------------
## 1. Portal Architecture: Hubs vs. Projects
The [Azure AI Foundry portal](https://learn.microsoft.com/en-us/credentials/certifications/resources/study-guides/ai-901) (ai.azure.com) uses a multi-tier governance structure: [1, 3, 4] 

* 
* Hub: The overarching organizational resource boundary. It connects directly to your Azure Subscription and Resource Group. Security policies, data connections, and corporate governance are configured at the Hub level. [3, 5, 6, 7] 
* Project: The workspace where developers actually build things. A Hub can contain multiple Projects. Projects inherit security/storage infrastructure from the Hub but allow separate teams to deploy models, test prompts, and manage independent AI assets. [8, 9, 10, 11, 12] 
* 

------------------------------
## 2. Model Catalog & Deployment Options
The Model Catalog contains over 1,800 models ranging from Azure OpenAI models (GPT-4o, GPT-4o-mini) to open-weight models (Llama, Mistral). [1, 8] 

* 
* Deployment Prerequisites: To deploy a model, your identity needs the Cognitive Services Contributor role or equivalent permissions, along with Azure Marketplace subscription rights. [13] 
* Key Parameters to Configure:
* Region: Where the physical host data center resides (crucial for data sovereignty).
   * Capacity: Token-per-minute limits or provisioned throughput.
   * Content Filter: Core to Responsible AI. Configures restrictions on four primary harm categories (Hate, Self-harm, Sexual, Violence) at various severity levels.
   * Prompt Shields: Extra defense layers to detect block jailbreak attacks and malicious indirect inputs. [1, 3, 14, 15, 16] 
* 

------------------------------
## 3. Prompt Management (Chat Roles)
When using the portal's Playground or programming against the API, you must recognize three definitive roles: [16] 

* 
* system: Pre-defined rules that explicitly dictate the AI’s persona, tone, safety guardrails, and behavioral boundaries.
* user: The raw text prompts submitted dynamically by human operators.
* assistant: The historical output messages generated previously by the model during the chat thread. [1, 16, 17] 
* 

------------------------------
## 4. Reading the Foundry Python SDK
You will not write Python, but you must be able to read and spot errors in a 10–20 line code snippet. Look for these core components: [1, 2] 

* 
* Client Initialization: Creating the primary connection object using a specific project connection string.
* Chat Completion Method: Passing a list of role/content dictionaries to the model.
* 

# Look for these exact patterns on the examfrom azure.ai.foundry import AIProjectClientfrom azure.identity import DefaultAzureCredential
# 1. Establish Authentication & Client Connectionclient = AIProjectClient.from_connection_string(
    conn_str="your-project-connection-string",
    credential=DefaultAzureCredential()  # Uses Entra ID / Managed Identity
)
# 2. Invoke Chat Completions using defined Rolesresponse = client.inference.chat_completion(
    model="deployment-name-not-base-model-name",  # MUST match your portal deployment name
    messages=[
        {"role": "system", "content": "You are a brief exam assistant."},
        {"role": "user", "content": "What is AI-901?"}
    ]
)
# 3. Reading the Result Output
print(response.choices[0].message.content)

------------------------------
## 5. Foundry Agent Service
The Foundry Agent Service enables multi-step, autonomous workflows using the Microsoft Agent Framework. [18, 19] 

* 
* Portal Flow: Create Agent → Attach specific Tools → Instantiate an isolated conversation Thread → Execute a Run → Enumerate and evaluate message arrays. [1, 16, 20] 
* Built-in Agent Tools to Know:
* File Search: Performs automated vector indexing/retrieval (RAG) across raw uploaded files.
   * Code Interpreter: Sandboxed runtime environment allowing the agent to write and execute custom Python scripts on the fly to solve mathematical or complex processing problems.
   * Function Calling: Allows developers to expose external REST APIs or local functions to the agent. [1, 16, 21, 22, 23] 
* 

------------------------------
## 6. Security & Identity Permissions

* 
* Authentication: Swapping static, exposed API keys for secure Microsoft Entra ID (Managed Identities) is an extreme priority for enterprise security questions. [14] 
* Principle of Least Privilege:
* Use Cognitive Services OpenAI User if an app only needs to execute chat inferences (cannot create or change resources).
   * Use Cognitive Services Contributor if an administrator or script needs to deploy models or alter project infrastructures. [13, 14, 16] 
* 

------------------------------
Would you like to try a mock practice quiz focusing strictly on these Foundry Portal & SDK workflows, or would you like to review Azure Content Understanding next?

[1] [https://mscertquiz.com](https://mscertquiz.com/blog/ai-901-study-guide)
[2] [https://crackcerts.com](https://crackcerts.com/exam-guide/ai-901)
[3] [https://www.youtube.com](https://www.youtube.com/watch?v=a-yuXz_uV30&vl=en)
[4] [https://itnext.io](https://itnext.io/inside-microsoft-foundry-toolbox-and-content-understanding-a-technical-deep-dive-678b888fa703)
[5] [https://www.qservicesit.com](https://www.qservicesit.com/azure-ai-foundry-aws-bedrock)
[6] [https://team400.ai](https://team400.ai/blog/2026-04-08-getting-started-azure-ai-foundry-guide)
[7] [https://medium.com](https://medium.com/data-science-collective/building-ai-agents-in-azure-with-ai-agents-sdk-and-ai-foundry-4dcf50386de5)
[8] [https://www.youtube.com](https://www.youtube.com/watch?v=Sq8Cq7RZM2o)
[9] [https://www.youtube.com](https://www.youtube.com/watch?v=BAMQN6Jc5PM)
[10] [https://www.chatprd.ai](https://www.chatprd.ai/how-i-ai/jj-englerts-guide-to-a-daily-operating-system-with-claude-cowork)
[11] [https://dev.to](https://dev.to/rajkumar218/azure-ai-foundry-intro-3bdh)
[12] [https://medium.com](https://medium.com/@aserdargun/microsoft-certified-azure-data-scientist-associate-part-2-743ceab1f7a6)
[13] [https://www.youtube.com](https://www.youtube.com/watch?v=Gon9HDkBGj8)
[14] [https://mscertquiz.com](https://mscertquiz.com/blog/ai-901-study-guide)
[15] [https://www.udemy.com](https://www.udemy.com/course/ai-901-exam-prep-microsoft-azure-ai-fundamentals/)
[16] [https://mscertquiz.com](https://mscertquiz.com/blog/how-to-pass-ai-901-first-try)
[17] [https://learn.microsoft.com](https://learn.microsoft.com/en-us/credentials/certifications/resources/study-guides/ai-901)
[18] [https://www.youtube.com](https://www.youtube.com/watch?v=_S1mNm8B5XI)
[19] [https://techcommunity.microsoft.com](https://techcommunity.microsoft.com/blog/azure-ai-foundry-blog/beyond-the-model-empower-your-ai-with-data-grounding-and-model-training/4478144)
[20] [https://jannikreinhard.com](https://jannikreinhard.com/microsoft-foundry-first-agent/)
[21] [https://medium.com](https://medium.com/@m_prasanth/semantic-kernel-vs-microsoft-365-agents-sdk-vs-azure-ai-foundry-6e60465a7a6c)
[22] [https://learn.microsoft.com](https://learn.microsoft.com/en-us/azure/foundry-classic/agents/how-to/tools-classic/code-interpreter)
[23] [https://learn.microsoft.com](https://learn.microsoft.com/en-us/azure/foundry/agents/how-to/tools/code-interpreter)
