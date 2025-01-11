# ChatGPT Exploratory Prompting

This repository shares my beginner-level exploration of ChatGPT’s features and workflows. My interests span four broad areas: two focused on applications (_coding support and guidance_ and _technical and business writing assistance_) and two centered on technical aspects of routine ChatGPT use (_memory management_ and _meta-prompting_). To share my experiences, I use several content formats:

- Descriptive writing: Detailed explanations of processes and workflows.
- Instruction templates: Reusable ChatGPT templates for various tasks.
- Q&A collections: Curated prompts and ChatGPT answers focused on specific topics, intended for exploration and discovery.
- Workflow demonstrations: ChatGPT conversations applied to model problems, showcasing potential use cases.

All responses are based on the GPT-4o model and provided "as is," without critical evaluation unless explicitly stated otherwise. In Q&A collections, I approach ChatGPT as a tool for exploration rather than a source of definitive solutions. My objective is to surface overlooked considerations, transforming some of the "unknown unknowns" in ChatGPT workflows into "known unknowns."

This repository is a work in progress. Although some development occurs in the `dev` branch, I strive to update the `main` branch regularly. Content may evolve over time, and portions might appear incomplete or inconsistent.

## Highlights of My Experiments

- Developed prompt templates for revising technical text.
- Adapted style guides for several programming languages (Python, SQL, and VBA) to improve code consistency and quality.
- Explored approaches to active memory context management and guided meta-prompting for refining ChatGPT prompts.
- Analyzed semistructured data files to evaluate ChatGPT's ability to identify patterns and infer structure.
- Tested ChatGPT's intuition in interpreting data file formats with minimal context.
- Generated Python classes and methods based on serialized data formats and plain language descriptions.
- Assessed ChatGPT’s capability to interpret and transform data file formats into structured outputs.
- Developed workflows for iterative prompt improvement through guided experimentation.
- Implemented techniques for active memory context adjustments to improve response continuity and relevance.
- Refined ChatGPT’s outputs by providing targeted feedback to enhance clarity and precision.
- Examined how ChatGPT interprets ambiguous instructions or minimal data input.
- Utilized meta-prompting strategies to enhance prompt design for specific tasks.
- Collaborated with ChatGPT to create step-by-step guides and structured code walkthroughs.
- Discovered ChatGPT's ability to create well-structured and formatted technical workflow guides from unstructured descriptions.

## Model Problems

While simulating electrical circuits using a [SPICE][] circuit simulator, I selected two related model problems to explore ChatGPT's capabilities as a Python coding assistant.

### 1. SPICE Netlist Parser in Python

The SPICE [Netlist][] is a common plain-text format used by SPICE circuit simulators to describe electrical circuits. Modern simulators with graphical circuit editors, such as [LTspice][], can typically generate and utilize netlist files but often lack built-in support for converting these files into native circuit representations suitable for use in graphical editors. While several existing projects aim to parse SPICE netlists, I wanted to explore how ChatGPT could assist in developing a Python-based parser from scratch.

This exercise turned out to be a good instructive model problem for ChatGPT in a sense that the SPICE netlist file format is open source and sufficiently popular that there is no need to describe the format to ChatGPT as can be seen from the shared conversation. At this stage, I am sharing only the original ChatGPT [conversation][Netlist Parser]. In the future, I may convert this conversation into a tutorial when time permits.

### 2. LTspice Symbol and Circuit Parsers

A closely related problem involves creating parsers for the `*.asy` (symbol) and `*.asc` (circuit) plain-text file formats used by LTspice. Thus far, I have focused on `*.asy` file format, which stores vector graphical representation of circuit elements using a basic set of graphical primitives. This file format will serve as the primary demonstration target for now. Playing with the `*.asy` format in ChatGPT also proved to be quite instructive. While this time the file format is not open source, it is fairly intuitive, and is suitable, among other things, for probing ChapGPT's "intuition".

## Memory management

The baseline power of ChatGPT comes, of course, from the model training. On top of that, a crucial role in answer generation is played by the [memory context](https://help.openai.com/en/collections/8471548-memory). I do not have a clear understanding of what memory context actually includes, but I find it convenient to think of it as a set of bullet points collected / generated by ChatGPT while answering provided prompts. When a new ChatGPT account is created, ChatGPT uses just the model training to produce the answers, but later on memory context helps ChatGPT generate more tailored answers. Moreover, memory context facilitates handling complex topics, iterative refinement, and enables special prompting techniques.

Memory context consists of several components:
- **Temporary context** is derived from the contents of the current conversation and applies only to that specific interaction.  
  Using the prompt `Show me the temporary context for this chat and explain how I can modify it` should display its current state along with instructions for modification.
- **Persistent memory** is derived from the contents of all conversations and applies universally across interactions.  
  As of this writing (December 2024), persistent memory must be enabled in `Settings -> Personalization -> Memory`. Its current status can be checked using the prompt `Is persistent memory on?`. If persistent memory is enabled, the prompt `Show me persistent memory and explain how I can modify it` should display its contents along with instructions for modification. The same `Memory` menu includes a "Manage" button, which allows you to remove items from persistent memory. Additionally, the tab provides access to a sub-popup for [custom instructions](https://help.openai.com/en/articles/8096356-custom-instructions-for-chatgpt), which are also part of the persistent memory.

Note: The context displayed using the appropriate prompts or in the memory manager likely provides only a brief summary. The output may also vary if requests are repeated. Additionally, depending on the current context, ChatGPT may decline to answer these questions directly. For this reason, it is recommended to query ChatGPT about persistent memory from a new, blank chat (without any temporary context).

Basic memory-related prompts include
- `Is persistent memory on?`  
- `Show me persistent memory and explain how I can modify it`  
- `Show me the temporary context for this chat and explain how I can modify it`  

Separate pages include a [short tutorial][MemoryManagementDemo] and an [extended collection of prompts and answers][MemoryManagementQnA] related to memory management.

## Ask ChatGPT to help you generate, debug, and improve prompts

Since the relevance of ChatGPT responses heavily depends on the quality of prompts, and given ChatGPT’s strength in transformative and creative writing tasks, it seems natural to explore whether ChatGPT can improve its own prompts. The following resources offer some insights and tools for this purpose:

- **[Prompt Template][MetaPromptTemplate]**: A reusable template designed to refine and enhance prompts.
- **[Q&A on Prompt Engineering][MetaPromptingQnA]**: A helpful guide to prompt design and optimization topics.
- **[Demonstrations][MetaPromptDemo]**: Practical examples illustrating how ChatGPT can assist with generating and troubleshooting prompts.
## Writing assistance for efficient technical and business writing

Both my work and hobbies involve technical and business writing. The primary goal of non-fiction readers is typically to minimize the time spent reading while maximizing the amount and completeness of relevant information retrieved. Consequently, the efficiency of non-fiction texts heavily depends on their accessibility and clarity.  

ChatGPT performs reasonably well in enhancing the efficiency of non-fiction texts, even with basic prompts like "Convert the following text into standard English". However, using detailed and comprehensive instructions often leads to significantly improved results. Additionally, editing — whether for text or code — should always be viewed as an iterative process, akin to traditional writing, where drafts undergo multiple revisions and refinements. Well-structured instructions effectively drive ChatGPT, simplifying the overall revision process and targeted refinement of specific text aspects.

To streamline this refinement process, I have developed two documents:

- **Stylistic Guidelines** ([Writing Style Guidelines for Technical and Business Texts][WritingStyleGuidelines]):  
    These guidelines are designed to be provided directly to ChatGPT and focus on core aspects such as writing mechanics, structure, vocabulary, sentence construction, and overall coherence. They are applicable to most common non-fiction writing tasks.
    
- **Context Template** ([Writing Context Guidelines][WritingContext]):  
    This template offers customizable options for defining high-level writing parameters, including audience, domain, intent, formality, tone, and other contextual factors. It also allows for creating tailored "profile" contexts (e.g., "LinkedIn Post"), which can be included when submitting instructions to ChatGPT, enabling it to adapt to specific needs.    

While the above documents do not include examples, examples can be generated easily using appropriate prompts. For instance, a section from the [Writing Style Guidelines][WritingStyleGuidelines] can be copied and prefixed with a general instruction, for example:

<details>
<summary><b>ChatGPT Sample Prompt</b></summary>

```
I have a section from the writing style guidelines and need
three defective examples for each bullet point, along with
their corresponding corrected versions.

Structure lists and series with clear, parallel elements:
- Parallel Structure:  
    Ensure parallelism in:  
    - Lists and series  
    - Coordinating conjunctions (e.g., and, but, or)  
    - Correlative conjunctions (e.g., either...or, neither...nor)  
    - Comparisons (e.g., more than, as...as)  
    - Infinitive phrases (e.g., to increase, to improve)  
    - Gerund phrases (e.g., filing, answering)  
    - Verb tense within series  
    - Clauses within sentences
```
</details>


<!--
## Coding assistance

**TODO**
While ChatGPT is developed as a conversational tool that should be easily accessible to beginners, learning certain technical aspects may drastically improve the results, as evidenced by the emergence of the prompt engineering field.

Divide and conquer
Iterative focused refinement
Technical aspects for tailoring answers

Graphics analysis: vector or raster - interpret serialized file by comparing with graphical representation?
-->


<!-- References -->

[WritingStyleGuidelines]: https://github.com/pchemguy/ChatGPTExploratoryPrompting/blob/main/Writing/WritingStyleGuidelines.md
[WritingContext]: https://github.com/pchemguy/ChatGPTExploratoryPrompting/blob/main/Writing/WritingContext.md
[MemoryManagementQnA]: https://github.com/pchemguy/ChatGPTExploratoryPrompting/blob/main/Technical/MemoryManagementQnA.md
[MetaPromptingQnA]:https://github.com/pchemguy/ChatGPTExploratoryPrompting/blob/main/Technical/MetaPromptingQnA.md
[MetaPromptTemplate]: https://github.com/pchemguy/ChatGPTExploratoryPrompting/blob/main/Technical/MetaPromptTemplate.md
[MemoryManagementDemo]: https://github.com/pchemguy/ChatGPTExploratoryPrompting/blob/main/Technical/MemoryManagementDemo.md
[MetaPromptDemo]: https://github.com/pchemguy/ChatGPTExploratoryPrompting/blob/main/Technical/MetaPromptDemo.md
[SPICE]: https://en.wikipedia.org/wiki/SPICE
[Netlist]: https://en.wikipedia.org/wiki/Netlist
[LTspice]: https://en.wikipedia.org/wiki/LTspice
[Netlist Parser]: https://chatgpt.com/share/676e4884-0c64-8004-9ab9-b5e5eb2e60f4