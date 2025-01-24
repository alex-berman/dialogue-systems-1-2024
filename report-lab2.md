# Lab II: Report
## Limitations
1. **Re-raise question after irrelevant user response**: When the system has asked a slot question (e.g. "Who are you meeting with?"), and the user has said something that the system does not understand as an answer (e.g. "ten"), the system says "Sorry, I didn't understand." However, it does not re-raise the question. As a potential improvement, it might be good if the system re-raises the question.
2. **Over-answering**: If the user answers a question (e.g. "Who are you meeting with?") with more information than the system asked for (e.g. "Alex on Monday"), the system doesn't understand. Improvement: Support over-answering, i.e. detect multiple entities in input, accept answers to not-yet-asked questions, and do not ask for information that is already grounded.
3. **Clarification requests from system**: If the ASR's confidence is weak, it might be appropriate to request a clarification from the user, e.g. "Alex Berman, is that correct?"

## Improvements

1. Solved simply be replacing SPEAK_COMPLETE transition targets in nomatch states from Listen to Prompt.
2. Solved as follows: In all slot states, any potential form entity is detected and stored in context, rather than only a single slot-specific entity. Furthermore, on entry to slot states, I check if a value for the current slot is already in context; if so, a "jump_to" event is fired instead of speaking the prompt. Each such jump_to event is associated with a transition to the respective slot state. Unfortunately, I had to define one jump_to event for each slot. There might be a more elegant solution for this.

(I did not approach limitation #3, such #2 was quite substantial.)