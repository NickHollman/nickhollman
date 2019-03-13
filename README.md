# nickhollman

Mechanisms for Optimal Donor Coordination
Nick Hollman and Junlin Mo
CMPLXSYS 530
Computer Modeling of Complex Systems
Winter 2019

Goal
The goal of this model is to engineer a centralized coordination mechanism for donors that optimizes for agent preference satisfaction and charitable impact (positive externalities). More specifically, the model will attempt to optimize while avoiding strategic behavior between agents on a few levels of complexity, that include two representations of agent preferences: ordinal ranking and cost-effectiveness estimates.  
Justification
An approach that is well suited for solving this optimization problem is agent-based modeling (ABM). This is the case for a few reasons. For one, ABM can capture all the relevant characteristics of each agent that is involved with charitable giving (e.g., strategy, preferences, donation amount, cost-effectiveness estimates.). In particular, agents will interact with each other based on the coordination mechanism and their individual strategy. Agent’s characteristics and simple rules act as the micro-level process of the model. Additionally, an ABM allows for an iterative process of agent interactions where their information and decision-making is limited by those around them in a network or neighborhood. An ABM would also effectively track the macro-level outcomes of this process that are preference satisfaction and positive externalities of the charities.
Main Micro-level Processes and Macro-level Dynamics of Interest
The micro-level processes mainly include agent characteristics, namely strategies and rules of interaction. In some cases, the micro-level process will be the interactions between the agents on a network through an iterative process. Agents would then have access to information about donation amounts and preferences of their immediate neighbors or other agents they have connections with in a network. The macro-level outcomes are agent preference satisfaction and positive externalities, namely charitable impact. The macro-level outcomes will come in the form of coordination emerging from agent strategies, interactions, and network structure. 
 
 
Model Outline

1) Environment
Description of the environment in your model. 
The environment consists of a 1D network. There is no interaction with the environment.
2) Agents
Description of the "agents" in the system.
 Class_Donors (n)
Donation amount drawn from fat tail distribution, which will be more, less, or equal to the sum of charity funding gaps
Preferences 
Random if ordinal rankings
Drawn from normal distribution if cost effectiveness estimates.
 Strategy/mechanism
Waiting out or being strategic with knowledge of others preferences
Blind donation or ignore other agents information
Total coordination that satisfies preferences equally
Wisdom of the crowd through one iteration
Wisdom of the crowd through multiple iterations in a network
Preference satisfaction 
Linked to funding gaps being fulfilled
Info from network connections
Info on preferences
Info on donation amounts
 
Class_Charities (3)
·      Funding Gap (Drawn arbitrarily from range [x, y])

Agent (Donor) procedures:
Initialize
Assigns above variables values, rankings, or strategies
Donate
According to their strategy or mechanism, agents donate some amount to a charity (or number of charities)
Communicate with connections
While agents are connected on a network, they will have the chance to obtain knowledge of other agents variables that will dictate their donation decision.
Agent (Charity) variables:
Funding gap
This model will include two agents: charities and donors, each with their own distinct variables and procedures. Agents will include the following variables: donation amount, preferences (either ordinal or cost effectiveness estimates), preference satisfaction level, and strategy (depending on the version). Donation amount for each agent will be drawn from a fat-tail distribution to mirror real donors. Many donors donate a moderate amount where few donors donate a large amount. Preferences will be randomly assigned to each agent. Preference satisfaction is based on how well each charity is funded. Agent strategies depend on the version of the model and the specified coordination mechanism. In addition to strategies, all agents will engage in the giving period in which all donations are allocated to the coordination mechanism and distributed to charities accordingly. The coordination mechanism is not an agent itself but rather an underlying algorithm for binding the micro-level dynamics of agent characteristics and macro-level outcomes of coordination and charitable impact. Charities will include the variable of a funding gap. Finding gaps are draw randomly from a predefined range.
3) Action and Interaction
Interaction Topology
Description of the topology of who interacts with whom in the system. 
When preferences are represented as cost effectiveness estimates, this model is best visualized as a network. All agents have at least one connection with another agent in the network. Agents, when acting on their procedures, may only obtain information from their immediate connections.
Action Sequence
What does an agent, cell, etc. do on a given turn? 
Initialize variables for charities and donors (assign funding gaps, donation amount, strategy)
Depending on the model variation, agents check their strategy or the overall mechanism and donate accordingly. 
In the case of the extension of the network variation. Agents interact with their connections in the network obtaining information on preferences and donation amount to dictate their donation decision and strategy.
Agents update the following variables: preference satisfaction, donation amount, and network connections. 
 
4) Model Parameters and Initialization
Describe and list any global parameters you will be applying in your model.
Describe how your model will be initialized
Provide a high level, step-by-step description of your schedule during each "tick" of the model
Global variables: 
Average agent preference satisfaction/charity funding gap
Global cost effectiveness estimates (via wisdom of the crowd)
Initialization of agents:

 Class_Donors (n)
·      Donation amount (From fat-tail), more, less or equal than sum of charity funding gaps
·      Preferences (cost-effectiveness estimate ranking, drawn from normal dist)
·      Strategy 
·      Preference satisfaction 
 
Class_Charities
·      Funding Gap (Drawn arbitrarily from range [x, y])
 

Model variation 1: Preferences as ordinal rankings
After initialization, at each tick, the donations will be allocated according to the coordination mechanism/agent rule set. At the start of a new tick each agent receives the same donation amount that they have been assigned during initialization. The donation amounts are “annually” refreshed at each tick as they can be thought of being part of the agent’s budget. At this point, agents donate their amount based on which strategy/mechanism is enacted. Strategies vary from ‘waiting out’, ‘blind’ donation and uncoordinated efforts more generally to complete compromise and coordination between non-strategic agents. Depending on how the donations are allocated, agents update their preference satisfaction which is linked to how well each charity is funded. Agent preferences stay constant but satisfaction changes over time. The funding gap for each charity is assigned randomly at each tick. 
Model variation 2: Preferences as cost effectiveness estimates
	Representing preferences as cost effectiveness estimates adds more complexity to the model. For one, the dynamics now include wisdom of the crowd from collective interactions and a network structure where agents estimates are influenced by immediate connections. In this model, initialization includes the same variable assignment as the initial version with the addition of the generation of a network structure and thus relations between agents. Following, a global cost effectiveness estimate is generated through an average of all agents individual estimates (wisdom of the crowd). The agents donations are then allocated such that priority is given to the most effective charity. This step produces two updated outcomes of interest: (1) agent’s individual preference satisfaction towards the donation allocation and (2) the positive externalities that are tied to funding effective charities. 
	In a further variation of this model, agents are situated in a network where they are initialized with random number of connections to other agents. The same process occurs of agents estimates being averaged, yet this happens at a local level. That is, at each tick, agents update their own estimates based on an average with only their immediate connections. This occurs simultaneously such that over time, the individual averages converge for each charity. Following, the agents donations are allocated such that priority is given to the most effective charity. Again, the two outcomes of preference satisfaction and charitable impact are measured. The hope is that the outcomes produced by this variation are more evenly balanced than the variation lacking a network structure. 
 
5) Assessment and Outcome Measures
What quantitative metrics and/or qualitative features will you use to assess your model outcomes?
In the initial model where agent preferences are represented ordinally, there will be primarily one outcome to measure: agent preference satisfaction. The outcome of agent preference satisfaction is directly linked with how well funded each charity is after each iteration. In this version of the model, an ideal outcomes looks like all agents preferences are equally satisfied. In the extended model where agent preferences are represented as cost effectiveness estimates, an addition outcome will be measured: the positive externalities of the charities. In the case of the extended model with cost effectiveness estimates, an ideal outcome would be one where the positive externalities of the charities are evenly balanced with the preference satisfaction of the agents.
6) Parameter Sweep
Parameter sweep:
Range of funding gaps between charities. Possible range of $100 - 2000 dependent on sum of agents donation amount.
How much money each agent has to donate. This will be pulled from a fat tail distribution but the range of the distribution will be swept. In particular the sweep will go through scenarios where the agents sum of donation amount is equal to, less than, and greater than the sum of the charities funding gaps.
Cost effectiveness estimates for charitable impact. These estimates will be drawn from a normal distribution where the range will be swept.
Number of agents, n. This variable will likely fall in the range of 5 - 20.

Sweeping the above parameters will allow for testing any interdependencies between variables especially donor amounts and its relation (=, >, <) to the funding gap.


