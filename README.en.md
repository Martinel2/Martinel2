<a href="https://martinel2.github.io/en/?utm_source=github&utm_medium=referral&utm_campaign=profile&utm_content=banner-en"><img width="1584" height="396" alt="Go to Jaehyeong Kim's site" src="banner-en.png" /></a>

[한국어](README.md) | **English**

I build services that use AI to make people's lives better.

I'm an AI engineer who raised RAG evidence coverage from 66.25% to 91.25% and AI document-editing quality from 82.5% to 91.2%, designing evaluation, approval and rollback so AI does not answer from wrong evidence or change users' documents on its own. I weigh accuracy, cost and response time against each other, confirm the trade-off with an evaluation, and then choose the implementation that fits the service.

[About](https://martinel2.github.io/en/?utm_source=github&utm_medium=referral&utm_campaign=profile&utm_content=header-intro-en) | [Portfolio](https://martinel2.github.io/en/portfolio.html?utm_source=github&utm_medium=referral&utm_campaign=profile&utm_content=header-portfolio-en) | [Resume](https://martinel2.github.io/en/resume.html?utm_source=github&utm_medium=referral&utm_campaign=profile&utm_content=header-resume-en) | [Blog (Korean)](https://velog.io/@kkuldangi3/posts) | [LinkedIn](https://www.linkedin.com/in/%EC%9E%AC%ED%98%95-%EA%B9%80-b75920345/)

**Email**: kkuldangi2@gmail.com

## Highlights

- **[Improving RAG evidence selection: coverage 66.25% → 91.25%, evidence attached to unanswerable questions 20 → 0](https://martinel2.github.io/en/portfolio/fruition-jev-evidence.html?utm_source=github&utm_medium=referral&utm_campaign=profile&utm_content=exp-jev-en)**
  I thought wrong evidence makes the whole answer untrustworthy, so I replaced evidence selection with Jev. GPT cost about 2.5× more, and tuning search weights kept scores flat. Selection got much slower, so I tuned candidates and parallelism to cut median time from 9.090s to 1.137s.
- **[Designing the agent execution environment: user-defined skills behind approval, edit quality 82.5% → 91.2% (114 drafts)](https://martinel2.github.io/en/portfolio/fruition-agent.html?utm_source=github&utm_medium=referral&utm_campaign=profile&utm_content=exp-agent-en)**
  Users repeat different tasks, so I let them define their own Skills. I judged that users can't trust AI that changes documents freely, so code checks permissions and scope, and changes apply only after approval. Code checks missed omitted requests, so drafts get a semantic evaluation and one rewrite at most.
- **[Building data pipelines: PDF restoration rate 45.17% → 89.89%, drug conversion $200 estimated → $11.18 spent](https://martinel2.github.io/en/portfolio/fruition-document.html?utm_source=github&utm_medium=referral&utm_campaign=profile&utm_content=exp-pdf-en)**
  Broken tables and equations lose the figures answers rely on, so body text uses fast AnyDoc and table and equation regions are read separately. Converting each repeated sentence once with Batch API kept about 44,000 drug records within budget.

All figures come from internal evaluations.

## Skills

- **AI & Search:** LangChain, LangGraph, Spring AI, RAG, LangSmith, LLM Evaluation, LLM Guardrail
- **Backend:** Java, Spring Boot, Python
- **Data & Infra:** MySQL, PostgreSQL, Redis, Elasticsearch, Weaviate, Docker, Docker Compose, GitHub Actions, Kafka

## Projects

### Fruition | LLM Wiki-based AI workspace

[GitHub | AI repository](https://github.com/FruitionKR/Fruition-ai) | [Project overview](https://martinel2.github.io/en/portfolio/fruition.html?utm_source=github&utm_medium=referral&utm_campaign=profile&utm_content=fruition-detail-en)

2026.04 — Present | AI SW Maestro, 17th cohort | Deployed on AWS EKS, in QA | Team project (3 + designer) | **AI lead**

- **How it started:** a teammate's pain point with managing documents, refined through design thinking: saved documents could not be found when needed.
- **Team:** me (all AI), 1 backend (Spring backend), 1 frontend & DevOps (frontend, MSA deployment on AWS), external designer, 3 mentors

**What I built**

- **[Evidence selection for RAG](https://martinel2.github.io/en/portfolio/fruition-jev-evidence.html?utm_source=github&utm_medium=referral&utm_campaign=profile&utm_content=fruition-jev-en)**
  - Problem: In a service that answers from documents, retrieval missed evidence and attached evidence to unanswerable questions, undermining trust.
  - Decision: GPT selection cost about 2.5x and took longer; tuning weights and RRF gave similar scores across settings, so I adopted Jev, which picks only from fixed options and had first been validated on request routing (77 → 81 of 98 correct).
  - Solution: Two stages: BGE-M3, the best Korean semantic model in benchmarks, and BM25 for exact terms gather candidates and Jev picks the final evidence. Compared on identical candidates with blind cross-grading, then cut candidates to 300 and compared 4, 6, 8 and 10 parallel batches, choosing 8 with no accuracy difference.
  - Result: Coverage on 80 answerable questions rose from 66.25% to 91.25%. Median selection time 9.090s → 1.137s (still slower than the original 0.431s).
- **[User-defined task instructions (Skills)](https://martinel2.github.io/en/portfolio/fruition-agent.html?utm_source=github&utm_medium=referral&utm_campaign=profile&utm_content=fruition-agent-en)**
  - Problem: Recurring tasks differ by user, so they cannot all be built as features, and AI edits arrived with parts of the request missing, leaving repeatable work to chance.
  - Decision: AI drafts instructions, code checks permissions and scope, and the user decides publishing and applying. Code format checks missed omitted requests, so I added LLM semantic evaluation.
  - Solution: Authoring, review and publishing of natural-language instructions with checks against bypassing permission or approval; preview and separate approval before changes; semantic evaluation with at most one rewrite. Generation, evaluation and rewrite run as LangGraph nodes for step-level tracing, and published Skills are stored as immutable versions in PostgreSQL.
  - Result: Edit quality 94 → 104 of 114 drafts (82.5% → 91.2%); documents stayed unchanged before approval. Failed drafts 20 → 10.
- **[PDF → Markdown conversion](https://martinel2.github.io/en/portfolio/fruition-document.html?utm_source=github&utm_medium=referral&utm_campaign=profile&utm_content=fruition-pdf-en)**
  - Problem: Broken tables and equations in paper PDFs made the figures behind Wiki pages and answers unusable.
  - Decision: Repairing only detected damage missed errors, and full AI conversion lacked table and equation accuracy and was costly, so I split processing by content type. Body text uses fast AnyDoc extraction; repair moved from an sLLM to commercial LLM APIs to avoid GPU server costs.
  - Solution: Extracted body text with AnyDoc and repaired only garbled parts with AI, read table and equation regions separately, and kept original figures.
  - Result: PDF → Markdown restoration rate rose from about 45% with Docling alone to about 90%.
- **[AI job cancellation and rollback](https://martinel2.github.io/en/portfolio/fruition-rollback.html?utm_source=github&utm_medium=referral&utm_campaign=profile&utm_content=fruition-rollback-en)**
  - Problem: AI jobs save documents, folders and Wiki pages several times between model calls; if cancelling leaves partial changes, users cannot trust AI with work.
  - Decision: Asking the model to undo cannot guarantee original values and a global lock cannot handle failures, so I chose reverse rollback from execution records.
  - Solution: Save the cancel state first to block later writes, then restore children first in reverse order; rebuild merged Wiki pages without the cancelled contribution.
  - Result: Cancelling a two-folder, six-document task at each of 9 points restored the original state, with no model calls during rollback.
- **[Parallel Wiki generation](https://martinel2.github.io/en/portfolio/fruition-ingest.html?utm_source=github&utm_medium=referral&utm_campaign=profile&utm_content=fruition-ingest-en):** Distributed per-document jobs over Kafka with up to 4 workers; analysis of 4 documents fell from 282.11s to 73.89s (about 74% faster).
- **MSA:** Splitting only by feature would keep DB load the same while adding hops, so I proposed splitting by data ownership and co-designed boundaries and communication with teammates and mentors.

### Pilltip | Personalized AI medication service

[GitHub repository](https://github.com/PillTipKR/Pilltip) | [Project overview](https://martinel2.github.io/en/portfolio/pilltip.html?utm_source=github&utm_medium=referral&utm_campaign=profile&utm_content=pilltip-detail-en)

2025.03 — 2025.12 | Pusan National University capstone | 6 users on internal APK builds | Team project (3 + designer) | **Core backend, data preparation**

- **How it started:** drug information is scattered, making it hard to check whether a medicine is safe for your current health condition.
- **Team:** me (backend & AI), 1 Android (Kotlin app), 1 backend & security (user DB, login, questionnaires, AES-GCM), designer

**What I built**

- **[Drug data pipeline](https://martinel2.github.io/en/portfolio/pilltip-data.html?utm_source=github&utm_medium=referral&utm_campaign=profile&utm_content=pilltip-data-en)**
  - Problem: Rewriting about 44,000 drug records as-is was estimated at about $200 in API costs, more than the budget allowed for covering every drug.
  - Decision: Instead of covering fewer drugs, convert each repeated sentence once. The job needed no real-time response, so Batch API traded waiting time for lower cost.
  - Solution: Split text into sentence blocks, merged exact duplicates, converted via GPT Batch API and mapped results back to each drug. Reproduced in 2026 with PySpark, which parallelizes across cores and scales out, to measure each step.
  - Result: Actual API spending was $11.18 versus about $200 estimated for all original text (preprocessing labour excluded). In the reproduction, exact deduplication cut text from 744MB to 44.1MB (−94.1%).
- **[Personalized medication chatbot](https://martinel2.github.io/en/portfolio/pilltip-personalization.html?utm_source=github&utm_medium=referral&utm_campaign=profile&utm_content=pilltip-chatbot-en)**
  - Problem: Users checking whether a drug is safe describe symptoms in different words from drug indications, and the health data needed for personalization could not go to external AI.
  - Decision: A synonym dictionary had too many overlapping symptoms, so I used semantic search; filtering the profile had too many cases, so profile decisions stay internal. Weaviate was chosen as lighter than Milvus, and Spring AI ran orchestration on the Spring backend to avoid a separate Python container.
  - Solution: Weaviate semantic search and AI orchestration route to drug search, medication risk and dosage paths; pregnancy, current medications and underlying conditions are judged in internal code.
  - Result: Personalized symptom-based search with those profile fields excluded from external LLM inputs.
- **Backend:** Designed the drug database on Java and Spring Boot with search, autocomplete and DUR risk display. Elasticsearch handles partial matching and autocomplete and Redis caches repeated risk lookups, cutting search responses from 5–7s to 0.8s on average. Built FCM medication reminders and logs, deep-link friend invites and family profile switching.
- **Exhibition feedback:** Most of the 10 pieces of feedback from two exhibitions asked for health supplements, so I extended search and autocomplete, caution and interaction info, medication reminders and logs, and chatbot answers to health supplements.

## Open source

**[Rhwp](https://github.com/edwardkim/rhwp)** (2026.06): Gave Claude Code a work plan and contribution rules to automate the flow from issue analysis to PR, including HWP/HWPX save-error fixes; 7 PRs merged. Listed as a contributor.

[PR #1213 | Merged](https://github.com/edwardkim/rhwp/pull/1213) | [PR #1351 | Submitted](https://github.com/edwardkim/rhwp/pull/1351) | [All contributions](https://github.com/edwardkim/rhwp/pulls?q=is%3Apr+author%3AMartinel2)

## Activities

- **AWS training** (2026.06 — 2026.07): Completed Cloud Practitioner Essentials, Machine Learning Engineering on AWS, and Developing Generative AI Applications on AWS
- **APPTIVE, Pusan National University** (2025.03 — 2026.01): Backend mentee and mentor. Led 6 mentoring and code-review sessions for 12 mentees. Helped revise the curriculum to strengthen HTTP, Servlet, REST API and database foundations. [Backend Mentor Merit Award](https://martinel2.github.io/assets/evidence/apptive-merit.jpeg) (2026.01.09)
- **SK AI SUMMIT, K-ICT WEEK in Busan** (2025.11 / 2025.07): Represented Pusan National University at the Pilltip booth, demonstrating the service to more than 100 visitors and answering technical questions.
- **945-day Baekjoon problem-solving streak** (2022.02 — 2025.07): Aiming for one problem a day, I reached a longest streak of 945 consecutive days on solved.ac. 1,659 problems solved, Platinum IV. [Solutions](https://github.com/Martinel2/BaekJoon) | [solved.ac](https://solved.ac/profile/kkuldangi3)

## Awards

- **Capstone Design Gold Award** | 2025.10 | Software & AI division / College of Information and Biomedical Engineering, Pusan National University
- **Busan DATA WEEK Top Excellence Award** | 2025.09 | Data utilization case competition / Busan Techno Park
- **AI LAUNCH Career School Startup Hackathon Encouragement Award** | 2025.09 | KRYPTON X x Root Impact x Google.org
- **SW University Digital Competition Sponsor Award** | 2025.08 | SW University Council

## Education & certifications

- **Pusan National University** | 2022.02 — 2026.02 (Transfer) | GPA 4.12 / 4.5
- **Daegu University** | 2019.03 — 2022.02 (Withdrew) | GPA 4.2 / 4.5
- **Engineer Information Processing** | 2025.09 | Human Resources Development Service of Korea

## Writing (Korean)

- [Moving to MSA and learning from feedback](https://velog.io/@kkuldangi3/MSA-전환과-피드백)
- [Reflections on design thinking](https://velog.io/@kkuldangi3/디자인-싱킹-회고)

## Algorithms

[![Solved.ac Profile](https://mazassumnida.wtf/api/v2/generate_badge?boj=kkuldangi3)](https://solved.ac/profile/kkuldangi3)

<img src="https://martinel2.github.io/assets/evidence/baekjoon-streak.png" alt="solved.ac yearly streaks, 2022 to 2025" width="720">
