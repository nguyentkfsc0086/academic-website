#computer_science
#llms
#biomedical
#health
Original document: https://drive.google.com/file/d/1JlzOqz0kaxncHHrpqS5UUoHPGQqz65nn/view



> [!Abstracrt] 
> Examine the application of LLMs in biomedicine and health like information retrieval, question answering, medical text summarization.
> Find a significant advance in text generation
> But LLMs haven't evoluted in the field of biomedical -> more risk (uncrorrected infor, privacy and legal,...)
> Give an overview for researcher

- This is a overall paper -> not deep into the field

> [!NOTE] Notes
> ### Overview
> - There is a few biomed specific have been developed with biomed data
> - Recent models can do vary task but need a lot of data for fine-tuning the model
> 	- More complexity to model development and deployment
> - Large decoder-only LMS can perform unseen task after less-shot prompting [[Opportunities and challenges for ChatGPT and large language models in biomedicine and health.pdf#page=2&selection=265,19,266,48&color=yellow| p.2]]
> - LLMs can generate unhealthy contents due the noise of the input data [[Opportunities and challenges for ChatGPT and large language models in biomedicine and health.pdf#page=2&selection=306,0,309,13&color=yellow| p.3]] -> important to make LLMs generate helpful content
> 	- There is a design that make LLMs generate non toxic content along with human feedback [[Opportunities and challenges for ChatGPT and large language models in biomedicine and health.pdf#page=2&selection=319,39,323,19&color=yellow|p.4]] -> Alignment tunning
> 
> - Fine tuning will become inefficient and costly when the size of the model increase 
> 	-> Prompt engineer can take advantage of the learning ability of LLMs
> 	-> Can tuning the model with nature language to return expected output + improve the performance [[Opportunities and challenges for ChatGPT and large language models in biomedicine and health.pdf#page=2&selection=331,42,345,52&color=yellow|p5]]
> 			- Check fig1
> - There is a branch called biomedical NLP
> 	-  Model tuning bu using style of US Medical Licnensing Exam -> evaluate the performance [[Opportunities and challenges for ChatGPT and large language models in biomedicine and health.pdf#page=2&selection=371,48,374,51&color=yellow | idk]] -> approach level of human expert in 6 months -> through different strategies
> 		- Pre training from scratch [[Opportunities and challenges for ChatGPT and large language models in biomedicine and health.pdf#page=3&selection=36,0,36,25&color=yellow|he]] -> create a special LM for biomed with initialized parameter from biomed data base
> 		- [[Opportunities and challenges for ChatGPT and large language models in biomedicine and health.pdf#page=3&selection=50,0,50,29&color=yellow|pre train from checkpoints]] check again
> 		- [[Opportunities and challenges for ChatGPT and large language models in biomedicine and health.pdf#page=3&selection=64,0,64,35&color=yellow| fine tuning with specific data]] used frequently to adapt with samller LMs for specific task
> 		- [[Opportunities and challenges for ChatGPT and large language models in biomedicine and health.pdf#page=3&selection=76,0,76,47&color=yellow|Fine tuning with another stategies]] like instruction tuning or RLHF fine-tuning
> 		- and a lot more
> Model can have some benefit if it trained by biomed data but it will be costly -> LMs will be larger nowadays
> 	- Applying the technique can reduce the cost
> 	- Applied in combination
>### Application of LLMs in Biomed and Health
>#### Information retrivial
>	- Can not use LLMs as search engine at the time of the paper because it make up wrong information
>	- LLMs is good at summary information, search engine like gg use AI to summarize the search result but not guarantee error free
>	- Can use LLMs to make better queries => better search result
>#### Question Answering
>	- Def: answer automatically given questions
>	- Used to assist decision making
>	- Use retrieval augmentation to reduce hallucination, still need a system for evaluation
>		- More than 1 way to reduce hallucination
>#### Text summarize
>	- Important application of NLP
>	- Significant application: 
>		- Radiology report summarize
>		- Clinical note summarization
>#### Information extraction
>	- Extract specific information from unstructure text into a structure format with 2 most common studies
>		- Name entity recognition: recognizing biological and clinical entities
>		- relation extraction: extract relation between entities between text
>#### Medical education
>	- Good area to development
>	- Already applied in Khan Academy, not related to health care tho
>	- Still need to dev
>#### Other applications
>	- Coreference resolutiion:
>		- finding all mentions that refer to the same entities in a text
>	- Text classification: 
>#### Limitation and risk
>	- Hellucination
>		- Product fake contents
>	- Fairness and bias
>		- LMs learn from historical data -> can lead to bias
>			- prof that ChatGPT have social bias in answer -> not health related
>	- Privacy
>		- Might leak personal information -> what can it do with biomed data
>	- Legal and ethical
>		- hihi
>	- Open source and close source LLMs
>		- Opend source:
>			- pros: easy to addapt into specific tasks
>			- cons: depend on community support
>		- Close source:
>			- cons: hard to customize
>			- pros: more dedicat support
>### Discussion and conclussion
>	- some branch of biomed llms already develop
>	- llms achieved new state of performance art such as QA
>	- promising 
>

> [!quote] Comments
> Prompt is a real job
> A lot of LLMs was made for Biomed tasks
> QA tasks is like another way to retrive information -> text summary of LLMs do a very good job
> OMG hallucination huhuhuhu
> Good idea retrive augmentation: use the advance of LLMs
> 

> What kind of data use to train the LLMs model?

> [!tip] New Terms
>  [[Scientific terms | Encoder]]
> [[Scientific terms| Decoder]]
> [[Scientific terms|Zero-shot prompting]]
> [[Scientific terms|Alignment tunning]]
> [[Scientific terms|instruction fine-tuning]]
> [[Scientific terms|Hallucination]]
> [[Scientific terms|Retrive augmentation]]

### Table/figure analysis

![[Screenshot 2025-08-22 at 8.40.51 PM.png]]
 ![[Screenshot 2025-08-22 at 8.58.18 PM.png]]
 Fig2: 
	 - X: Name of LLMs
	 - Y: Accuracy of the return information
![[Screenshot 2025-08-25 at 11.47.56 PM.png]]
Table 2:
- Compare the models in each task (test database)
	- Learning: the way ppl tuning the model -> give instruction for the model
	- The rest is the test database
- Numbers: The accuracy of informations