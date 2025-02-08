# Research-agent
from groq import Groq

client = Groq()
completion = client.chat.completions.create(
    model="llama-3.3-70b-versatile",
    messages=[
        {
            "role": "user",
            "content": "i want make a class for Research Agent\n"
        },
        {
            "role": "assistant",
            "content": "**Research Agent Class**\n==========================\n\nBelow is a Python implementation of a Research Agent class:\n\n```python\nclass ResearchAgent:\n    \"\"\"\n    A class representing a Research Agent.\n\n    Attributes:\n        name (str): The name of the research agent.\n        expertise (list): A list of areas where the research agent has expertise.\n        projects (list): A list of projects the research agent is working on.\n    \"\"\"\n\n    def __init__(self, name, expertise=None, projects=None):\n        \"\"\"\n        Initializes a ResearchAgent object.\n\n        Args:\n            name (str): The name of the research agent.\n            expertise (list, optional): A list of areas where the research agent has expertise. Defaults to None.\n            projects (list, optional): A list of projects the research agent is working on. Defaults to None.\n        \"\"\"\n        self.name = name\n        self.expertise = expertise if expertise is not None else []\n        self.projects = projects if projects is not None else []\n\n    def add_expertise(self, area):\n        \"\"\"\n        Adds a new area of expertise to the research agent.\n\n        Args:\n            area (str): The area of expertise to add.\n        \"\"\"\n        self.expertise.append(area)\n\n    def remove_expertise(self, area):\n        \"\"\"\n        Removes an area of expertise from the research agent.\n\n        Args:\n            area (str): The area of expertise to remove.\n        \"\"\"\n        if area in self.expertise:\n            self.expertise.remove(area)\n\n    def add_project(self, project):\n        \"\"\"\n        Adds a new project to the research agent.\n\n        Args:\n            project (str): The project to add.\n        \"\"\"\n        self.projects.append(project)\n\n    def remove_project(self, project):\n        \"\"\"\n        Removes a project from the research agent.\n\n        Args:\n            project (str): The project to remove.\n        \"\"\"\n        if project in self.projects:\n            self.projects.remove(project)\n\n    def display_info(self):\n        \"\"\"\n        Displays information about the research agent.\n        \"\"\"\n        print(f\"Name: {self.name}\")\n        print(f\"Expertise: {', '.join(self.expertise)}\")\n        print(f\"Projects: {', '.join(self.projects)}\")\n\n\n# Example usage\nif __name__ == \"__main__\":\n    agent = ResearchAgent(\"John Doe\", [\"Machine Learning\", \"Data Science\"], [\"Project Alpha\", \"Project Beta\"])\n    agent.display_info()\n\n    agent.add_expertise(\"Natural Language Processing\")\n    agent.add_project(\"Project Gamma\")\n\n    print(\"\\nUpdated Info:\")\n    agent.display_info()\n\n    agent.remove_expertise(\"Machine Learning\")\n    agent.remove_project(\"Project Alpha\")\n\n    print(\"\\nUpdated Info:\")\n    agent.display_info()\n```\n\nThis class includes the following attributes and methods:\n\n*   **Attributes:**\n    *   `name`: The name of the research agent.\n    *   `expertise`: A list of areas where the research agent has expertise.\n    *   `projects`: A list of projects the research agent is working on.\n*   **Methods:**\n    *   `__init__`: Initializes a ResearchAgent object with the given name, expertise, and projects.\n    *   `add_expertise`: Adds a new area of expertise to the research agent.\n    *   `remove_expertise`: Removes an area of expertise from the research agent.\n    *   `add_project`: Adds a new project to the research agent.\n    *   `remove_project`: Removes a project from the research agent.\n    *   `display_info`: Displays information about the research agent.\n\nThe example usage demonstrates how to create a ResearchAgent object, display its information, add and remove expertise and projects, and update the information accordingly."
        }
    ],
    temperature=1,
    max_completion_tokens=1024,
    top_p=1,
    stream=True,
    stop=None,
)

for chunk in completion:
    print(chunk.choices[0].delta.content or "", end="")
