# 🛠️ Tech Toolbox

By Ben Thompson-Watson

A curated, single-file toolbox for programmers, data scientists, and anyone working in tech. It collects the tools, links, and working practices that make your work easier, more efficient, and more effective — from AI-assisted development through to shell utilities.

## Table of Contents

- [🤖 AI-Assisted Development](#-ai-assisted-development)
  - [AI Coding Tools](#ai-coding-tools)
  - [Choosing the Right Tool](#choosing-the-right-tool)
  - [Working with AI: Foundations](#working-with-ai-foundations)
  - [Modes and Workflows](#modes-and-workflows)
  - [Context Windows](#context-windows)
  - [Prompt Patterns](#prompt-patterns)
  - [Slash Commands](#slash-commands)
  - [Evaluating AI Output](#evaluating-ai-output)
  - [Hands-On Labs and Workshop Kit](#hands-on-labs-and-workshop-kit)
- [🧠 AI Platforms, Models, and Frameworks](#-ai-platforms-models-and-frameworks)
- [💻 Programming Languages](#-programming-languages)
- [🌿 Version Control](#-version-control)
- [📊 Data Science Tools](#-data-science-tools)
- [🌐 Web Development Tools](#-web-development-tools)
- [🧪 Testing and QA](#-testing-and-qa)
- [☁️ Cloud Services](#️-cloud-services)
- [⚙️ DevOps and Infrastructure](#️-devops-and-infrastructure)
- [📈 Dashboarding and Results Tools](#-dashboarding-and-results-tools)
- [🎨 Design Tools](#-design-tools)
- [🚀 Productivity Tools](#-productivity-tools)
- [🧩 Useful VSCode Extensions](#-useful-vscode-extensions)
- [🐚 Useful UNIX / macOS Shell Tools](#-useful-unix--macos-shell-tools)
- [📚 Learning Resources](#-learning-resources)
- [Contributing](#contributing)
- [Acknowledgments](#acknowledgments)

## 🤖 AI-Assisted Development

Everything you need to compare, adopt, and get real value from modern AI coding tools — including the full workshop material from the old `ai-toolbox` repo.

### AI Coding Tools

| Tool | Best for | Watch-outs |
|------|----------|------------|
| [GitHub Copilot](https://github.com/features/copilot) ([docs](https://docs.github.com/en/copilot)) | In-editor coding help, iterative edits, and code explanation — fast inner-loop support while writing code. | Confirm generated code matches project conventions. |
| [Claude Code](https://claude.com/claude-code) ([docs](https://code.claude.com/docs)) | Agentic coding in the terminal, IDE, or web — reasoning-heavy tasks, multi-file changes, drafting and iterating on implementations. | Keep task boundaries and verification criteria clear. |
| [OpenAI Codex](https://openai.com/codex/) | Structured coding tasks, larger changes, and agentic workflows — implementation plus reasoning over files and tasks. | Keep requirements explicit to avoid broad or off-target edits. |
| [Cursor](https://cursor.com/) | An AI-first code editor with inline edits, chat, and codebase-aware autocomplete. | Review multi-file "agent" edits carefully before accepting. |
| [Playwright](https://playwright.dev/) ([docs](https://playwright.dev/docs/intro)) | End-to-end testing and browser automation — pairs well with AI tools for generating and maintaining UI tests. | Test reliability depends on stable selectors and good test isolation. |
| GitNexus | Git-centric workflows, repository navigation, and collaboration context tied to branch state, history, and PR flow. | Validate outputs against the current branch and CI rules. |
| Pixel Agents | Multi-step agent workflows and orchestration — chaining planning, implementation, and validation in one flow. | Keep guardrails explicit to avoid over-broad actions in automated runs. |
| UI-UX Pro Max Skill Next Level Builder Tool | Rapid UI concepting, UX flow iteration, and high-polish interface drafting. | Validate accessibility, responsiveness, and design-system consistency before shipping. |

### Choosing the Right Tool

- Use lightweight in-editor help (Copilot-style autocomplete) for small edits.
- Use planning-first agentic workflows (Claude Code, Codex) for multi-file changes.
- Use review-focused modes when quality risk is high.
- Use Playwright when validating real user flows in the browser.
- Use multi-agent tools when you want repeatable workflows with clear stages.
- Use UI/UX builder tools when your priority is design exploration and prototype velocity.

### Working with AI: Foundations

The goal: build practical judgment for using AI tools in software workflows.

**Core principles**

- Be specific about scope, constraints, and desired output format.
- Start with planning for non-trivial tasks.
- Keep context focused: include only relevant files and requirements.
- Verify results with tests, lint checks, and manual review.
- Treat AI output as a draft until validated.

**Common failure modes**

- Vague prompts produce generic output.
- Too much context creates noisy responses.
- Skipping review introduces regressions.
- Missing acceptance criteria causes rework.

**Good prompt skeleton**

1. Task and goal
2. Constraints
3. Inputs (code, docs, links)
4. Output format
5. Verification steps

**Practical rule:** use a simple loop — *Plan → Implement → Verify → Reflect*.

### Modes and Workflows

Different modes optimize for different outcomes: speed, safety, depth, or clarity.

| Mode | Use when | Output | Benefit |
|------|----------|--------|---------|
| **Plan** | Requirements are complex or unclear | Ordered steps, risks, assumptions, validation plan | Reduces rework and hidden coupling |
| **Build** | Requirements are clear and scoped | Implemented code and targeted changes | High velocity |
| **Review** | Code quality and regressions are the primary concern | Findings by severity, file-level evidence, test gaps | Catches risk early |
| **Debug** | Behavior is wrong or flaky | Root-cause hypothesis, repro steps, fix, regression test | Systematic troubleshooting |
| **Refactor** | Behavior should stay the same but code quality should improve | Cleaner structure, naming, modularity, unchanged behavior | Maintainability |

**Recommended workflow**

1. Plan for 3–5 minutes.
2. Implement the smallest viable change.
3. Review findings and risks.
4. Verify with tests.
5. Document what changed and why.

### Context Windows

A context window is the amount of text and code the model can effectively process in one interaction.

**Why it matters**

- Larger context can improve coherence across files.
- Too much irrelevant context can lower quality.
- Higher context usage can increase latency and cost.

**Practical strategy**

- Include only relevant files and excerpts.
- Prefer concise summaries plus precise snippets.
- Re-anchor often: restate the goal and acceptance criteria.
- Split large tasks into smaller scoped passes.

<details>
<summary><strong>Context packing checklist</strong></summary>

- [ ] Task statement is explicit.
- [ ] Constraints are listed.
- [ ] Inputs are current and minimal.
- [ ] Expected output format is defined.
- [ ] Verification steps are included.

</details>

### Prompt Patterns

Four reusable patterns — each one states a goal, constraints, inputs, and the expected output.

| Pattern | Goal | Output |
|---------|------|--------|
| **Implementation** | Implement feature X in file Y (keep API unchanged, no new dependencies) | Patch + short rationale + test plan |
| **Review** | Review a change for bugs and regressions, severity-first | Findings with evidence and test gaps |
| **Refactor** | Improve readability without behavior changes, preserving external contracts | Refactor patch + safety checks |
| **Debug** | Identify the root cause of issue X, minimizing speculative fixes | Cause, fix, regression test |

**Anti-patterns to avoid**

- "Fix this" with no context.
- Asking for broad rewrites without constraints.
- No acceptance criteria.
- No verification requested.

<details>
<summary><strong>Reusable prompt template</strong></summary>

```markdown
## Task
Describe the exact outcome you want.

## Context
List only relevant files, constraints, and existing behavior.

## Requirements
- Functional requirements
- Non-functional requirements
- Constraints (dependencies, style, compatibility)

## Output Format
Specify format: patch, summary, checklist, tests.

## Verification
Define checks to run and pass criteria.
```

**Example**

> **Task:** Add pagination to endpoint X.
> **Context:** API in `src/api/users.ts`, tests in `tests/users.test.ts`.
> **Requirements:** Backward compatible, default page size 20.
> **Output:** Code patch + test updates + short rationale.
> **Verification:** All tests pass, lint clean.

</details>

### Slash Commands

Slash commands speed up prompting by giving the assistant a clear intent before your natural-language request. **Fast rule:** run `/help` first in your tool to see the exact commands available in your version — availability varies by IDE, extension version, and workspace setup.

**Commonly used chat commands (GitHub Copilot Chat and similar)**

- `/explain` — ask for an explanation of selected code or errors.
- `/fix` — ask for a direct fix proposal.
- `/tests` — generate or improve tests.
- `/new` — scaffold a new file or component from a prompt.
- `/doc` — generate or improve documentation.

**`/init`-style commands** — some code-agent tools (like Claude Code) provide an `/init` command that bootstraps project guidance files, captures conventions and coding rules, and gives the assistant a stronger baseline for future tasks. After init, ask for: a project summary, build and test commands, coding standards, and high-risk areas to review first.

**Example prompt flow**

- `/init` then: *"Create a short contributor guide for this repo; include setup, run, test, and review checklist."*
- `/tests` then: *"Generate tests for edge cases in user input validation and explain coverage gaps."*
- `/fix` then: *"Fix the failing test and keep behavior backward compatible."*

**Safety notes:** always review generated edits before commit, run tests and lint checks after assistant-generated changes, and keep prompts scoped to reduce unintended edits.

### Evaluating AI Output

Score each area, then total it up.

**Output quality** — requirements fully covered · no obvious functional regressions · clear naming and structure · edge cases addressed.

**Safety and reliability** — assumptions stated · risks called out · changes scoped and reversible · verification steps executed.

**Collaboration readiness** — rationale documented · diff easy to review · follow-up tasks explicit.

| Score | Verdict |
|-------|---------|
| 18–20 | Production-ready with minor polish |
| 14–17 | Good, with targeted fixes needed |
| 10–13 | Usable draft, significant review required |
| < 10 | Rework recommended |

### Hands-On Labs and Workshop Kit

<details>
<summary><strong>Five hands-on labs</strong></summary>

1. **Mode comparison** — build a small feature with Plan Mode then Build Mode. *Deliverable:* compare speed, quality, and rework.
2. **Context window tradeoffs** — solve the same bug with large vs. focused context. *Deliverable:* compare iterations and final correctness.
3. **Review quality** — generate code, then run Review Mode on it. *Deliverable:* list findings and apply the top 3 fixes.
4. **Playwright test generation** — use an AI tool to generate Playwright tests for a critical user flow. *Deliverable:* passing tests, stable selectors, and one flaky-test fix.
5. **Prompt pattern A/B test** — use a vague prompt and a structured prompt on the same task. *Deliverable:* side-by-side output quality comparison.

**Lab rubric** — score 1–5 on: correctness, clarity, maintainability, test quality, and time to completion.

</details>

<details>
<summary><strong>Suggested 90-minute workshop flow + agenda template</strong></summary>

**90-minute flow**

1. 10 min — Foundations
2. 20 min — Tool and mode comparison
3. 35 min — Labs
4. 15 min — Group review and scoring
5. 10 min — Wrap-up and next steps

**Agenda template**

```markdown
## Session Details
- Title / Audience / Duration / Prerequisites

## Learning Outcomes
- Outcome 1, 2, 3

## Agenda
1. Intro and goals
2. Tool overview
3. Modes and context windows
4. Hands-on labs
5. Debrief and checklist scoring
6. Q&A

## Materials
- Repo link, slides link, example tasks

## Follow-Up
- Practice tasks, resource list, feedback form
```

</details>

## 🧠 AI Platforms, Models, and Frameworks

- [Anthropic Claude](https://claude.ai/) ([API docs](https://docs.claude.com/)) - Frontier AI assistant and API from Anthropic, strong at reasoning, coding, and long-context tasks.
- [OpenAI Platform](https://platform.openai.com/) - API access to GPT models, embeddings, and assorted developer tooling.
- [Google Gemini](https://ai.google.dev/) - Google's multimodal model family, with a free tier via Google AI Studio.
- [Hugging Face](https://huggingface.co/) - The hub for open-source models, datasets, and ML demos, plus the `transformers` library.
- [Ollama](https://ollama.com/) - Run open-source LLMs (Llama, Mistral, Gemma, and more) locally with a single command.
- [LangChain](https://www.langchain.com/) - A popular framework for composing LLM applications: chains, agents, retrieval, and integrations.
- [LlamaIndex](https://www.llamaindex.ai/) - A data framework for connecting LLMs to your own data (RAG pipelines, indices, query engines).
- [OpenRouter](https://openrouter.ai/) - A single API endpoint for calling many different model providers, handy for comparisons.
- [LM Studio](https://lmstudio.ai/) - A desktop app for discovering, downloading, and running local LLMs with a friendly UI.

## 💻 Programming Languages

- [Python](https://www.python.org/) - A high-level, interpreted programming language with a focus on simplicity and readability.
- [TypeScript](https://www.typescriptlang.org/) - A strongly typed superset of JavaScript that compiles to plain JavaScript, now the default for serious front-end work.
- [JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript) - A scripting language used primarily for web development, but also for server-side programming and game development.
- [Java](https://www.java.com/en/) - A popular programming language used for building enterprise-level applications, mobile apps, and more.
- [C++](https://isocpp.org/) - A high-performance, general-purpose programming language often used in system software, game development, and other performance-critical applications.
- [C](https://en.wikipedia.org/wiki/C_(programming_language)) - A high-level programming language used for system-level programming, embedded systems, and more.
- [C#](https://docs.microsoft.com/en-us/dotnet/csharp/) - A modern, multi-paradigm programming language developed by Microsoft for building Windows and web applications.
- [Go](https://golang.org/) - An open-source programming language created by Google, designed for building efficient, scalable, and reliable software.
- [Rust](https://www.rust-lang.org/) - A systems programming language that focuses on safety, speed, and concurrency.
- [Kotlin](https://kotlinlang.org/) - A modern programming language for the Java Virtual Machine (JVM) that can also be compiled to JavaScript or native code.
- [Swift](https://developer.apple.com/swift/) - A general-purpose programming language created by Apple for developing software for macOS, iOS, watchOS, and tvOS.
- [Ruby](https://www.ruby-lang.org/en/) - A dynamic, object-oriented programming language with a focus on simplicity and productivity.
- [PHP](https://www.php.net/) - A server-side scripting language used primarily for web development, but also for general-purpose programming.
- [SQL](https://en.wikipedia.org/wiki/SQL) - The standard language for querying and manipulating relational databases.
- [Haskell](https://www.haskell.org/) - A functional programming language that focuses on strong typing, lazy evaluation, and mathematical reasoning.
- [SPARK Ada](https://en.wikipedia.org/wiki/SPARK_(programming_language)) - A programming language designed for high-assurance software development.
- [HTML](https://developer.mozilla.org/en-US/docs/Web/HTML) - A markup language used for creating web pages and other web-based content.
- [CSS](https://developer.mozilla.org/en-US/docs/Web/CSS) - A style sheet language used for describing the look and formatting of a document written in HTML or XML.
- [JSON](https://www.json.org/) - A lightweight data interchange format that is easy for humans to read and write, and easy for machines to parse and generate.
- [XML](https://www.w3.org/XML/) - A markup language used for storing and transporting data, often used in web services and other data exchange scenarios.
- [YAML](https://yaml.org/) - A human-friendly data serialization format, ubiquitous in configuration files and CI/CD pipelines.

## 🌿 Version Control

- [Git](https://git-scm.com/) - A widely-used version control system that allows you to keep track of changes to your code and collaborate with others.
- [GitHub](https://github.com/) - A web-based platform that provides hosting for Git repositories, as well as a range of collaboration and project management tools.
- [GitLab](https://gitlab.com/) - A complete DevOps platform with Git hosting, built-in CI/CD, and issue tracking.
- [Bitbucket](https://bitbucket.org/) - Atlassian's Git hosting service, with tight Jira integration.
- [Conventional Commits](https://www.conventionalcommits.org/) - A lightweight convention for commit messages that makes history readable and enables automated changelogs.
- [gitignore.io](https://www.toptal.com/developers/gitignore) - Generate `.gitignore` files for any combination of languages, editors, and operating systems.
- [Oh Shit, Git!?!](https://ohshitgit.com/) - Plain-English recipes for getting out of common Git messes.

## 📊 Data Science Tools

- [Jupyter Notebook](https://jupyter.org/) - An open-source web application that allows you to create and share documents that contain live code, equations, visualizations, and narrative text.
- [Google Colab](https://colab.research.google.com/) - A cloud-based Jupyter notebook environment that allows users to run Python code, including machine learning code, using free GPU and TPU resources.
- [Microsoft Azure Databricks](https://azure.microsoft.com/en-us/services/databricks/) - A fast, easy, and collaborative Apache Spark-based analytics platform designed to help you process big data and build AI solutions.
- [Neo4j](https://neo4j.com/) - A graph database that enables users to store, manage, and analyze data relationships with high performance and scalability.
- [NumPy](https://numpy.org/) - A library for the Python programming language that provides support for large, multi-dimensional arrays and matrices, as well as a range of mathematical functions.
- [Pandas](https://pandas.pydata.org/) - A library for the Python programming language that provides support for data analysis, manipulation, and visualization.
- [Polars](https://pola.rs/) - A lightning-fast DataFrame library written in Rust, a modern alternative to Pandas for large datasets.
- [Scikit-learn](https://scikit-learn.org/) - A library for the Python programming language that provides tools for data mining and analysis, including regression, classification, clustering, and more.
- [Choosing the Right Estimator](https://scikit-learn.org/stable/tutorial/machine_learning_map/index.html) - A page on Scikit-learn that provides a high-level decision-making overview to help users select the most appropriate estimator for a given machine learning task, based on the characteristics of the data.
- [PyTorch](https://pytorch.org/) - The dominant deep learning framework in research and increasingly in production, with a Pythonic, define-by-run API.
- [TensorFlow](https://www.tensorflow.org/) - An end-to-end open-source platform for machine learning that makes it easy to build and deploy ML models at scale, and includes a comprehensive suite of tools and libraries for developing advanced ML applications.
- [Keras](https://keras.io/) - An easy-to-use deep learning library that allows you to build, train, and deploy neural networks with just a few lines of code.
- [Matplotlib](https://matplotlib.org/) - A comprehensive library for creating static, animated, and interactive visualizations in Python, with publication-quality figures in a variety of hardcopy formats and interactive environments across platforms.
- [Seaborn](https://seaborn.pydata.org/) - A library for the Python programming language that provides tools for data visualization and exploration, including statistical plots, heatmaps, and more.
- [Plotly](https://plotly.com/python/) - Interactive, publication-quality charts for Python (and JavaScript), great for dashboards and notebooks.
- [Streamlit](https://streamlit.io/) - Turn Python scripts into shareable data apps in minutes — ideal for ML demos and internal tools.
- [Python Graph Gallery](https://www.python-graph-gallery.com/) - A collection of hundreds of charts made with Python, including code and examples to recreate them.
- [ColorBrewer](https://colorbrewer2.org/) - A tool for creating color schemes for maps and visualizations, with options for colorblind-safe and print-friendly palettes.
- [Kaggle](https://www.kaggle.com/) - Datasets, competitions, and notebooks for practicing and benchmarking data science skills.

## 🌐 Web Development Tools

### Front-End Development

- [React](https://reactjs.org/) - A popular JavaScript library for building user interfaces, developed and maintained by Facebook.
- [Next.js](https://nextjs.org/) - The leading React framework, with server-side rendering, file-based routing, and full-stack capabilities.
- [Vue.js](https://vuejs.org/) - A progressive, lightweight JavaScript framework for building UIs, developed and maintained by a community of developers.
- [Svelte](https://svelte.dev/) - A compiler-based UI framework that shifts work from the browser to build time, producing fast, small bundles.
- [Bootstrap](https://getbootstrap.com/) - A popular open-source CSS framework for building responsive and mobile-first websites and web applications.
- [Tailwind CSS](https://tailwindcss.com/) - A highly customizable and utility-first CSS framework for building modern web interfaces.

### Back-End Development

- [Node.js](https://nodejs.org/) - A popular server-side JavaScript runtime that allows you to build scalable and efficient web applications and APIs.
- [Express](https://expressjs.com/) - A minimalist and flexible Node.js web framework that provides a robust set of features for building web and mobile applications.
- [Django](https://www.djangoproject.com/) - A high-level Python web framework that helps you build scalable and secure web applications quickly.
- [Flask](https://palletsprojects.com/p/flask/) - A lightweight and flexible Python web framework that provides useful tools and features for building web applications.
- [FastAPI](https://fastapi.tiangolo.com/) - A modern, high-performance Python web framework for building APIs, with automatic OpenAPI docs and type-hint-driven validation.
- [MongoDB](https://www.mongodb.com/) - A popular NoSQL database that provides scalability and flexibility for building modern web applications.
- [PostgreSQL](https://www.postgresql.org/) - A powerful open-source relational database management system that provides scalability and security features for web applications.
- [Redis](https://redis.io/) - An in-memory data store used as a cache, message broker, and database for high-performance applications.
- [SQLite](https://www.sqlite.org/) - A tiny, zero-configuration, file-based SQL database — perfect for prototypes, embedded use, and small apps.

### Other Web Development Tools

- [Vite](https://vitejs.dev/) - A blazing-fast build tool and dev server that has become the default for modern front-end projects.
- [Webpack](https://webpack.js.org/) - A popular static module bundler for JavaScript applications that helps you manage dependencies and optimize your code.
- [Babel](https://babeljs.io/) - A popular JavaScript transpiler that helps you write modern JavaScript code and transpiles it to compatible code that can run in older browsers.
- [Lighthouse](https://developers.google.com/web/tools/lighthouse) - A powerful open-source tool from Google that helps you improve the quality and performance of your web applications.
- [Can I use](https://caniuse.com/) - Browser support tables for HTML, CSS, and JavaScript features.
- [ngrok](https://ngrok.com/) - Expose a local development server to the internet with one command — great for demos and webhook testing.

## 🧪 Testing and QA

- [Playwright](https://playwright.dev/) - Cross-browser end-to-end testing and automation with a trace viewer, robust test runner, and parallel execution.
- [Cypress](https://www.cypress.io/) - A developer-friendly end-to-end testing framework that runs in the browser with time-travel debugging.
- [Jest](https://jestjs.io/) - A delightful JavaScript testing framework with a focus on simplicity, batteries included.
- [Vitest](https://vitest.dev/) - A Vite-native unit test framework — Jest-compatible API with much faster startup.
- [pytest](https://docs.pytest.org/) - The de facto standard Python testing framework: simple asserts, powerful fixtures, and a huge plugin ecosystem.
- [Postman](https://www.postman.com/) - Build, test, and document APIs with collections, environments, and automated test suites.
- [Selenium](https://www.selenium.dev/) - The long-standing standard for browser automation, with bindings for many languages.
- [k6](https://k6.io/) - Developer-centric load testing: write performance tests in JavaScript and run them from the CLI or cloud.

## ☁️ Cloud Services

- [Amazon Web Services (AWS)](https://aws.amazon.com/) - A comprehensive and widely used cloud platform that provides a range of services, including compute, storage, databases, analytics, and more.
- [Microsoft Azure](https://azure.microsoft.com/) - A cloud computing platform by Microsoft that offers a variety of services and solutions for hosting, deploying, and managing web applications.
- [Google Cloud Platform (GCP)](https://cloud.google.com/) - A suite of cloud computing services by Google that includes computing, storage, and application development tools.
- [Firebase](https://firebase.google.com/) - A mobile and web application development platform by Google that offers a range of backend services, including hosting, real-time database, and authentication.
- [Vercel](https://vercel.com/) - Zero-config deployment for front-end frameworks (especially Next.js), with previews for every pull request.
- [Netlify](https://www.netlify.com/) - A platform for deploying static sites and serverless functions with a generous free tier.
- [Cloudflare](https://www.cloudflare.com/) - CDN, DNS, security, and an increasingly capable serverless platform (Workers, Pages, R2).
- [Supabase](https://supabase.com/) - An open-source Firebase alternative built on PostgreSQL: auth, storage, realtime, and instant APIs.
- [Heroku](https://www.heroku.com/) - A cloud platform that provides a fully-managed environment for hosting and deploying web applications, with a focus on ease of use and rapid development.
- [DigitalOcean](https://www.digitalocean.com/) - A cloud infrastructure provider that offers simple and reliable virtual servers, object storage, and more, with a focus on developers and small businesses.

## ⚙️ DevOps and Infrastructure

- [Docker](https://www.docker.com/) - Package applications and their dependencies into portable containers that run the same everywhere.
- [Kubernetes](https://kubernetes.io/) - The industry-standard platform for orchestrating containers at scale.
- [GitHub Actions](https://github.com/features/actions) - CI/CD built into GitHub: build, test, and deploy straight from your repository.
- [Terraform](https://www.terraform.io/) - Infrastructure as code: declaratively provision cloud resources across AWS, Azure, GCP, and more.
- [Ansible](https://www.ansible.com/) - Agentless automation for configuration management, application deployment, and orchestration.
- [Prometheus](https://prometheus.io/) - The standard open-source monitoring system and time-series database for metrics.
- [Grafana](https://grafana.com/) - Beautiful dashboards and alerting on top of Prometheus and dozens of other data sources.
- [Nginx](https://nginx.org/) - A high-performance web server, reverse proxy, and load balancer.

## 📈 Dashboarding and Results Tools

- [Power BI](https://powerbi.microsoft.com/en-us/) - Data visualization and business intelligence tool from Microsoft that allows users to create interactive dashboards and reports.
- [Tableau](https://www.tableau.com/) - Powerful data visualization tool that helps users to create interactive and beautiful dashboards.
- [Looker Studio](https://lookerstudio.google.com/) - Free data visualization tool from Google (formerly Data Studio) that helps users to create interactive dashboards and reports.
- [Looker](https://looker.com/) - Business intelligence and analytics platform that allows users to explore and analyze data using SQL-like queries.
- [QlikView](https://www.qlik.com/us/products/qlikview) - Data discovery and business intelligence platform that enables users to analyze, visualize and explore their data.
- [Domo](https://www.domo.com/) - Cloud-based business intelligence platform that provides real-time data insights and visualization.
- [SAP Lumira](https://www.sap.com/products/lumira.html) - Data visualization tool that enables users to create interactive dashboards, charts and maps.
- [Excel](https://www.microsoft.com/en-us/microsoft-365/excel) - Powerful spreadsheet program that can be used to create charts, graphs and tables to visualize data.
- [IBM Cognos Analytics](https://www.ibm.com/products/cognos-analytics) - Business intelligence and analytics platform that provides data visualization, reporting and analysis capabilities.
- [SAS Visual Analytics](https://www.sas.com/en_us/software/visual-analytics.html) - Data visualization and analysis tool that enables users to explore and analyze their data.

## 🎨 Design Tools

- [Figma](https://www.figma.com/) - A browser-based interface design tool that allows you to collaborate in real-time with others.
- [Sketch](https://www.sketch.com/) - A digital design tool that is widely used for designing user interfaces and user experiences.
- [Adobe Creative Cloud](https://www.adobe.com/creativecloud.html) - A suite of creative software products, including Photoshop, Illustrator, InDesign, and more.
- [Excalidraw](https://excalidraw.com/) - A virtual whiteboard for sketching hand-drawn-style diagrams — perfect for architecture sketches.
- [Canva](https://www.canva.com/) - Quick, template-driven graphic design for slides, social images, and marketing material.
- [Coolors](https://coolors.co/) - A fast color-scheme generator for finding and refining palettes.
- [MockUPhone](https://mockuphone.com) - A website that allows users to create high-quality device mockups for their app or website designs.

## 🚀 Productivity Tools

- [Notion](https://www.notion.so/) - A web-based productivity tool that allows you to create notes, databases, wikis, and more.
- [Obsidian](https://obsidian.md/) - A powerful knowledge base and note-taking app that works on local Markdown files, with backlinks and graph view.
- [Trello](https://trello.com/) - A web-based project management tool that allows you to organize your work and collaborate with others.
- [Linear](https://linear.app/) - A fast, keyboard-driven issue tracker built for modern software teams.
- [Slack](https://slack.com/) - A team collaboration tool that allows you to communicate and share files with others in real-time.
- [Miro](https://miro.com/) - A collaborative online whiteboard for brainstorming, planning, and workshops.

## 🧩 Useful VSCode Extensions

- [GitLens](https://marketplace.visualstudio.com/items?itemName=eamodio.gitlens) - Supercharges Git in VSCode: inline blame, rich history, and comparison tools.
- [Git Graph](https://marketplace.visualstudio.com/items?itemName=mhutchie.git-graph) - An extension that provides an interactive and customizable graph of your Git repository, making it easier to understand the history and relationships of your branches and commits.
- [Prettier](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode) - The opinionated code formatter — set it to format on save and never argue about style again.
- [ESLint](https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint) - A popular linter that helps you find and fix errors and code quality issues in your JavaScript and TypeScript code.
- [Error Lens](https://marketplace.visualstudio.com/items?itemName=usernamehw.errorlens) - Surfaces errors and warnings inline, right where they occur, instead of hiding them in the Problems panel.
- [GitHub Copilot](https://marketplace.visualstudio.com/items?itemName=GitHub.copilot) - AI pair programming in the editor: autocomplete, chat, and code explanation.
- [CodeSnap](https://marketplace.visualstudio.com/items?itemName=adpyke.codesnap) - A tool that helps you capture and share your code as images, making it easier to communicate your ideas to others.
- [Doxygen Documentation Generator](https://marketplace.visualstudio.com/items?itemName=cschlosser.doxdocgen) - An extension that helps you generate Doxygen-style documentation for your C++, C#, and Java code.
- [Live Server](https://marketplace.visualstudio.com/items?itemName=ritwickdey.LiveServer) - Launch a local development server with live reload for static and dynamic pages.

## 🐚 Useful UNIX / macOS Shell Tools

- [Homebrew](https://brew.sh/) - A package manager for macOS and Linux that makes it easy to install and manage a variety of Unix software packages and tools.
- [Oh My Zsh](https://ohmyz.sh/) - A community-driven framework for managing your Zsh configuration that includes a variety of plugins and themes to customize your shell experience.
- [Zsh Syntax Highlighting](https://github.com/zsh-users/zsh-syntax-highlighting) - A plugin for the Zsh shell that provides syntax highlighting for commands and their arguments, making it easier to spot errors and understand what's happening in your terminal session.
- [Zsh Autosuggestions](https://github.com/zsh-users/zsh-autosuggestions) - Another plugin for Zsh that suggests command completions based on your command history, making it faster to type frequently used commands and reducing typos.
- [tmux](https://github.com/tmux/tmux) - A terminal multiplexer that allows you to split your terminal window into multiple panes and tabs, making it easier to work with multiple terminal sessions at once.
- [jq](https://jqlang.github.io/jq/) - A command-line tool for processing and manipulating JSON data, making it easier to extract and transform data from APIs and other sources.
- [fzf](https://github.com/junegunn/fzf) - A command-line fuzzy finder that allows you to quickly search and navigate through files, directories, and command history using a fuzzy search interface.
- [ripgrep](https://github.com/BurntSushi/ripgrep) - A faster alternative to the grep command for searching through files and directories using regular expressions, making it easier to find and analyze large amounts of text data.
- [fd](https://github.com/sharkdp/fd) - A simple, fast, and user-friendly alternative to `find`.
- [bat](https://github.com/sharkdp/bat) - A `cat` clone with syntax highlighting, line numbers, and Git integration.
- [tldr](https://tldr.sh/) - Community-maintained, example-first cheat sheets for command-line tools — the man pages you actually wanted.
- [htop](https://htop.dev/) - An interactive process viewer that makes `top` look prehistoric.

## 📚 Learning Resources

- [MDN Web Docs](https://developer.mozilla.org/) - The definitive reference for HTML, CSS, JavaScript, and web APIs.
- [freeCodeCamp](https://www.freecodecamp.org/) - Free, project-based curriculum covering web development, data science, and more.
- [roadmap.sh](https://roadmap.sh/) - Community-driven learning roadmaps for developer roles and technologies.
- [The Odin Project](https://www.theodinproject.com/) - A free, full-stack web development curriculum with a strong project focus.
- [Exercism](https://exercism.org/) - Free coding practice in 70+ languages with mentor feedback.
- [LeetCode](https://leetcode.com/) - The go-to platform for practicing algorithm and data-structure problems and interview prep.
- [Anthropic Academy](https://www.anthropic.com/learn) - Courses and guides on building with Claude and prompt engineering.
- [DeepLearning.AI](https://www.deeplearning.ai/) - Short courses and specializations on machine learning, deep learning, and building with LLMs.
- [Awesome Lists](https://github.com/sindresorhus/awesome) - The master index of community-curated "awesome" lists on every technical topic imaginable.

## Contributing

If you have any suggestions for additional resources to add to this toolbox, please feel free to create a pull request.

## Acknowledgments

- This README merges and builds on the content of the former [`ai-toolbox`](https://github.com/BenWatson2000/ai-toolbox) repository.
- Thanks to everyone who suggests and maintains the resources listed here.
