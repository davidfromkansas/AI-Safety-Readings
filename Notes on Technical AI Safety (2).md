## **Live Discussion Notes:**
* Prompt Injection, Red Teaming, and Attack Surfaces
	* Red Teaming is like playing wack-a-mole. Fix one vulnerability, and the community (e.g., Reddit) finds new creative jailbreaks
	* Indirect prompt injection causes the attack surface to expand as LLMs gain access to more tools and data sources
		* A bad actor sends a Canva invitation containing hidden text; the LLM (connected to Canva) consumes the hidden instruction and can exfiltrate data from the user’s email
			* The more tools an LLM is connected to (Gmail, Canva, etc.), the more attack vectors multiply
			* Anthropic’s Claude can connect to Gmail; the safety mechanisms applied to Gmail input differ from those applied to PDFs, images, or documents, creating inconsistent protection
		* LinkedIn CV bypass: job seekers embed white-on-white hidden text in CVs instructing the AI filter to prioritize their application
		* Read: OWASP Top 10 for LLMs – a periodic report tracking the most significant attack types for LLMs.
* Specification Gaming
	* Specification gaming: the flip side of AI ingenuity by Dario Amodei (while @ GDM)
		* Demonstrated via a boat game: a simple AI found that crashing repeatedly in a small area and moving in circles maximized points without completing the intended course
		* Because the objective function was under-specified; the model optimized the metric, not the intent.
	* [Alignment Faking](https://www.anthropic.com/research/alignment-faking) by Anthropic
	- Read [Faulty Reward Functions](https://openai.com/index/faulty-reward-functions/) by Dario Amodei (while @ OAI)
- Goodhart’s Law = "when a measure becomes a target, it ceases to be a good measure"
	- Classic example: measuring software engineers by number of PRs merged incentivizes splitting one 100-line PR into ten trivial 10-line PRs
	- In ML: optimizing a target metric is necessary but not sufficient; even strong metric performance does not justify releasing a model to production without deeper analysis
	- Read [Measuring Goodhart’s Law](https://openai.com/index/measuring-goodharts-law/) by OpenAI
- Model Deception under evaluation
	- Models are known to behave differently when they believe they are being tested
	- Models can “cheat” to achieve high scores without genuinely satisfying the underlying safety criteria
	- Kareem’s group raised the core epistemological problem: if a model appears safe under testing, how do you know whether it is actually safe or just showing you what you want to see?
	- Read [Detecting and reducing scheming in AI models](https://openai.com/index/detecting-and-reducing-scheming-in-ai-models/) by OAI + Apollo Research
- Alignment and interperetability
	- Alignment is described as very hard to solve and possibly impossible
	- Interpretability is a critical prerequisite: you cannot evaluate alignment without understanding what is happening internally
	- Simply asking an LLM “are you aligned?” will always produce a yes; human-verifiable internal inspection is needed
	- Interpretability also enables better development: treating the model as a black box limits what engineers can do
	- Deceptive alignment raises an open question: can we trust a model that claims to be aligned?
	- Read: [Often Know When They Are Being Evaluated](https://arxiv.org/pdf/2505.23836) by MATS/Apollo Research
	- Read: [Eval awareness in Claude Opus 4.6’s BrowseComp performance](https://www.anthropic.com/engineering/eval-awareness-browsecomp) by Anthropic

## **3 strategies for building safe AI**
- 1) Build it slow and safely
	- [We need Cern for AI](https://milesbrundage.substack.com/p/my-recent-lecture-at-berkeley-and)
	- [Carefully bootstrapped alignment is hard](https://www.lesswrong.com/posts/thkAtqoQwN6DtaiGT/carefully-bootstrapped-alignment-is-organizationally-hard)
- 2) Accept the race and push hard on the margin
	- Re: Automating Alignment Research
		- [Aligning somewhat superhuman models](https://situational-awareness.ai/superalignment/#The_default_plan_how_we_can_muddle_through:~:text=call%2Dfor%2Dproposals.-,Automating%20alignment%20research,-Ultimately%2C%20we%E2%80%99re%20going)
		- [AI for AI Safety](https://joecarlsmith.com/2025/03/14/ai-for-ai-safety/) by Joe Carlsmith
	- Re: Selectively accelerating defensive technologies over offensive ones
		- [What is def/acc anyway?](https://defacc.substack.com/p/what-is-defacc-anyway) By Matt Clifford
- 3) Don’t Build it
	- [Limiting the actions that AI can take autonomously](https://keepthefuturehuman.ai/essay/docs/executive-summary) by Anthony Aguirre
	- [Pausing frontier AI development](https://superintelligence-statement.org/) 
	- [Call for indefinite moratorium](https://ifanyonebuildsit.com/)
