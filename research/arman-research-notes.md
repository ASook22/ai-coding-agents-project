# Research Notes: AI Coding Agents — Demonstration and Implications

**Prepared by:** Arman  
**Project:** AI Coding Agents  
**Presentation section:** Demonstration and Implications  
**Estimated speaking time:** 35 seconds

## 1. Research question

How can AI coding agents help software developers, and why must developers still review and test AI-generated code?

## 2. How AI coding agents work

AI coding assistants can explain existing code, suggest solutions, generate code, and help create tests. More autonomous agents can use tools to inspect files, make edits, and run commands, depending on their configuration and permissions.

For the demonstration, the AI assistant will be asked to identify a Python bug, explain its cause, propose a correction, and create a test.

**Sources:**

- Google for Developers — [Chat with Gemini Code Assist](https://developers.google.com/gemini-code-assist/docs/chat-gemini-standard-enterprise)
- GitHub Docs — [Using agent mode in your IDE](https://docs.github.com/en/copilot/how-tos/copilot-in-your-ide/use-copilot-agents/use-agent-mode)
- OpenAI — [Agents API documentation](https://developers.openai.com/api/docs/guides/agents-api/overview)

These sources describe real capabilities of coding assistants and agents. The precise capabilities depend on the product and its permissions.

## 3. Benefits: productivity and debugging

AI coding assistants can help developers understand unfamiliar code, identify possible bugs, and produce code or tests more quickly.

A controlled experiment by Peng and colleagues, published in 2023, studied developers implementing an HTTP server in JavaScript. Participants with access to GitHub Copilot completed the task 55.8% faster than the control group.

**Research source:**

Peng, S., Kalliamvakou, E., Cihon, P., & Demirer, M. (2023). *The Impact of AI on Developer Productivity: Evidence from GitHub Copilot.*

https://arxiv.org/abs/2302.06590

**Important limitation:** This result came from a particular programming task under experimental conditions. It does not mean AI makes every developer or every project 55.8% faster.

## 4. Risks: incorrect code and verification

AI-generated code can be incorrect, incomplete, or unsuitable for the surrounding project. A suggested fix can appear reasonable without handling all edge cases.

The National Institute of Standards and Technology (NIST) provides guidance on secure software development practices for generative AI. Its recommendations support using established development processes and security checks rather than accepting generated output without verification.

**Source:**

National Institute of Standards and Technology. (2024). *Secure Software Development Practices for Generative AI and Dual-Use Foundation Models: An SSDF Community Profile.*

https://csrc.nist.gov/pubs/sp/800/218/a/final

A separate randomized controlled trial by researchers at METR examined 16 experienced open-source developers completing 246 tasks in mature projects. In that specific 2025 study, allowing AI tools increased task completion time by 19%, despite developers expecting a productivity improvement.

**Research source:**

Becker, J., Rush, N., Barnes, B., & Rein, D. (2025). *Measuring the Impact of Early-2025 AI on Experienced Open-Source Developer Productivity.*

https://arxiv.org/abs/2507.09089

**Important limitation:** This study involved a small group of experienced developers working in codebases they already knew. It should not be generalized to every developer, task, or newer AI tool. Together, these studies show why productivity depends on the task and context.

## 5. Demonstration plan

### Example Python program

```python
def average(numbers):
    return sum(numbers) / len(numbers)

print(average([]))
```

**Problem:** When the list is empty, `len(numbers)` equals zero. The function attempts to divide by zero and raises a `ZeroDivisionError`.

### Prompt for the AI assistant

> Find the bug in this Python function, explain the problem, fix it, and write a simple test to verify the fix. The function crashes when given an empty list. Suggest a safe fix.

### What to observe

1. Does the assistant identify the division-by-zero problem?
2. Does it suggest a clear way to handle an empty list?
3. Does it generate a useful test?
4. Does the proposed solution pass the test when actually run?

One possible approach is to raise a clear `ValueError` for an empty list, or return a documented alternative if that is what the application requires. The best choice depends on the program's requirements.

The demonstration should distinguish between a suggested fix and a fix that has actually been applied and tested.

## 6. Implications for software development

AI coding agents can support debugging, code generation, and testing, but they do not remove the need for software engineering judgment.

Developers should:
- Review generated changes.
- Test normal inputs and edge cases.
- Check security and correctness.
- Understand the proposed solution before accepting it.

The main implication is that AI can assist with development, but the quality of the final software still depends on appropriate review and verification.

## 7. Conclusion

AI coding agents can help developers with programming tasks, but their benefits are not guaranteed in every situation. My demonstration illustrates both their usefulness and their limitations: the assistant can propose a solution, while the developer remains responsible for checking that the solution works.

## References

1. Google for Developers. [Chat with Gemini Code Assist](https://developers.google.com/gemini-code-assist/docs/chat-gemini-standard-enterprise)
2. GitHub Docs. [Using agent mode in your IDE](https://docs.github.com/en/copilot/how-tos/copilot-in-your-ide/use-copilot-agents/use-agent-mode)
3. OpenAI. [Agents API documentation](https://developers.openai.com/api/docs/guides/agents-api/overview)
4. Peng, S. et al. (2023). [The Impact of AI on Developer Productivity: Evidence from GitHub Copilot](https://arxiv.org/abs/2302.06590)
5. NIST. (2024). [Secure Software Development Practices for Generative AI and Dual-Use Foundation Models](https://csrc.nist.gov/pubs/sp/800/218/a/final)
6. Becker, J. et al. (2025). [Measuring the Impact of Early-2025 AI on Experienced Open-Source Developer Productivity](https://arxiv.org/abs/2507.09089)