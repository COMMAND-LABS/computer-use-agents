# TLDR

How to run a Containerized "Computer Use" Agent

## Notes

- Anthropic's original "Computer Use" Agent implementation
  - https://github.com/anthropics/anthropic-quickstarts

##

```sh
git clone https://github.com/anthropics/anthropic-quickstarts
ls
cd anthropic-quickstarts
ls
cd computer-use-demo
ls
code .
```

##

Needs to be ran inside the `computer-use-demo` project

```sh
./setup.sh
```

##

Needs to be ran inside the `computer-use-demo` project

```sh
docker build . -t computer-use-demo:local
export AGENTOPS_API_KEY=%your_api_key_here%
docker run \
  -e ANTHROPIC_API_KEY=$ANTHROPIC_API_KEY \
  -e AGENTOPS_API_KEY=$AGENTOPS_API_KEY \
  -v $(pwd)/computer_use_demo:/home/computeruse/computer_use_demo/ \
  -v $HOME/.anthropic:/home/computeruse/.anthropic \
  -p 5900:5900 \
  -p 8501:8501 \
  -p 6080:6080 \
  -p 8080:8080 \
  -it computer-use-demo:local
```

## 1st test prompt

```
Open the calculator and add 2 + 2
```

## How to add files and folders on your PC into the container

- create a folder called `scratch` in the `computer-use-demo` project
- add the `Example_AAA_Contract.pdf` file
- rerun the container...

```sh
docker run \
  -e ANTHROPIC_API_KEY=$ANTHROPIC_API_KEY \
  -e AGENTOPS_API_KEY=$AGENTOPS_API_KEY \
  -v $(pwd)/computer_use_demo:/home/computeruse/computer_use_demo/ \
  -v $HOME/.anthropic:/home/computeruse/.anthropic \
  -v $(pwd)/scratch:/home/computeruse/scratch \
  -p 5900:5900 \
  -p 8501:8501 \
  -p 6080:6080 \
  -p 8080:8080 \
  -it computer-use-demo:local
```

## 2nd test prompt

```
My name is Tad Duval, I’m sending a contract to a client named Leo Sanchez to set up a Containerized “Computer Use” Agent for him. I am based in Miami and Leo is based in Arizona. The price of the service is $1000 USD for setup plus an option of a monthly retainer of $1000 USD for up to 10 hours of additional modification work to the Agent. Copy and edit the template Example_AAA_Contract.pdf contract in $HOME/scratch folder to contain the details of the proposal. The anticipated start date is in a week on 11-23-2024. Store the final copy of the contract in the same folder as a pdf as well. The size of the final copy should be no more than 1.5 times the size of the template.
```

## Now let's add AgentOps

Add AgentOps as a dependency...

```computer_use_demo/requirements.txt
agentops
```

_OR IF COMPUTER USE TRACKING IS NOT YET RELEASED..._

```computer_use_demo/requirements.txt
agentops @ git+https://github.com/AgentOps-AI/agentops.git@anthropic-vision
```

then initialize AgentOps at the top of the streamlit.py...

```py
import agentops  # type: ignore
agentops.init(api_key=os.environ["AGENTOPS_API_KEY"])
```

```sh
docker build . -t computer-use-demo:local
export AGENTOPS_API_KEY=%your_api_key_here%
docker run \
    -e ANTHROPIC_API_KEY=$ANTHROPIC_API_KEY \
    -e AGENTOPS_API_KEY=$AGENTOPS_API_KEY \
    -v $(pwd)/computer_use_demo:/home/computeruse/computer_use_demo/ \
    -v $HOME/.anthropic:/home/computeruse/.anthropic \
    -v $(pwd)/scratch:/home/computeruse/scratch \
    -p 5900:5900 \
    -p 8501:8501 \
    -p 6080:6080 \
    -p 8080:8080 \
    -it computer-use-demo:local
```

## Test 2nd prompt again after AgentOps integration

```
My name is Tad Duval, I’m sending a contract to a client named Leo Sanchez to set up a Containerized “Computer Use” Agent for him. I am based in Miami and Leo is based in Arizona. The price of the service is $1000 USD for setup plus an option of a monthly retainer of $1000 USD for up to 10 hours of additional modification work to the Agent. Copy and edit the template Example_AAA_Contract.pdf contract in $HOME/scratch folder to contain the details of the proposal. The anticipated start date is in a week on 11-23-2024. Store the final copy of the contract in the same folder as a pdf as well. The size of the final copy should be no more than 1.5 times the size of the template.
```

## 🎉

And hopefully everything works smooth for you
