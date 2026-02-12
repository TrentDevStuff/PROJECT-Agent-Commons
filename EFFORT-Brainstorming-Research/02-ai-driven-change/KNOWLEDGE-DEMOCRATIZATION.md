---
created: 2026-02-12T23:30:00Z
updated: 2026-02-12T23:30:00Z
type: research
parent_effort: EFFORT-Brainstorming-Research
research_area: 02-ai-driven-change
thread: "2.3"
status: draft
backlinks:
  - [[RESEARCH]]
  - [[SYNTHESIS]]
  - [[HUMAN-NATURE-TAXONOMY]]
---

# 2.3 Knowledge Democratization: The End of Expertise Scarcity

## Core Question

What happens when anyone can access expert-level capability through AI, and knowledge hoarding is no longer a competitive advantage?

## Why This Matters for Agent Commons

The Area 1 synthesis identified information hoarding as one of the most designable human-nature tendencies -- it responds to technology-assisted transparency. If AI fundamentally destroys the value of knowledge hoarding by making expert knowledge universally accessible, it removes one of the primary power bases of traditional organizations. This thread investigates whether that is actually happening, how far it goes, and what replaces knowledge as the scarce resource.

---

## 1. The End of Expertise Scarcity: Profession by Profession

### 1.1 Legal

**The disruption is real and accelerating.** Legal work is among the most AI-susceptible professions because a large fraction of it consists of pattern-matching across documents and precedent -- exactly what large language models excel at.

**Tools and adoption:**
- **Harvey AI** (founded 2022, backed by Sequoia and OpenAI): Built on GPT-4, used by Allen & Overy (one of the "Magic Circle" firms), PwC, and dozens of other major firms. Handles contract analysis, legal research, due diligence, and document drafting. Allen & Overy reported in 2024 that Harvey was being used by approximately 3,500 lawyers across 43 offices.
- **CoCounsel** (Thomson Reuters/Casetext): Integrated into Westlaw, the dominant legal research platform. Automates case research, document review, deposition preparation, and contract analysis. Thomson Reuters reported usage across thousands of law firms by mid-2024.
- **Luminance**: UK-based AI for contract review and negotiation. Used by over 600 organizations across 70+ countries. Claims to review contracts 10x faster than human lawyers.
- **Relativity (previously kCura)**: AI-powered e-discovery platform processing billions of documents. The e-discovery market was already heavily automated before generative AI.

**What AI can handle:**
- **Contract review and analysis**: Multiple studies suggest AI can handle 80-90% of standard contract review tasks. A 2023 LawGeex study found AI reviewed NDAs with 94% accuracy versus 85% for experienced lawyers, and 26 seconds versus 92 minutes per document.
- **Legal research**: Finding relevant cases, statutes, and precedent. AI dramatically reduces research time from hours to minutes. Stanford's CodeX center estimated in 2024 that AI could automate approximately 44% of the tasks performed by lawyers.
- **Document drafting**: Standard contracts, wills, corporate filings, and regulatory submissions. AI generates competent first drafts that lawyers then review.
- **Due diligence**: In M&A transactions, AI can review thousands of documents in hours rather than weeks. Deloitte estimated that AI-assisted due diligence reduced review time by 70-80%.
- **Prediction**: Lex Machina (now owned by LexisNexis) uses AI to predict case outcomes, judge behavior, and litigation timelines. Accuracy rates of 70-80% on case outcome prediction have been reported.

**What AI cannot handle (yet):**
- Courtroom advocacy, client counseling, and negotiations requiring emotional intelligence
- Novel legal theory and creative argumentation
- Ethical judgment in ambiguous situations
- Building relationships with judges, opposing counsel, and clients
- Strategic litigation decisions requiring understanding of client goals, risk tolerance, and political context

**Business model implications:**
The billable hour model is under existential pressure. If AI does in 26 seconds what took 92 minutes, clients will not pay for 92 minutes. Goldman Sachs estimated in 2023 that 44% of legal tasks could be automated. McKinsey's estimate was similar: 23% of lawyer working hours fully automatable, with another 23-30% significantly augmentable.

Big Law firms face the "associate problem": they have historically hired large classes of junior associates to do the document review, research, and drafting work that AI now handles. Several major firms quietly reduced their 2024 and 2025 associate classes. Latham & Watkins, Baker McKenzie, and Clifford Chance have all publicly discussed restructuring work allocation around AI tools.

The access-to-justice implications are profound. In the U.S., approximately 80% of civil legal needs of low-income Americans go unmet (Legal Services Corporation data). If AI can provide competent legal guidance for routine matters (tenant rights, simple wills, small claims, traffic violations), it could dramatically expand legal access. Companies like DoNotPay (the "robot lawyer") and LegalZoom have already moved in this direction, though with mixed quality results.

**Assessment:** Legal is experiencing genuine disruption, not hype. The profession will not disappear -- but the ratio of lawyers needed to work produced is declining sharply. The value shifts from knowing the law (which AI can do) to judgment, advocacy, relationships, and strategy (which AI cannot yet do). This is a clear case of knowledge democratization reducing the scarcity value of professional knowledge.

### 1.2 Medical

**AI diagnostic performance is matching or exceeding specialists in specific domains, but deployment lags capability.**

**Specific performance data:**
- **Medical imaging (radiology, dermatology, pathology)**: This is the area with the strongest evidence. A 2020 meta-analysis by Liu et al. in *The Lancet Digital Health* reviewed 82 studies and found that deep learning models performed equivalent to or better than healthcare professionals in diagnostic accuracy for medical imaging. A 2024 follow-up in *Nature Medicine* confirmed this finding across a broader range of imaging modalities.
- **Dermatology**: Esteva et al. (2017) in *Nature* demonstrated a CNN that classified skin cancer at the level of 21 board-certified dermatologists. Google Health subsequently showed AI matching specialist performance across 26 skin conditions (Liu et al., 2020). The challenge is that lab conditions differ from real-world deployment -- skin tone variation, image quality, and clinical context all degrade performance.
- **Ophthalmology**: Google/DeepMind's AI for detecting diabetic retinopathy (Gulshan et al., 2016, *JAMA*) achieved sensitivity and specificity comparable to or exceeding ophthalmologists. This was one of the first FDA-cleared autonomous AI diagnostic systems (IDx-DR, approved 2018). By 2024, autonomous AI retinal screening was deployed in over 900 primary care locations in the U.S.
- **Pathology**: Paige AI received FDA approval in 2021 for AI-assisted pathology. Studies show AI can identify cancer in tissue slides with accuracy rivaling senior pathologists, particularly for prostate and breast cancer. The system processes slides in seconds versus the 5-15 minutes a pathologist spends.
- **Radiology**: Multiple studies show AI matching radiologist performance for chest X-ray interpretation (Rajpurkar et al., 2018, CheXNet), mammography (McKinney et al., 2020, *Nature*), and CT interpretation. Google Health's mammography AI reduced false negatives by 9.4% and false positives by 5.7% compared to expert radiologists.

**AI beyond imaging:**
- **Diagnostic reasoning**: GPT-4 scored approximately 87% on USMLE Step 1 (2024 data), significantly above the passing threshold. Med-PaLM 2 (Google) achieved expert-level performance on medical question-answering benchmarks. However, real clinical reasoning involves uncertainty, incomplete information, and patient context that benchmarks do not capture.
- **Drug discovery**: DeepMind's AlphaFold (2020, 2022) predicted the 3D structures of virtually all known proteins -- a problem that had stymied biology for 50 years. This has accelerated drug target identification significantly. Insilico Medicine used AI to identify a novel drug target and design a candidate molecule for idiopathic pulmonary fibrosis in under 18 months -- a process that typically takes 4-5 years. The molecule entered Phase II clinical trials in 2023.
- **Clinical decision support**: Epic Systems (the dominant U.S. electronic health record vendor, covering ~40% of U.S. patient records) integrated AI-powered predictive tools for sepsis, patient deterioration, and readmission risk. Performance has been mixed -- the Epic sepsis model was criticized by Wong et al. (2021) for poor real-world performance despite strong training metrics, illustrating the lab-to-clinic gap.
- **Mental health**: Woebot (AI chatbot for CBT) showed preliminary efficacy in randomized controlled trials for depression and anxiety. However, the evidence base is still early, and concerns about AI handling crisis situations (suicidal ideation) remain serious. Wysa, another AI mental health tool, has been deployed in NHS England pilots.

**Healthcare access implications:**
The most transformative potential is in global health access. An estimated 4.5 billion people worldwide lack access to essential health services (WHO data). AI diagnostics deployed via smartphone could provide basic screening where no physicians exist. India's eSanjeevani telemedicine platform served over 150 million consultations by 2024. Ada Health, an AI symptom checker, has been used over 30 million times across 140+ countries.

The doctor shortage is real and worsening. The Association of American Medical Colleges (AAMC) projected a shortage of up to 124,000 physicians in the U.S. by 2034. AI cannot replace physicians wholesale, but it can extend their reach -- a single physician with AI tools can effectively screen and triage far more patients.

**Assessment:** Medical AI is demonstrating genuine expert-level capability in specific, bounded tasks (imaging interpretation, structured diagnosis, drug target identification). It is not replacing physicians -- it is augmenting them and potentially extending medical access to underserved populations. The knowledge democratization effect is real but constrained by regulation, liability concerns, and the irreducible importance of the human patient-physician relationship for complex care.

### 1.3 Financial

**The financial advisory disruption is mature -- robo-advisors are a decade old now. AI is moving into more complex financial reasoning.**

**Robo-advisor performance and adoption:**
- **Wealthfront** (founded 2008, AUM approximately $70 billion by 2024): Provides automated portfolio management, tax-loss harvesting, and financial planning for fees of 0.25% versus 1.0-1.5% for traditional advisors. Performance has broadly tracked market indices after fees, which means outperforming most actively managed portfolios (since ~85% of active managers underperform their benchmark over 10 years per S&P SPIVA data).
- **Betterment** (founded 2008, AUM approximately $45 billion by 2024): Similar offering to Wealthfront. Their 2023 performance report showed tax-loss harvesting adding 0.77% to after-tax returns on average.
- **Schwab Intelligent Portfolios**: Launched 2015, $80+ billion in AUM by 2024, zero advisory fee (makes money on cash sweeps). The large incumbents entering robo-advisory legitimized the category but also demonstrated that the technology is table-stakes, not a durable competitive advantage.
- **Vanguard Digital Advisor**: The world's largest asset manager entered with a hybrid human-AI model at 0.15-0.20% fees. This compressed margins across the entire advisory industry.

**Performance data:**
The SPIVA scorecard data (S&P Dow Jones Indices) consistently shows that over 10-year periods, approximately 85-90% of actively managed large-cap U.S. equity funds underperform the S&P 500. Robo-advisors that simply hold index funds in tax-efficient wrappers mechanically outperform most human-selected portfolios. This is not AI insight -- it is Bogle/Vanguard's passive investing thesis validated by decades of data. AI adds value primarily in tax optimization, rebalancing, and behavioral nudging (preventing panic selling).

**AI in more complex finance:**
- **Algorithmic trading**: High-frequency trading firms (Citadel Securities, Two Sigma, Renaissance Technologies, DE Shaw) have used quantitative and AI models for decades. Renaissance's Medallion Fund returned ~66% gross annualized from 1988-2018. But these returns are not democratized -- they accrue to the funds and their investors, not to the public.
- **Credit underwriting**: Upstart and other AI lenders use machine learning for credit decisions, approving borrowers that traditional FICO-based models would reject. Upstart reported 75% fewer defaults at the same approval rate, or 174% more approvals at the same default rate. This genuinely expands credit access.
- **Fraud detection**: JP Morgan's COiN platform processes 12,000 commercial credit agreements in seconds -- work that previously required 360,000 hours of lawyer and loan officer time annually.
- **Research analysis**: Bloomberg Terminal integrated AI (BloombergGPT, now part of Bloomberg's AI suite) for financial analysis, summarization, and natural-language querying of financial data. This gives individual investors and small firms access to analytical capabilities that previously required teams of analysts.

**Assessment:** Financial advice has been commoditized for standard wealth management. The value of human financial advisors has shifted from investment selection (which AI does better and cheaper) to behavioral coaching, complex financial planning (estate planning, tax strategy, business ownership transitions), and relationship/trust. AI is genuinely democratizing basic financial management -- the average person can now get competent portfolio management for near-zero cost.

### 1.4 Software Engineering

**This is the profession with the most rapid and measurable AI disruption.**

**Adoption and productivity data:**
- **GitHub Copilot** (launched 2021, generally available 2022): By early 2025, over 1.8 million paying subscribers and adopted by over 77,000 organizations (GitHub's reported figures). GitHub's internal research (Kalliamvakou et al., 2022) found that developers using Copilot completed tasks 55% faster than those without. A 2024 follow-up study found that AI-assisted developers accepted approximately 30-35% of code suggestions.
- **Percentage of code AI-generated**: GitHub's CEO Thomas Dohmke stated in 2024 that more than 46% of code across all programming languages on GitHub was AI-generated. Google reported internally that 25%+ of new code at Google was generated by AI by mid-2024. Amazon CEO Andy Jassy reported in 2024 that Amazon's internal AI coding tool (Amazon Q, based on CodeWhisperer) was generating code at scale, and that the migration of 30,000 production apps from Java 8 to Java 17 was completed in hours rather than the estimated years without AI.
- **Cursor, Replit, Codeium, Tabnine**: The AI coding assistant market has proliferated beyond GitHub Copilot. Cursor (AI-first code editor) reported rapid growth through 2024-2025. Replit's AI features were used by millions of developers. Competition is driving down prices and improving capabilities.

**Impact on developer demand:**
This is contested. Two opposing narratives:

*The displacement narrative*: Dropbox laid off 500 employees (16% of workforce) in late 2023, with CEO Drew Houston explicitly citing AI as the reason. Multiple tech companies cited AI efficiency in 2023-2024 layoff announcements. Some software development agencies reported 30-50% headcount reductions due to AI-assisted productivity. Devin (Cognition Labs, 2024) demonstrated an "AI software engineer" capable of handling end-to-end coding tasks autonomously, though with significant limitations.

*The augmentation narrative*: Stack Overflow's 2024 developer survey showed that developers with AI tools reported higher productivity but also reported that demand for their work increased -- AI made software cheaper to produce, so more software was demanded (Jevons paradox). GitHub's data showed that total code volume on the platform continued to increase alongside AI adoption, suggesting AI was expanding the total pie rather than just replacing human effort.

**Impact on junior developers:**
This is the most concerning area. Junior developer roles traditionally involved writing boilerplate code, fixing simple bugs, and learning through doing repetitive work. AI handles these tasks efficiently. Multiple tech leaders (including Satya Nadella and Jensen Huang) have publicly discussed the changing nature of entry-level software work.

However, the counterargument is that AI tools create new entry points. Someone with no programming background can now build functional software using AI assistance, potentially democratizing software creation far beyond the traditional developer population. The "prompt engineer" and "AI-assisted developer" roles are new categories that did not exist before.

**Assessment:** Software engineering is the canary in the coal mine for knowledge work disruption. AI is genuinely writing a large and growing percentage of production code. The profession is not disappearing, but it is transforming -- from writing code to directing and reviewing AI-generated code, architectural decisions, and system design. The ratio of developers needed to output produced is declining. Junior developers are most affected; senior developers with architectural judgment and system understanding are currently least affected.

### 1.5 Education

**AI tutoring is showing genuine promise but is not yet matching the best human tutors.**

**Key developments and research:**
- **Khan Academy + Khanmigo** (GPT-4 powered): Launched 2023 as an AI tutor within Khan Academy's platform. Khanmigo uses a Socratic tutoring approach -- asking guiding questions rather than giving answers directly. Khan Academy reported serving millions of students with AI tutoring by 2024. Pilot studies showed promising engagement metrics, but rigorous RCT data on learning outcomes was still emerging as of early 2025.
- **Duolingo Max** (GPT-4 powered): Added AI conversation practice and mistake explanation features. Duolingo reported that users of AI features showed higher engagement and retention. However, language acquisition research suggests that AI conversation partners still lack the responsiveness and cultural context of human interlocutors for developing true fluency.
- **Google's LearnLM**: Announced 2024 as an AI model specifically fine-tuned for education. Google partnered with multiple universities to develop AI-powered learning tools.

**The "2-sigma problem" (Bloom, 1984):**
Benjamin Bloom demonstrated that one-on-one human tutoring improved student performance by two standard deviations (approximately from the 50th to the 98th percentile). This is the benchmark. The problem has always been scalability -- one-on-one tutoring is prohibitively expensive. AI tutoring could theoretically provide this at scale, but current evidence suggests AI tutors achieve approximately 0.2-0.8 sigma improvement (VanLehn, 2011, for earlier intelligent tutoring systems; more recent generative AI studies are still emerging).

The gap between AI and human tutoring narrows in structured domains (mathematics, programming, foreign language grammar) and widens in unstructured domains (essay writing, creative thinking, philosophical reasoning, scientific inquiry). Human tutors adapt to emotional states, motivational needs, and learning styles in ways AI currently cannot.

**Education system implications:**
- Universities face the "credential vs. competence" challenge. If AI can teach the knowledge, what is the university selling? The answer is increasingly signaling, social networks, research, and the "college experience" -- none of which require traditional lectures.
- Bryan Caplan's *The Case Against Education* (2018) argues that 80% of education's value is signaling (showing employers you can complete a four-year program) rather than human capital (actually learning useful skills). If AI provides the human capital directly, Caplan's argument becomes more relevant -- but signaling may persist because employers still need screening mechanisms.
- Emerging models: micro-credentials (Coursera certificates, Google Career Certificates), competency-based degrees (Western Governors University), portfolio-based assessment (Lambda School/BloomTech model, despite its struggles), and AI-verified skill assessment.

**Assessment:** AI tutoring is genuinely expanding educational access, particularly in structured domains. It is not yet matching the best human tutors in complex, adaptive, emotionally-responsive instruction. The larger disruption is to the educational system's structure -- the unbundling of teaching, credentialing, research, and socialization that universities currently bundle together.

### 1.6 Creative Fields

**The most contested domain. AI creative tools are powerful, prolific, and threatening to creative livelihoods.**

**Current state:**
- **Visual art**: Midjourney, DALL-E 3, Stable Diffusion, and Adobe Firefly can generate professional-quality images in seconds. Midjourney has over 16 million registered users. In 2022, an AI-generated image won the Colorado State Fair art competition (Jason Allen's "Theatre d'Opera Spatial" via Midjourney), sparking a national debate. Stock photography demand from traditional sources (Getty, Shutterstock) declined measurably after AI image generation became mainstream. Shutterstock reported declining contributor payouts in 2023-2024.
- **Music**: Suno and Udio can generate complete songs (lyrics, melody, arrangement, vocals) in seconds. Suno reached over 10 million users by 2024. The major labels (Universal, Sony, Warner) filed copyright lawsuits against Suno and Udio in 2024. Google's Lyria and Meta's MusicGen represent additional entrants. AI music quality improved from obviously synthetic to commercially competitive between 2023 and 2025.
- **Writing**: GPT-4, Claude, and Gemini produce competent prose across genres. Amazon reported in 2023 that AI-generated books were flooding the Kindle marketplace -- some generated entirely by AI, many using AI assistance. Freelance writing rates on platforms like Upwork declined 30-50% in categories where AI competence is highest (blog posts, product descriptions, social media content). Literary fiction and long-form narrative remain more resistant.
- **Video**: Runway Gen-2, Pika, and OpenAI's Sora demonstrated AI video generation ranging from short clips to minute-long scenes. As of early 2025, AI video was impressive for short-form content but not yet competitive with professional production for long-form or narrative video. The trajectory, however, is steep.

**Impact on creative professionals:**
The Concept Art Association published survey data in 2024 showing that 70% of concept artists reported reduced work opportunities due to AI. Illustrators, particularly those doing commercial work (book covers, advertising, web design), reported significant client migration to AI tools. The Authors Guild's 2023 survey found that author income had declined 42% from 2009 to 2023, with AI contributing to but not solely responsible for the decline.

However, new creative roles are emerging. "AI-assisted creativity" is becoming a discipline -- humans who are skilled at directing AI tools, curating outputs, and combining AI capabilities with human vision are producing work that neither pure AI nor unaided humans could create alone.

**Assessment:** AI is rapidly commoditizing the execution layer of creative work. Stock illustration, generic content writing, background music, and template-based design are being automated. High-end creative work (distinctive voice, emotional resonance, cultural commentary, original vision) remains human territory but the boundary is shifting. The economic impact on mid-tier creative professionals is already severe.

### 1.7 Consulting and Strategy

**The most interesting case because consulting sells knowledge + judgment + trust + brand.**

**What AI can handle:**
- **Data analysis and insight generation**: McKinsey, BCG, and Bain have all deployed internal AI tools for market sizing, competitive analysis, benchmarking, and data synthesis. McKinsey's Lilli (internal AI knowledge tool) reportedly indexes the firm's entire knowledge base. BCG's in-house AI tools are used across client engagements.
- **Frameworks and best practices**: AI can apply Porter's Five Forces, SWOT analysis, value chain analysis, and other standard consulting frameworks as well as a first-year analyst. BCG published research (Dell'Acqua et al., 2023, Harvard Business School) showing that consultants using GPT-4 performed 25% faster and produced 40% higher quality output on tasks "inside the frontier" (well-defined analytical tasks).
- **Report writing and slide creation**: A significant portion of junior consultant work involves creating PowerPoint decks and written analyses from raw data. AI accelerates this dramatically.

**What AI cannot handle (the Dell'Acqua finding):**
The same Harvard/BCG study found a critical caveat: on tasks "outside the frontier" (requiring creative insight, judgment about ambiguous data, or integration of novel information), consultants who relied on AI performed *worse* than those who worked without it. The AI was confidently wrong, and consultants failed to catch the errors because they trusted the tool. This is the most important finding for the consulting industry: AI makes the routine brilliant and the novel dangerous.

**What remains human:**
- **Client relationships and trust**: CEOs hire McKinsey partly for the analysis but significantly for the brand credibility ("McKinsey recommended it" provides career insurance), the personal relationship with the engagement partner, and the trust built over years of working together.
- **Political navigation**: Understanding organizational dynamics, stakeholder interests, and the unspoken constraints on what recommendations will actually be implemented. This is judgment about human nature that AI does not yet possess.
- **Implementation support**: Helping organizations actually change -- which requires understanding psychology, organizational culture, and resistance dynamics.
- **Novel strategy**: Identifying opportunities that no one has seen before, synthesizing weak signals from disparate domains, and making creative leaps. This is the "outside the frontier" work where AI currently hurts more than helps.

**Assessment:** Consulting will be transformed but not eliminated. The analytical and framework-application layer (which employs most junior consultants) is being automated. The relationship, judgment, and implementation layers remain human. The industry will likely shrink in headcount while maintaining or growing revenue -- a smaller number of more experienced consultants leveraging AI to deliver faster and cheaper.

---

## 2. Power Dynamics Shift: Where Does Power Move When Knowledge Is Free?

### 2.1 The Historical Context: Knowledge As Power

Francis Bacon's *ipsa scientia potestas est* ("knowledge itself is power," 1597) has been literally true throughout organized society. Every dominant institution has been built on knowledge asymmetry:

- **Priesthoods** monopolized literacy and scriptural interpretation
- **Guilds** controlled trade secrets and apprenticeship access
- **Professions** (law, medicine, engineering) use licensing to restrict knowledge application
- **Corporations** use trade secrets, proprietary processes, and information classification
- **Governments** use classification systems, intelligence agencies, and controlled disclosure
- **Academia** uses peer review, credentialing, and publication gatekeeping

The printing press, the internet, and open-source software each eroded knowledge monopolies. AI represents a qualitative escalation: not just making information available (the internet did that) but making the *application* of information accessible. You do not need to understand patent law to get a competent patent analysis -- you need an AI tool. This is the difference between access to a law library (internet) and access to a lawyer (AI).

### 2.2 Five Candidates for the New Power Base

If knowledge is no longer scarce, what becomes the scarce resource that confers power? Five candidates emerge:

**Candidate 1: Capital (Those Who Own AI Infrastructure)**

The argument: AI requires massive infrastructure -- compute clusters costing billions, training runs consuming megawatts, data centers spanning continents. As of 2024-2025, the AI infrastructure stack is dominated by a handful of companies: Nvidia (chips), Microsoft/Azure + AWS + Google Cloud (compute), and the frontier model labs (OpenAI, Anthropic, Google DeepMind, Meta AI). If AI becomes the foundation of all economic activity, controlling AI infrastructure is controlling the means of production.

The evidence: Nvidia's market capitalization exceeded $3 trillion in 2024, briefly making it the world's most valuable company. Microsoft invested $13 billion in OpenAI. Google, Amazon, and Meta each invested tens of billions in AI infrastructure in 2024 alone. The capital requirements for training frontier models are escalating: GPT-4 reportedly cost over $100 million to train; next-generation models are estimated at $1-10 billion.

The counter-evidence: Inference costs are plummeting. OpenAI reduced API costs by 97% between GPT-3 (2020) and GPT-4o (2024). Open-source models (Llama 3, Mistral, Qwen) are competitive with proprietary models for many tasks and can run on consumer hardware. The cost of *using* AI is dropping toward zero even as the cost of *building* frontier AI is escalating. This creates a split: capital concentrates at the infrastructure layer but democratizes at the application layer.

Assessment: Capital is *a* source of power in the AI era, but its power may be concentrated at the infrastructure layer rather than the application layer. This is analogous to how electricity generation is capital-intensive and concentrated, but the applications of electricity are widely distributed. If open-source AI and commoditized inference continue their trajectory, capital advantage in AI may narrow to a few infrastructure choke points rather than conferring general power.

**Candidate 2: Execution Speed (First-Mover Advantage)**

The argument: In a world where AI gives everyone similar analytical capability, the scarce resource is speed of execution. Whoever moves fastest captures the opportunity. This favors small, agile teams over large organizations burdened by approval processes, compliance overhead, and coordination costs.

The evidence: AI-native startups are demonstrating remarkable velocity. Midjourney was built by a team of 11 people and reached $200+ million in annual revenue. Harvey AI went from founding to deployment at a Magic Circle law firm in under two years. Cursor went from launch to widespread developer adoption in months. These timelines would be impossible in large organizations.

The counter-evidence: First-mover advantage is historically weak in many markets. MySpace preceded Facebook. AltaVista preceded Google. Being first matters less than being *right* -- getting the product, market fit, and execution correct. Speed without judgment produces fast failure.

Assessment: Execution speed is a genuine power shift, particularly from large to small organizations. But it is not a durable moat -- speed is a process advantage, not a structural one. Anyone can move fast. What matters is speed *plus* judgment.

**Candidate 3: Taste and Judgment (Curation Over Creation)**

The argument: When AI can generate infinite content, code, designs, analyses, and proposals, the bottleneck shifts from creation to curation. The person who can distinguish the excellent from the merely competent becomes more valuable than the person who can produce the competent. This is the "taste layer" argument.

The evidence: In creative fields, the most successful AI-augmented creators are those with strong aesthetic judgment who use AI as a tool rather than a replacement. In software engineering, the most valuable role is shifting from code-writing to architecture and code review -- deciding *what* to build and *whether* AI-generated code is correct. In business strategy, the Dell'Acqua/BCG finding that AI hurts performance on novel judgment tasks suggests that the ability to know *when not to trust AI* is itself a critical skill.

The historical precedent: Photography did not kill painting -- it freed painting from the obligation of representation and elevated it to expression (Impressionism, Abstract Expressionism). Recorded music did not kill live performance -- it made live performance the premium experience. Calculators did not make mathematical intuition less valuable -- they eliminated computational drudgery and elevated mathematical reasoning.

The counter-evidence: What if AI develops taste? Current AI models can already predict which images humans will find aesthetically pleasing (NIMA, Google's neural image assessment). If taste is learnable from data, it is automatable. The "taste is uniquely human" argument may be a comfortable assumption that does not survive contact with advancing AI capability.

Assessment: Taste and judgment are currently among the strongest candidates for the new power base. But this could be a temporary phenomenon -- a brief window where human judgment exceeds AI judgment before AI catches up. The deeper question is whether taste is a product of human embodied experience (emotions, mortality, physical sensation) that AI cannot replicate, or a learnable pattern that AI will eventually master.

**Candidate 4: Social Capital (Network, Trust, Relationships)**

The argument: AI can analyze, synthesize, and generate -- but it cannot *be trusted* in the way humans trust each other. Trust is built through shared experience, vulnerability, reputation, and time. In a world where AI handles information processing, the scarce resource is the human relationship that enables coordination, deal-making, and collective action.

The evidence: Venture capital runs on relationships, not information -- every VC has access to the same market data, but deal flow depends on who you know and who trusts you. Sales remains fundamentally relational despite decades of CRM software. Political power runs on coalition-building, not analysis. Even in the AI era, the most successful founders (Sam Altman, Jensen Huang, Mark Zuckerberg) derive power not just from their companies but from their personal networks and relationships.

The counter-evidence: Social capital has always been unequally distributed and correlated with existing privilege (class, education, geography, family). If social capital becomes the primary power base, it risks recreating or amplifying existing inequality -- the "old boys' network" becomes the permanent aristocracy.

Assessment: Social capital is a strong candidate but a troubling one from an equity perspective. It is resistant to AI automation but also resistant to democratization. The Agent Commons concept needs to grapple with this: if the system rewards relationship-building, it may systematically advantage those with existing social advantages.

**Candidate 5: Attention (In a World of Infinite Content)**

The argument: AI can generate infinite content -- text, images, music, video, analysis, proposals. Human attention is fixed (approximately 16 waking hours per day). Attention becomes the ultimate scarce resource. Whoever captures attention captures value.

The evidence: The attention economy is already dominant. Google, Meta, TikTok, and YouTube are attention-harvesting machines. As AI floods every content channel with competent material, the bar for capturing attention rises. This advantages those with existing attention (celebrities, established brands, incumbents with distribution) and those who can create content that breaks through the noise (authenticity, shock, novelty, emotional resonance).

The counter-evidence: The attention economy has been widely criticized for producing addictive, polarizing, and low-quality content optimized for engagement rather than value. If attention becomes the primary power base in an AI world, the result may be worse content, more manipulation, and greater polarization -- the social media pathology amplified.

Assessment: Attention is already scarce and will become scarcer as AI increases content supply. But attention as a power base produces dystopian incentives (optimize for engagement, not value). A well-designed system (like Agent Commons) should probably design against attention-as-power in favor of contribution-as-power.

### 2.3 Skill-Biased Technological Change: Historical Patterns

The concept of "skill-biased technological change" (SBTC) was developed by economists (Katz and Murphy, 1992; Autor, Levy, and Murnane, 2003) to explain why technology has historically increased the wage premium for skilled workers. The argument: technology complements high-skill work (making it more productive) while substituting for routine work (displacing it).

**The Autor framework (task-based approach):**
David Autor's influential framework (2003, 2015) distinguishes between:
- **Routine cognitive tasks** (data entry, bookkeeping, basic analysis): Highly automatable, declining employment
- **Routine manual tasks** (assembly, repetitive manufacturing): Automatable with robotics, declining employment
- **Non-routine cognitive/analytical tasks** (research, strategy, management): Complemented by technology, growing employment and wages
- **Non-routine manual tasks** (home care, plumbing, cooking): Resistant to automation, but low wage growth
- **Non-routine cognitive/interpersonal tasks** (leadership, negotiation, care): Most resistant, but variable wage growth

AI is disrupting this framework because generative AI is the first technology that automates non-routine cognitive tasks. Historically, technology automated routine work and complemented non-routine cognitive work. AI automates both. This is why the current disruption feels qualitatively different.

**Who benefits most from AI democratization?**
Early evidence suggests a "leveling up" effect: AI helps lower-skilled workers more than higher-skilled workers in relative terms. Brynjolfsson, Li, and Raymond (2023, NBER Working Paper) studied customer support agents using AI and found that AI tools improved performance by 14% on average, but the gains were concentrated among novice and low-skill workers (34% improvement) while high-skill workers saw little improvement (0-5%). This suggests AI is a genuine equalizer for task-level performance -- but whether this translates to economic equalization depends on how productivity gains are distributed (see Thread 2.4).

### 2.4 The Matthew Effect: Does AI Amplify Existing Advantages?

The "Matthew Effect" (Merton, 1968, named for the Gospel of Matthew: "For unto every one that hath shall be given") describes how initial advantages compound. In technology adoption, this manifests as: those who already have resources (capital, education, networks) adopt new technology first, capture early advantages, and use those advantages to capture more -- widening the gap.

**Evidence that AI amplifies inequality:**
- AI tool access correlates with income and education. Pew Research (2024) found that 43% of adults with a college degree had used ChatGPT, versus 18% of those with a high school degree or less. Usage was highest among those aged 18-29 with college education.
- AI companies are located in a handful of cities (San Francisco, Seattle, New York, London, Beijing). Talent concentration is extreme -- a few thousand AI researchers at a handful of companies are building systems that affect billions.
- Early AI adopters in business are capturing disproportionate productivity gains. The gap between AI-adopting and non-adopting firms is widening, not narrowing, according to McKinsey's 2024 Global Survey on AI.

**Evidence that AI reduces inequality:**
- The Brynjolfsson customer support study (above) shows AI helps lower-skilled workers more.
- AI translation tools are reducing language barriers. Google Translate serves over 500 million daily users in 130+ languages. While quality is imperfect, it represents a massive reduction in language-based information inequality.
- AI coding tools are enabling non-programmers to build software. The "citizen developer" movement powered by AI dramatically expands who can create digital tools.
- AI educational tools reach places traditional education cannot. Khan Academy serves learners in 190+ countries.

**Assessment:** The Matthew Effect is real and operating in AI adoption. But the technology itself has equalizing properties (helps lower-skilled more, reduces access barriers, scales to underserved populations). The net effect depends on policy, institutional design, and how gains are distributed -- which is precisely what the Agent Commons concept needs to address.

---

## 3. The Creativity Question

### 3.1 Does AI Commoditize Execution and Elevate Originality?

The optimistic framing: AI handles the execution (writing prose, generating images, composing music, writing code), freeing humans to focus on originality (what to create, why, and for whom). Just as the printing press commoditized the scribe's execution and elevated the author's originality, AI commoditizes the technician's execution and elevates the visionary's originality.

**Evidence supporting this view:**
- In software engineering, AI is shifting value from coding to architecture and product vision. The most successful AI-era software companies are distinguished by *what* they build, not by code quality (AI makes code quality table-stakes).
- In creative fields, the most successful AI-augmented artists are those with distinctive vision. Refik Anadol's AI art installations sell for millions because of his artistic vision, not because of the technical execution (which AI handles).
- In consulting, the Dell'Acqua study suggests that the value boundary is between "within the frontier" (routine analysis, where AI excels) and "outside the frontier" (novel judgment, where humans still add value).

### 3.2 What Remains Uniquely Human?

**Embodied experience:** AI does not feel pain, joy, loss, love, fear, or mortality. Art that resonates most deeply often comes from these experiences. Whether AI can produce art that *feels* as if it comes from these experiences (mimicking rather than experiencing them) is an open question. Current evidence suggests AI can produce technically impressive work that many people find emotionally engaging -- the "Chinese Room" debate in aesthetics.

**Intentionality and meaning-making:** Humans create art *for reasons* -- to process trauma, express identity, critique society, connect with others, explore existence. AI generates outputs that match patterns in training data. Whether this distinction matters to the audience (as opposed to the creator) is unclear -- if the listener finds the music moving, does it matter that the composer had no emotional intention?

**The taste layer:** The strongest argument for enduring human value is that AI generates options while humans curate and judge. In a world of infinite AI-generated possibilities, the ability to select, refine, and contextualize becomes the scarce skill. This is already visible in AI-assisted creative workflows: human-AI collaboration produces better results than either alone.

### 3.3 Historical Precedent: Photography and Painting

Photography (1839) was expected to make painting obsolete. Instead:
- It freed painting from its representational function, leading to Impressionism, Expressionism, Abstract art, and eventually conceptual art
- It became its own art form with its own aesthetic traditions
- Both painting and photography coexist, each having found its niche
- The most valued paintings are now *more* expensive than before photography, not less -- because painting's value shifted from representation (which photography commoditized) to expression and cultural significance (which photography cannot replace)

**Does AI follow this pattern?**
The analogy is encouraging but may be imperfect. Photography automated one specific function of painting (representation). AI automates a much broader range of creative functions -- composition, style, technique, and even aspects of emotional expression. The question is whether AI's creative range is broad enough to leave nothing for human creativity to retreat to.

**Counter-argument: What if AI creativity reaches parity?**
If AI achieves genuine creative parity -- producing work indistinguishable from human work across all dimensions including emotional resonance, cultural significance, and novelty -- then the photography analogy breaks down. In that scenario:
- The value of creative work shifts entirely to provenance ("made by a human" as premium, analogous to "handmade" in a machine-made world)
- Or creative work as a profession largely disappears, surviving only as a hobby and identity practice
- Or new creative frontiers emerge that require embodied human experience in ways we cannot currently predict

This is genuinely uncertain. The honest assessment is that we do not know whether AI creativity will plateau below human parity, reach parity, or exceed it. Current trajectory suggests rapid improvement but with persistent gaps in certain dimensions (emotional authenticity, cultural commentary, experiential grounding).

---

## 4. Access Inequality: Digital Divide 2.0

### 4.1 Will AI Democratize or Create a New Divide?

The "digital divide" was coined in the 1990s to describe unequal access to computers and the internet. AI creates a potential "AI divide" with additional dimensions beyond physical access.

**The three layers of the AI divide:**

**Layer 1: Infrastructure access (can you reach AI at all?)**
- Internet penetration: approximately 5.5 billion people online globally (ITU 2024 data), but with dramatic quality disparities. Sub-Saharan Africa has ~40% internet penetration, and much of that is low-bandwidth mobile.
- Compute access: Running local AI models requires hardware beyond what most people own. Cloud-based AI (ChatGPT, Claude) requires only a browser and internet, but premium tiers cost $20-200/month.
- The cost barrier is real but declining. ChatGPT Free provides GPT-4o access at no cost. Google's Gemini is free with a Google account. Meta's Llama models are open-source and can run on modest hardware. The trend is toward broad access at the basic tier, with performance advantages at the premium tier.

**Layer 2: AI literacy (can you use AI effectively?)**
- "Prompt engineering" has become a skill with demonstrable impact on output quality. The gap between a naive user and a skilled user of the same AI tool can be enormous -- the same model produces dramatically different results depending on how it is used.
- AI literacy correlates with existing education levels. Stanford's AI Index Report (2024) found that AI tool usage is highest among those with graduate education and lowest among those without high school completion.
- Age gap: younger users adopt AI tools faster but do not necessarily use them more effectively. Pew (2024) found that 18-29 year olds were 2-3x more likely to have used generative AI than those over 65.
- Organizational divide: companies with AI strategies outperform those without. McKinsey's 2024 survey found that "AI high performers" (top quartile of AI adoption) were 2.5x more likely to report revenue growth attributed to AI.

**Layer 3: AI agency (can you shape AI, not just use it?)**
- This is the deepest and least discussed layer. Those who can fine-tune models, build AI-powered tools, create custom agents, and shape AI development have qualitatively more power than those who are passive consumers of AI outputs.
- The developer/non-developer divide may be the most important new inequality. AI tool builders capture value; AI tool users capture some value; those who do not use AI at all are left behind.
- However, AI is lowering the barrier to tool-building. No-code AI platforms, natural language programming, and AI-assisted development are enabling non-programmers to build custom AI tools. This is a genuine counter-trend.

### 4.2 AI Literacy as the New Literacy

Historical parallels:
- **Textual literacy** (post-printing press): Those who could read had access to information others did not. It took centuries for universal literacy to become a norm, and the transition period produced enormous inequality between literate and illiterate populations.
- **Computer literacy** (1980s-2000s): Those who could use computers effectively had career advantages. This gap has largely closed in developed countries but remains significant globally.
- **AI literacy** (2020s-): The ability to effectively use AI tools -- knowing what to ask, how to evaluate outputs, when to trust and when to verify, how to integrate AI into workflows -- is emerging as a new literacy requirement.

The World Economic Forum's Future of Jobs Report (2024) identified AI and big data skills among the fastest-growing skills globally. LinkedIn's 2024 Workforce Report showed that job postings mentioning "AI" or "generative AI" skills increased by over 400% from 2022 to 2024.

### 4.3 Language Barriers

AI performance varies dramatically by language:
- English: Best performance across all AI systems (largest training data, most research, most benchmarks)
- Chinese, Spanish, French, German, Japanese, Korean: Good performance, supported by most major AI systems
- Hindi, Arabic, Portuguese, Russian: Moderate performance, improving
- African languages, indigenous languages, low-resource languages: Poor performance. Many of the world's 7,000+ languages have minimal AI support.

This creates a knowledge democratization paradox: AI is democratizing knowledge for English speakers while potentially widening the gap for speakers of under-resourced languages. Approximately 75% of internet content is in 10 languages, and AI training data reflects this distribution.

Efforts to address this include Meta's No Language Left Behind project (translation for 200+ languages), Google's 1000 Languages Initiative, and various open-source multilingual model efforts. Progress is real but insufficient -- most AI capability remains concentrated in English and a handful of other languages.

### 4.4 Previous Technology Waves and Inequality

**The internet (1990s-2000s):**
- Initially expected to democratize everything. Instead, created platform monopolies (Google, Amazon, Facebook) that captured most value.
- Produced the "network effects" concentration pattern: the platform with the most users attracts more users, creating winner-take-all markets.
- Reduced information inequality (free access to knowledge) while increasing economic inequality (tech industry wealth concentration).
- Net effect: globally positive (billions connected, massive information access) but domestically ambiguous (wage inequality increased in developed countries).

**Mobile (2010s):**
- Reached populations the internet missed. By 2024, mobile internet penetration exceeded desktop in most developing countries.
- M-Pesa (Kenya) demonstrated that mobile technology could leapfrog traditional infrastructure gaps.
- But mobile also enabled gig economy platforms (Uber, DoorDash, Instacart) that created a class of precarious workers with technology-enabled exploitation.
- Net effect: more inclusive than desktop internet but still captured disproportionately by platform owners.

**Social media (2010s-2020s):**
- Genuinely democratized voice and audience access. Anyone can publish to billions.
- But algorithmic curation concentrated attention on a few creators while most received none.
- Created attention inequality: a small number of creators capture vast audiences, most creators are invisible.
- Created information quality problems: misinformation spreads faster than truth (MIT study, Vosoughi et al., 2018, *Science*).

**Pattern:** Each technology wave has simultaneously reduced one form of inequality (access to information, access to audience, access to markets) while creating or amplifying others (economic concentration, attention inequality, digital labor exploitation). AI is following this pattern -- reducing knowledge inequality while potentially creating AI-literacy inequality, compute-access inequality, and AI-infrastructure-ownership inequality.

---

## 5. Education Implications

### 5.1 What Does Learning Mean When AI Can Teach Anyone Anything?

The educational system has historically served four functions:
1. **Knowledge transfer** (teaching facts and skills)
2. **Credentialing** (certifying competence)
3. **Socialization** (building networks, learning social norms)
4. **Research** (advancing human knowledge)

AI disrupts primarily function 1 and partially function 2. Functions 3 and 4 are more resistant.

**Knowledge transfer:** If AI can teach anyone any subject at any time, personalized to their level and learning style, the lecture model is obsolete. This is not hypothetical -- adaptive learning platforms have already demonstrated improvements over traditional instruction in some domains. The question is whether AI tutoring can replicate the motivational, relational, and mentorship aspects of human teaching.

**Credentialing:** If AI provides competence directly (you can perform the work because AI assists you), what is the credential for? Caplan's signaling model suggests credentials will persist as screening mechanisms even when they provide no human capital. But alternative credentialing is gaining traction:
- Google Career Certificates (launched 2020): 6-month programs accepted by 150+ employers as equivalent to a 4-year degree for specific roles
- Micro-credentials and digital badges: Credly issued over 50 million digital credentials by 2024
- Portfolio-based assessment: particularly in software engineering and design, GitHub profiles and portfolio websites increasingly substitute for degrees
- Competency-based education: Western Governors University (founded 1997, 130,000+ students by 2024) awards credit based on demonstrated competence rather than seat time

### 5.2 The Signaling vs. Human Capital Debate

Bryan Caplan's *The Case Against Education* (2018) argues that education's value is approximately 80% signaling and 20% human capital. His evidence:
- Sheepskin effects: completing a degree is disproportionately more valuable than completing all but the last year of a degree, suggesting the credential (sheepskin) matters more than the knowledge
- The value of education varies dramatically by field in ways inconsistent with human capital theory
- Many graduates work in fields unrelated to their degrees
- Self-taught experts earn less than credentialed ones with the same skills, suggesting the credential, not the knowledge, drives earnings

**Does AI validate Caplan's argument?**
If AI provides human capital directly (you can do the work because AI helps you), then the human capital component of education becomes less valuable. But the signaling component may persist or even increase -- employers need some way to screen candidates, and AI makes the underlying skills less differentiating, potentially making the credential more important as a screening mechanism.

Counter-argument: AI may also enable better direct assessment of competence. If an employer can have a candidate solve realistic problems with AI tools in a timed test, the credential becomes less necessary for screening. This would validate Caplan's critique *and* undermine his prediction that credentials persist -- because AI enables better signaling alternatives.

### 5.3 What Skills Matter in an AI World?

The skills that retain value are those that AI cannot replicate:

**Meta-learning:** The ability to learn how to learn -- to quickly acquire new skills as old ones are automated. In a world where specific knowledge is commoditized, learning velocity becomes the durable advantage.

**Judgment under uncertainty:** AI excels at pattern-matching in well-defined domains. Human judgment is still superior in ambiguous, novel, or morally complex situations. Tetlock's "superforecaster" research (2015, *Superforecasting*) shows that some humans are genuinely skilled at judgment under uncertainty, and this skill can be trained.

**Creativity and originality:** Not routine creativity (which AI can match) but genuine novelty -- seeing connections no one has seen before, asking questions no one has asked, combining domains in unprecedented ways.

**Emotional intelligence:** Understanding, responding to, and influencing human emotions. Goleman's work (1995, *Emotional Intelligence*) identified this as a distinct and trainable skill. AI can simulate empathy but cannot (yet) genuinely understand or reciprocate human emotional states.

**Ethical reasoning:** Making decisions in situations with genuine moral trade-offs, where values conflict and there is no "correct" answer derivable from data. AI can present ethical frameworks but cannot make ethical commitments.

**Collaboration and leadership:** Coordinating human effort, building teams, resolving conflicts, inspiring commitment. These are fundamentally interpersonal skills that require human presence, vulnerability, and trust.

---

## 6. Implications for Agent Commons

### 6.1 What Knowledge Democratization Means for Organizational Design

If AI truly democratizes expert knowledge, several implications follow for the Agent Commons concept:

**The case for small teams strengthens dramatically.** The primary argument for large organizations (from Coase) is that they reduce transaction costs by internalizing coordination. But the primary *mechanism* of that coordination was specialist knowledge embedded in organizational roles (the legal department, the finance department, the marketing department). If AI provides that specialist knowledge to anyone, the transaction cost advantage of large organizations shrinks. A team of 5 with AI can access legal, financial, marketing, engineering, and strategic expertise without hiring specialists. This validates the Forg concept.

**Information hoarding becomes futile.** The Area 1 synthesis identified information hoarding as "moderate-high" in designability. AI makes it the *most* designable tendency because the information itself is no longer scarce. When anyone can access expert-level analysis on any topic, hoarding information provides no advantage. This removes one of the most persistent sources of organizational dysfunction.

**Power shifts to judgment and taste.** If knowledge is commoditized, the Agent Commons needs to reward judgment, taste, and originality -- not knowledge. The value attribution system must distinguish between:
- Contribution of knowledge (low value, AI provides this)
- Contribution of judgment (medium-high value, still scarce)
- Contribution of original insight (highest value, genuinely scarce)
- Contribution of execution (variable, depends on whether AI can do the task)

**The credential problem.** If the Agent Commons rewards contribution rather than credentials, it aligns with the post-credential world that AI is creating. But it needs mechanisms to assess competence -- not through credentials (which AI makes less relevant) but through contribution history, peer review, and demonstrated capability.

### 6.2 The Remaining Scarcities

Even with full knowledge democratization, these remain scarce:
1. **Human attention** -- fixed at ~16 hours/day per person
2. **Trust** -- built through relationship and track record, not information
3. **Judgment** -- particularly under uncertainty and in novel situations
4. **Motivation and commitment** -- willingness to do the work, not just know how
5. **Physical presence** -- for tasks requiring embodied action
6. **Authentic human connection** -- for care, support, leadership
7. **Original vision** -- seeing possibilities that do not yet exist

A well-designed Agent Commons would build its value system around these scarcities rather than around knowledge or credential-based status.

### 6.3 Key Uncertainties

1. **Pace of AI capability improvement:** If AI develops taste, judgment, and creative parity with humans, the "taste layer" argument collapses and much of this analysis needs revision.
2. **Distribution of AI access:** If premium AI remains expensive and basic AI is mediocre, knowledge democratization is real for some and illusory for others.
3. **Regulatory response:** Professional licensing bodies (bar associations, medical boards) will resist AI encroachment. The outcome of these regulatory battles will shape how quickly knowledge democratization actually reaches consumers.
4. **Backlash and Luddism:** There may be cultural rejection of AI in some domains ("artisanal" and "human-made" as premium markers, analogous to the organic food movement).
5. **Black swan AI capabilities:** Unexpected AI breakthroughs could change the landscape faster than incremental trend analysis predicts.

---

## Key Sources

### AI in Professions
- LawGeex (2023). AI vs. Lawyers: Comparing Accuracy in NDA Review.
- Liu, X., et al. (2019). A comparison of deep learning performance against health-care professionals. *The Lancet Digital Health.*
- Esteva, A., et al. (2017). Dermatologist-level classification of skin cancer. *Nature.*
- Gulshan, V., et al. (2016). Development and validation of a deep learning algorithm for detection of diabetic retinopathy. *JAMA.*
- McKinney, S.M., et al. (2020). International evaluation of an AI system for breast cancer screening. *Nature.*
- Brynjolfsson, E., Li, D., & Raymond, L. (2023). Generative AI at Work. NBER Working Paper 31161.
- Dell'Acqua, F., et al. (2023). Navigating the Jagged Technological Frontier. Harvard Business School Working Paper.
- Kalliamvakou, E. (2022). Research: quantifying GitHub Copilot's impact on developer productivity and happiness. GitHub Blog.

### Knowledge and Power
- Bacon, F. (1597). *Meditationes Sacrae.*
- Katz, L. & Murphy, K. (1992). Changes in relative wages. *Quarterly Journal of Economics.*
- Autor, D., Levy, F., & Murnane, R. (2003). The skill content of recent technological change. *Quarterly Journal of Economics.*
- Autor, D. (2015). Why are there still so many jobs? *Journal of Economic Perspectives.*
- Merton, R.K. (1968). The Matthew Effect in science. *Science.*

### Creativity and AI
- Bloom, B. (1984). The 2-sigma problem. *Educational Researcher.*
- VanLehn, K. (2011). The relative effectiveness of human tutoring, intelligent tutoring systems, and other tutoring systems. *Educational Psychologist.*
- Caplan, B. (2018). *The Case Against Education.* Princeton University Press.
- Tetlock, P. & Gardner, D. (2015). *Superforecasting.* Crown.
- Goleman, D. (1995). *Emotional Intelligence.* Bantam.

### Digital Divide
- Pew Research Center (2024). Americans' use of ChatGPT and other AI tools.
- Stanford HAI (2024). AI Index Report.
- McKinsey & Company (2024). The State of AI in 2024.
- Vosoughi, S., Roy, D., & Aral, S. (2018). The spread of true and false news online. *Science.*
- World Economic Forum (2024). Future of Jobs Report.
