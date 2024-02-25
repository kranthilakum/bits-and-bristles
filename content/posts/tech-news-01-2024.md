---
title: Tech News w01 2024
date: 2024-01-01T09:55:46+05:30
draft: false
categories:
- "tech-news"
tags:
- "programming"
- "tech-news"
---

In 2023, Angular team introduced fine-grained reactivity with _Signals_ and _deferrable views_. Signals are a new primitive that allows you to create a stream of values that can be subscribed to. Signals are similar to observables, but they are not lazy. They are eager and emit values immediately. Signals are also not multicast, so each subscription will get its own stream of values. Signals are a great way to model state that changes over time. They are also a great way to model events that happen over time. 

This year they might make _Zone.js_ optional. With optional Zone.js, we could expect improvement in load times and faster initial render along with hybrid rendering and partial hydration. And with Signals, we might detect changes in only parts of the template of a component.

A _Zone_ is an execution context that persists across async tasks. You can think of it as thread-local storage for JavaScript. It allows you to associate data with a task and access that data from any async task that runs in that zone. Angular uses zones to implement change detection. When a change is made to the model, Angular runs change detection to update the view. Change detection is triggered by events like click, keypress, and mousemove. Angular uses zones to detect these events and run change detection. This year they might make Zone.js optional. Zone.js is a library that provides a way to run code in a zone. It is used by Angular to implement change detection. It is also used by other libraries like RxJS and Angular Material.

A zone has five responsibilities, including intercepting asynchronous task scheduling and wrapping callbacks for error handling and zone tracking across async operations. Zone.js can create contexts that persist across asynchronous operations, as well as provide life cycle hooks for asynchronous operations.


- [Angular](https://angular.dev)
- [Zone.js](https://github.com/angular/angular/blob/main/packages/zone.js/lib/zone.ts).
- [Signals](https://github.com/angular/angular/discussions/49685)
- [Deferral views](https://blog.angular.io/introducing-angular-v17-4d7033312e4b), Angular v17.

----

In 2023, Next.js introduced a new app server to support _React Server Components (RSC)_ and _Server Actions_, while maintaining interoperability with the old app server. The goal is to ease the transition for developers who have been using Next.js for several years. In the coming year, the focus includes addressing issues such as simplifying _caching_ to enhance the developer experience. The team also plans to continue investing in performance improvements, including a new _compiler_ powered by Rust, aiming for faster startup times. The long-term vision involves building a foundation for the next decade of Next.js, with a new routing system seen as a key component.

----

In the upcoming year, the React team anticipates increased adoption of _React Server Components (RSC)_. RSCs have expanded the scope of React beyond just a UI layer, influencing the architecture of applications for better user and developer experiences, particularly in cases where single-page applications (SPAs) fell short. One notable advancement is _React Forget_, an auto-memoizing compiler, showcased at React Advanced. React Forget eliminates the need for developers to use useMemo and useCallback.

Additionally, at React Native EU, the team announced the integration of familiar Chrome dev tools into React Native starting in version 0.73. They also provided a glimpse into research on Static Hermes, a native compiler for JavaScript, with the potential to not only accelerate React Native applications but also redefine the effective use of JavaScript.

----

In August 2023, Tao Xin released VanJS, a minimalistic open-source UI framework built on vanilla JavaScript (VanJS stands for vanilla JavaScript). VanJS takes a simpler approach to development, incorporating reactivity without relying on React. It boasts an easy-to-use API, zero dependencies, and is designed for small to medium-scale applications, making it the world's smallest reactive UI framework.

VanJS allows developers to build personal websites or create Chrome extensions, presenting itself as an alternative to React and native GUI applications. It is comparable to Swift UI, used for iOS app development, and even older technologies like Objective C. The framework supports a modern developer experience by enabling a more declarative way of building UI.

VanJS eliminates the need for JSX syntax and traditional create-compile-deploy-test cycles. It runs directly in the browser, offering an immediate REPL (Read-Eval-Print Loop) experience for programmers. The framework supports states, state bindings, and automatic propagation of state changes to the UI, simplifying the process of updating the user interface during application logic development.

Notably, VanJS features an AI-powered chatbot called VanJS App Builder, designed to create pages with VanJS. This chatbot utilizes a custom GPT model, instructed to read tutorials and sample apps from the VanJS website, demonstrating the framework's adaptability and its compatibility with large language models (LLMs).

Developers can leverage VanJS by loading the library from the _CDN_ and typing application code directly into HTML files or by using _npm_ for better dependency management and bundling support. VanJS aims to streamline the development process while providing a lightweight and efficient alternative for building reactive user interfaces.

[VanJs](https://github.com/vanjs-org/van/discussions/179)

----

Stable diffusion is a deep learning text-to-image model based on diffusion. SD4J can be used, via the GUI or programmatically in Java applications, to generate images. SD4J runs on top of the ONNX Runtime, a cross platform inference and training machine learning accelerator.

- [SD4J](https://github.com/oracle-samples/sd4j)
- [ONNX](https://onnxruntime.ai/)
- [Stable diffusion](https://github.com/CompVis/stable-diffusion)
- [Git LFS](https://git-lfs.com/)

---

With Dapr's cloud-native abstraction model, architects can separate business logic from implementation details.

- [Dapr](https://dapr.io)
- [Architecture trends report 2023](https://www.infoq.com/podcasts/infoq-architecture-trends-report-2023/), InfoQ.

---

GitHub recently introduced _trace2receiver_, an open-source tool that integrates with OpenTelemetry to analyze Git performance data. This tool allows users to identify performance issues, detect early signs of trouble, and highlight areas where Git itself can be enhanced.

The process of collecting Git performance data: 
- As enterprises develop larger monorepos, the demand on Git for high performance, regardless of repository size, has increased. Effective monitoring tools are essential to assess Git's performance in real-world scenarios, beyond just simulated tests.
- _Trace2_ offers detailed performance data, but interpreting this complex information often requires additional visualization.
- The core of _OpenTelemetry_ includes a customizable collector service daemon, supporting various modules for data collection, processing, and export. The GitHub team developed an open-source component, trace2receiver which allows custom collectors to gather Git's _Trace2_ data, convert it to a standard format (like OTLP), and send it to visualization tools for analysis.

The _trace2receiver_ tool serves two main functions in collecting Git telemetry data. First, it allows for an in-depth analysis of individual Git commands, tracking the time spent on each step, including any nested child commands in what is termed a "distributed trace" by OpenTelemetry. Second, it facilitates the aggregation of data across various users and machines over time. This enables the calculation of summary metrics, like average command times, providing a comprehensive view of Git's performance on a larger scale. This data is crucial for identifying areas for improvement and understanding user frustrations with Git.

The _trace2receiver_ tool uses `child(...)` spans to track the time spent on each subprocess, whether it's a shell script or a helper Git command. This helps in identifying the actual duration of Git commands, distinguishing real processing time from waiting for user interaction.

Additionally, Microsoft's also introduced Git Partial Clone in Azure DevOps which shows a trend toward more efficient handling of large codebases.

- https://news.ycombinator.com/item?id=37955927
- https://www.infoq.com/news/2023/12/git-partial-clone-azure-devops/
- https://github.com/git-ecosystem/trace2receiver/blob/main/Docs/README.md

[Source](https://www.infoq.com/news/2023/12/git-perf-data-telemetry/)

----

OpenAI's research paper on GPT-3, published in 2020, showed how the model could perform a variety of natural language processing (NLP) tasks using few shot learning; essentially, by prompting the model with a description or examples of the task to be performed.

[Language models are few shot learners](https://openai.com/research/language-models-are-few-shot-learners)

OpenAI cookbook article contains several "techniques for improving reliability" of GPT-3's responses. 

- [Techniques to improve reliability](https://cookbook.openai.com/articles/techniques_to_improve_reliability)
- [Bibliography from the OpenAI cookbook](https://cookbook.openai.com/articles/techniques_to_improve_reliability#bibliography)

The OpenAPI guide lists six strategies for eliciting better responses from their GPT models, with a particular focus on examples for their latest version, GPT-4. Each of the strategies is broken down into a set of specific, actionable tactics with example prompts. Many of the tactics are based on results of LLM research, such as chain-of-thought prompting or recursive summarization.

- [Six strategies for getting better results](https://platform.openai.com/docs/guides/prompt-engineering/six-strategies-for-getting-better-results)
- [Chain of thought](https://en.wikipedia.org/wiki/Prompt_engineering#Chain-of-thought)
- [Recursive summarization](https://openai.com/research/summarizing-books)

The OpenAI's Chat completion API offers system message which helps in deciding the behavior of an assistant. It gives the model a persona for shaping its responses.

[System message from Chat completion API](https://platform.openai.com/docs/guides/text-generation/chat-completions-api)

Instead of asking the model to perform math calculations itself, it should instead generate Python code to do the calculation; the code would then be extracted from the model response and executed. Remember that the code the model produces is not guaranteed to be safe, and should only be executed in a sandbox.

Several other LLM providers have suggest their own prompt engineering tips. 

NOTE: different LLMs, responds differently. With the rapid advancement we're seeing, in two years or five, we might not even need such complex prompting as systems get smarter.

- [Advanced prompt engineering](https://learn.microsoft.com/en-us/azure/ai-services/openai/concepts/advanced-prompt-engineering), Azure AI services, Microsoft.
- [Prompt best practices](https://ai.google.dev/docs/prompt_best_practices), Gemini, Google

[Source](https://www.infoq.com/news/2023/12/openai-prompt-engineering/)

---

