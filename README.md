# AGENT-RULES
This repository improves software maintainability by persisting technical decisions made during the session. 

When you tell an agent - "Do not use this library, but rather use this"
                       -  "Do not link the source tree to my Makefile, but rather just the binary" 
                       -  "The unit for spacing should be in dp not px"

You are creating architecture decisions on the fly, and most times unconsciously - To ensure that these changes are not lost at the end of the session, they should be persisted to a RULES.md file which the model re-absorbs at the start of the next session.
This is good for software maintainability.

Integration of this feature is designed to be easy and compatible across harnesses - a "code-maintain" skill and it's corresponding SKILLS.md is added which the agent can pick up on. The maintain skill directs the agent to identify design decisions made during the session and persist it to the RULES.md file. It will also check if it's interpretation of any prompts contradicts the given project rules in RULES.md and either pick a solution that complies or point out that your intent clashes with pre-existing rules. The rules in question will be struck down or upheld based on the user's verdict.  

Another option is to include an instruction in AGENTS.md for the agent to identify design decisions made during the session and persist it in the RULES.md file for the project.
