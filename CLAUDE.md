Agent operating principles:
- If you find that the appoach you're taking isn't working or is overcomplicated or is inappropriate, stop and think deep about the task you're trying to accomplish rather than immediately switching to a different approach.
- If you're not confident about something (you're not sure you've understood what I've asked, or you're not confident it would work), stop and ask me about it. Correctness is more important than how fast you implement it.
- When I ask you to do something, your first step should always be to formulate a plan with clear steps to reach the goal. Give me a short description of your plan and then get my confirmation before proceeding.
- Start with a plan that does the bare minimum to accomplish what I've asked. For any good ideas you have beyond the basics, ask me before adding them to the plan.
- If there's uncommitted work in the project, ask before proceeding.
- Maintain a CLAUDE.md file in every project. If one doesn't exist yet, create it.
- Write good code, even if it takes longer or is more work. Correctness trumps coding speed.
- When a test needs to be reworked due to changed functionality, first check that the test even makes sense or adds value anymore.

The principles of good code:
- It should be easily comprehensible to someone unfamiliar with the codebase. Naming and comments should guide the reader along so that they're not confused as to why parts of the code exist (the principle of least astonishment).
- Follow the best practices and idioms of the language/technology you're using.
- The choice of algorithm and architecture usually has a much bigger impact on performance than localized optimizations. Focus on the former, and avoid localized optimizations unless I ask for them.
- Keep the CLAUDE.md file in each project up to date as the project evolves.
- YAGNI: Don't add things that might be needed in future; focus on things that are actually needed now.
  - There's always a tension between YAGNI and flexible architecture. If you're unsure of how far to go on this, ask me.
- All functionality requires tests that verify its proper operation.
  - Architect in ways that make testing easier, but don't overcomplicate things.
- In general, a simpler solution is better.

The CLAUDE.md file in a project:
- It should exist at the root of a project.
- It should describe:
  - How it's architectured and why.
  - Any idiosyncrasies and how to deal with them.
  - How the components of the project fit together.
  - For each component:
    - Why it exists.
    - How it works.
    - What its responsibilities are.
  - Anything else that is important for an agent to know when working in this project.
- Avoid code examples in general unless it's really necessary in order to understand how things work.
- Whenever you gain new insights and understanding while working in a project, add them to the CLAUDE.md file.

Naming:
- Use names that enhance readability. High quality names reduce the need for comments.
- A class or struct name should help describe what its purpose is.
- A function or method name should describe what it does or describe the question it answers.
- A member name should fit its purpose in the class or struct.
- An instance name should describe its purpose in the algorithm.
- An iterator's name should start with the letter "i", followed by what it's iterating over (using camel or snake case depending on the coding standard).
- In general, names should describe "what", not "how" (otherwise you'd have to change the name whenever you changed how something worked).
  - The only exception to this is if you have a specialization of a more general concept where the "how" is important to understand the specialization.

Comments:
- Comments should be reserved for places where the implementation must be done in a non-obvious way (principle of least astonishment).
- Comments in an algorithm should focus on the "why" rather than the "how". A comment is a signal of intent so that when someone debugs the code, they know what you intended to accomplish.
- If the algorithm itself is complicated, then a comment describing how it works is appropriate.
- Do not include code examples in comments. They fall out-of-date too quickly.
- Comments must be checked regularly to ensure that they don't fall out of date with the code.
- Don't record history in the comments; that's what source code management software is for.
  - The only exception is for unusual code that is needed for historical reasons.
- If comments exist in the code already, assume that they might be important.
  - If you don't understand why a comment is there, ask.
  - Do not remove existing comments without my approval.
- Every source file should have a comment at or near the top (after any boilerplate header comment) that describes what its purpose is.
  - Each line of this comment should begin with "ABOUTME: " so that it can be grepped.
  - Keep these comment lines within 80 characters so that source code formatters don't break them.
