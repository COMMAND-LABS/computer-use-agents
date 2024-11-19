# TLDR

How to run a "Computer Use" Agent directly on a Mac

## Notes

- We are going to test out Deedy's "mac_computer_use" implementation
  - https://github.com/deedy/mac_computer_use
  - https://debarghyadas.com/

## Interesting links for reference

- https://www.anthropic.com/rsp-updates
- https://en.wikipedia.org/wiki/Anthropic
- https://www.anthropic.com/news/developing-computer-use
- https://www.anthropic.com/news/announcing-our-updated-responsible-scaling-policy
- https://www.anthropic.com/news/3-5-models-and-computer-use
- https://os-world.github.io/
- https://ai.meta.com/blog/llama-3-2-connect-2024-vision-edge-mobile-devices/

##

```sh
git clone git@github.com:deedy/mac_computer_use.git
cd mac_computer_use
code .
./setup.sh
source activate.sh
clear
mv streamlit.py streamlit_app.py
streamlit run streamlit_app.py
```

## Test prompt

```
Write the text "Hello" to a new called hello.txt on a's Desktop. a is the Mac user running this prompt.
```

## If you'd like to develop the source code of a "Computer Use" Agent, here is an amazing fork

- https://github.com/AgentOps-AI/dockerized-anthropic-vision-agent