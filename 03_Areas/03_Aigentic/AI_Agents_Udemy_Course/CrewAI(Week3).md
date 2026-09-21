[[01_AI_Agents_Udemy_Course]]
#aigentic
Resources: Udemy - Master AI Agents in 30 days - week3
- **More structured than openAI** ... like your own railways: config files and stru
- crewai.com
- CreaAI open-source framework ... is the one we are using (there are some other options from crewAI)
- Two flavours:
	- **CrewAI Crews**: build your crews (the one we are using)
	- CrewAI Flows: high level orchrestation for your crews
# Terminology
## Agent
An **autonomus** unit with an **LLM**, a **role**, a **goal**, a **backstoyr**, **memory**, **tools**.
It is always a good practice to include **success criteria in the goal**.
**CrewAI unify** role, goal and backstory in a generated promt (they are good in builiding prompts)
## Task
A specific **assignment to be carried out** with a **description**, expected **output**, **agent**
## Crew 
A bunch a agents with a bunch of tasks.
**Is better to have a good task than a good agent**
Two ways of using it, 
- sequential> tasks in order they are defined
- hirearchical> use a Manager LLM to orchrestrate it
**CrewAI separates agents and tasks from the code** trough yml files: every crew project has the following files:
- agents.yml
- tasks.yml
- crew.py brings everything together
- main.py
# Set Up
- Install UV tool: `uv tool install crewai==1.14.4`
- To equip our agent with all the crew ai knolwedge: `npx skills add crewaiinc/skills`
- In the agents.yml, include llm: openai/gpt-5.4-mini for each agent along with role, backstory, and goal.
## agents.yml
Define the agents:
`debater:`
  `role: >`
    `A compelling debater`
  `goal: >`
    `Present a clear argument either in favor of or against the motion. The motion is: {motion}. You will be successful if a judge agrees with your argument.`
  `backstory: >`
    `You're an experienced debator with a knack for giving concise but convincing arguments.`
    `The motion is: {motion}`
  `llm: openai/gpt-5.4-mini`
  
  The things within **{}** are set to contain **variables** later define within the code.

## tasks.yml
Define the tasks:
`propose:`
  `description: >`
    `You are proposing the motion: {motion}.`
    `Come up with a clear argument in favor of the motion.`
    `Be very convincing.`
  `expected_output: >`
    `Your clear argument in favor of the motion, in a concise manner.`
  `agent: debater`
  `context:`
    `- research_task`  
  `output_file: output/propose.md`

- **IMPORTANT**: your information MUST be up to date and relevant to now, {current_date}.
- **One task, one agent**
- **context:** context bo be passed from another task. Forcing independecy between tasks, and sequential. If context is not especified, **all the outputs** from previous tasks are included within the context. It also force sequential run.
## crew.py
Here you define the @agent linking the class with the agent from the agents.yml ...
`@agent`
`def debater(self) -> Agent:`
	`return Agent(`
		`config=self.agents_config['debater'],`
		`verbose=True`
	`)`
  
  ... and you define te @task linking the class with the task from tasks.yml ...
`@task`
`def propose(self) -> Task:`
	`return Task(`
		`config=self.tasks_config['propose'],`
	`)`

## main.py
Define the inputs ...
`motion = input("Enter the motion: ")`
`inputs = {`
	`motion': motion,`
	`current_date': str(datetime.now().date())`
`}`

# Examples
Example stock_picker has very nice features:
- Structured output (from one task to the other) using pedantic.
- Memory.
- Own defined tools (pushover). Those are defined within a folder called "tools", with a @tool decorator.
- Se pasa de secuencial a gerárcico añadiendo:
	- manager en agents.yml (we can define it or not)
	- en crew.py:
	@crew
    def crew(self) -> Crew:
        **manager** = Agent(
            config=self.agents_config['manager'],
            allow_delegation=True
        )
        return Crew(
            agents=self.agents, # Automatically created by the @agent decorator
            tasks=self.tasks, # Automatically created by the @task decorator
            process=Process.**hierarchical**,
            verbose=True,
            tracing=True,
            memory=True,
            **manager_agent=manager**
        )
	
