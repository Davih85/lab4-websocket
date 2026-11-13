# Lab 4 WebSocket -- Project Report

## What I specified

I will send: **"Because it rains I play league"** to the server and 
I expect the doctor to reply: **"Is that the real reason?"**.

## What I changed

I only modified the test file `src/test/kotlin/websockets/ElizaServerTest.kt`.
I removed the `@Disabled` annotation, removed unused imports to pass Ktlint, captured the list size into a local variable, and added the assertions. 
I also implemented the `onMessage` to send the test sentence when the welcome sequence finishes.

## Technical decisions

**Why this sentence and answer?**

To avoid a flaky test, I need a keyword whose list of responses has only one element. 
In my sentence I used `"because"` because the list for `"because"` contains one answer: `"Is that the real reason?"`. 
Therefore, the random choice is deterministic.


**What I rejected:**
- `"I feel sad"` or `"I am tired"`: These match `"i feel"` and `"i am"`, which have 4 random responses.
- `"My mother is sad"`: It matches `"mother"`, which has 3 responses.
- `"I always feel sad"`: The word `"always"` is checked before `"i feel"` so it overrides it.

## How I verified

1. Ran `./gradlew test` to execute `onOpen` and `onChat` and both passed.
2. Ran `./gradlew ktlintFormat` and `./gradlew ktlintCheck` to ensure the code follows the style guidelines.
3. Ran `./gradlew check` and passed.
4. Performed manual verification by running `./gradlew bootRun` and connecting to `ws://localhost:8080/eliza` via Postman.

## AI disclosure


- **Tools / skills:** Deepseek used as an assistive tool.
- **Purpose:** Understanding concepts
- **Representative prompts:** "Que es el latch? explicame como funciona y en que afecta"
- **Affected files/sections:**  None. The assistant was used only to understand the concepts.
- **Validation steps:** I ran ./gradlew test, ./gradlew ktlintFormat, ./gradlew ktlintCheck and ./gradlew check and all passed
- **Citations:** None
- **Human-reviewed:**  I understood the concepts and applied them on the line codes

