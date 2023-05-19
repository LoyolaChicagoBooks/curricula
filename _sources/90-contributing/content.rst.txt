How to Contribute
=================

Anyone is welcome to contribute to this project as long as you meet some basic criteria.


Requirements
------------

- interest in ACM/IEEE curricular framework
- being in touch with modern computer science practice
- appreciation and understanding of open source culture
- GitHub account
- ORCID ID


Contribution process
--------------------

- fork a repo
- make pull requests
- attend in-person or virtual meetings to discuss next steps and other aspects of the project

.. todo:: Set up an issue template for contributors.


Sample tool stack
-----------------

- Visual Studio Code
- extensions: Esbonio by Swyddfa (comes up when searching for sphinx but not restructured), reStructuredText by Tatsuya (optional, for additional syntax-directed editing support with headings etc.)
- requires nonvirtual install of Python Sphinx and theme packages (unless you want to launch VS Code manually within a venv) - see requirements.txt in this repo
- the Esbonio language server will rebuild the html version very quickly upon save
- supports passive outline in explorer pane
- preview within VS Code works and refreshes quasi-instantly (but a bit suboptimal for long documents because it goes back to the top after each HTML rebuild)
- you can also see the local file path of the html in the output window in case you want to view it in an external browser
- optional Botrush Edge/Chrome browser extension for downloading ChatGPT sessions in varioius formats including Markdown
- pandoc for converting Markdown and other formats to reStructuredText

.. image:: images/vscode-rest.png


Possible chapter structure (GPT 3.5)
------------------------------------

When structuring a chapter in a computer science textbook for an ACM CS2 course, it is important to include several key structural elements to effectively present the material. Here's a suggested outline for each chapter:

1. Introduction:

   - Provide an overview of the chapter's topic and its relevance in computer science.
   - Explain the objectives and goals of the chapter.
   - Outline the main concepts or techniques that will be covered.

2. Motivation:

   - Present real-world examples or scenarios that illustrate the need for understanding the topic.
   - Explain why the topic is important in solving practical problems or advancing computer science knowledge.
   - Discuss the potential benefits or applications that can be achieved by mastering the topic.

3. Background:

   - Review any prerequisite knowledge or concepts necessary to understand the chapter's material.
   - Summarize related topics or theories that will be built upon or referenced in the chapter.
   - Provide references to previous chapters or external resources for further reading, if applicable.

4. Example:

   - Present a concrete example or case study that demonstrates the application of the topic.
   - Provide step-by-step explanations or code snippets to illustrate how the example works.
   - Discuss the insights gained from the example and highlight its relevance to the broader concepts covered in the chapter.

5. Details:

   - Explain the key concepts, algorithms, data structures, or techniques related to the chapter's topic.
   - Provide in-depth explanations, definitions, and formal descriptions as needed.
   - Include relevant equations, pseudocode, or code snippets to clarify the implementation details.
   - Offer proofs or derivations to support the understanding of the topic, if applicable.

6. Limitations:

   - Discuss the limitations or constraints associated with the topic or techniques covered.
   - Highlight scenarios or cases where the topic might not be applicable or might yield suboptimal results.
   - Address any assumptions made during the presentation of the topic and their potential implications.

7. Critical Discussion:

   - Encourage critical thinking and analysis of the topic by raising thought-provoking questions.
   - Discuss alternative approaches, variations, or related research that expands on the topic.
   - Present potential challenges or open problems within the field to stimulate further exploration.

8. Summary and Conclusion:

   - Recap the main points covered in the chapter.
   - Emphasize the key takeaways and insights gained from studying the topic.
   - Provide a concise summary of the chapter's content.
   - Preview the next chapter or suggest further resources for continued learning.

Additionally, each chapter should include exercises, programming assignments, or other hands-on activities to reinforce the understanding of the material. These exercises can vary in difficulty and cover different aspects of the chapter's topic.

Remember that this outline is a general guideline, and the specific structure may vary depending on the content and style of the textbook. Adapt it to suit your specific needs and the preferences of your intended audience.


Possible chapter structure (GPT 4)
----------------------------------

A well-structured textbook chapter should make it easy for students to understand the content and reinforce their learning. Here are some recommended structural elements:

1. **Chapter Title**: Clearly indicate the main topic or concept the chapter will cover.

2. **Learning Objectives**: List the key points or skills that students should understand or be able to do after reading the chapter.

3. **Introduction**: Provide a brief overview of the chapter's topic, why it's important, and how it fits into the larger context of the field.

4. **Motivation**: Explain why the topic is relevant. This could include real-world applications, historical context, or explanations of problems that the topic can solve.

5. **Background/Prerequisites**: Briefly review any prerequisite knowledge or skills that are necessary to understand the current chapter.

6. **Main Content**: Break down the topic into manageable sections and subsections. Each should focus on one aspect of the topic, explain it clearly, and provide relevant examples. This could include theoretical explanations, discussions of specific algorithms or data structures, or other core content.

7. **Illustrations, Diagrams, and Code Examples**: These provide visual or practical examples that can help students understand abstract concepts. Code examples are particularly important in a programming course.

8. **In-Text Questions/Activities**: These can help students check their understanding as they read. They could be simple comprehension questions, practice problems, or small coding exercises.

9. **Case Studies/Practical Applications**: Provide examples of how the concepts are used in practice. This could be a detailed walkthrough of a problem-solving process, or an exploration of a real-world case where these concepts were applied.

10. **Limitations and Challenges**: Discuss any known limitations or challenges with the topic. This can also include discussions about efficiency, trade-offs, or other real-world considerations.

11. **Critical Discussion or Analysis**: Provide a deeper or more theoretical discussion of the topic. This could include open problems, ongoing debates in the field, or advanced applications.

12. **Summary/Recap**: Briefly summarize the main points of the chapter, and tie them back to the learning objectives.

13. **Practice Problems/Exercises**: Provide a set of problems or exercises for students to complete. This can help them practice the skills they've learned and reinforce their understanding.

14. **Further Reading/Resources**: Suggest additional resources for students who want to learn more. This could include academic papers, online tutorials, or other textbooks.

15. **Glossary/Terms**: Define any new terminology that was introduced in the chapter.

Remember that the goal is to support students' understanding and learning, so the structure should be clear, logical, and as consistent as possible across different chapters.
