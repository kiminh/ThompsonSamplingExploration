
This framework allows to test several Bayesian Machine Learning models for exploration with Thompson Sampling in online advertising applications. All the models are implemented in PyTorch. 

## Main
Running a simulation:
```
python run_simulation.py --exp 2 --freq 10 --len_sim 2000 --n_ads_sel 100 --n_new_ads 1000 --agent dropoutNN
```
### args
```
--exp        - experiment number
--len_sim    - simulation length 
--n_ads_sel  - number of ads selected from the agent in each iteration
--n_new_ads  - number of ads shown to the agent in each iteration
--deep_gt    - True: ground truth from a neural network model; False: Logistic Regression model
--freq       - frequency of model updates
--agent      - select agent 
```

## Agent
The agent folder contains the code for each agent. Each agent has an underlying model, which given a context is able to select an action and update its internal model.

```
agents["bayesianNN"]            - Bayesian Neural Network with Stochastic Variational Inference
agents["bayesianLR-1"]          - Bayesian Logistic Regression
agents["bayesianLR-05"]         - Bayesian Logistic Regression with reduced weigh variance
agents["bayesianLR_exploit"]    - Greedy Bayesian Logistic Regression
agents["vanillaNN"]             - Greedy Neural Network
agents["dropoutNN"]             - Dropout Neural Network
agents["concretedropoutNN"]     - Concrete Dropout Neural Network (to be implemented)
agents["logisticLR"]            - Greedy Logistic Regression

```

## Simulator
Simulator.py acts as a controller, given an agent, it provides at each iteration a context, observe the action selected and generate a reward.

## Data
All the data needed can be downloaded [here](https://drive.google.com/open?id=1DEKMzuR-jlUpCDaZE4x0vtoQWgiirtR7) and should be put in the data folder.
