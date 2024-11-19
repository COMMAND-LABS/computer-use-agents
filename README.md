# TLDR

Code and resources for "Computer Use Agents DEEP DIVE WITH AGENTOPS" video

> [!CAUTION]
> Computer use is a beta feature. Please be aware that computer use poses unique risks that are distinct from standard API features or chat interfaces. These risks are heightened when using computer use to interact with the internet. To minimize risks, consider taking precautions such as:
>
> 1. Use a dedicated virtual machine or container with minimal privileges to prevent direct system attacks or accidents.
> 2. Avoid giving the model access to sensitive data, such as account login information, to prevent information theft.
> 3. Limit internet access to an allowlist of domains to reduce exposure to malicious content.
> 4. Ask a human to confirm decisions that may result in meaningful real-world consequences as well as any tasks requiring affirmative consent, such as accepting cookies, executing financial transactions, or agreeing to terms of service.
>
> In some circumstances, Claude will follow commands found in content even if it conflicts with the user's instructions. For example, instructions on webpages or contained in images may override user instructions or cause Claude to make mistakes. We suggest taking precautions to isolate Claude from sensitive data and actions to avoid risks related to prompt injection.
>
> Finally, please inform end users of relevant risks and obtain their consent prior to enabling computer use in your own products.

## Table of contents

- Part 1 - How to run a Containerized "Computer Use" Agent
  - Check out part_1.md
- Part 2 - How to run a "Computer Use" Agent directly on a Mac
  - Check out part_2.md

## Prerequisites

- Laptop or Desktop
- Docker
  - https://www.docker.com
  - and download the appropriate version for your machine
- VSCode
  - https://code.visualstudio.com
  - and download the appropriate version for your machine
- Familiarity with .git
  - https://git-scm.com
- An Anthropic API key
  - https://console.anthropic.com
- An AgentOps API key
  - https://app.agentops.ai
