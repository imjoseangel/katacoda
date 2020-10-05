# Definition

A class or module should have one, and only one, reason to change. If a class has more than one responsibility, it becomes coupled. A change to one responsibility results to modification of the other responsibility.

## Bad Code Example

<pre class="file">
class Animal:
    def __init__(self, name: str):
        self.name = name

    def get_name(self) -> str:
        return f'My name is: {self.name}'

    def save(self, animal):
        pass


animal = Animal('Lion')
animal.save(animal)
</pre>

## Clone Example

Clone the example repository with the command `git clone https://github.com/imjoseangel/pythonsolid.git katacoda-solid-examples`{{execute}}

Within the root of a repository, the examples are under a directory called `examples`. Open the *Bad Code Example* `katacoda-solid-examples/examples/bad/01_singleresponsibility/example01.py`{{open}}.

Within the JSON file, the courses element defines each scenario. For example:

<pre class="file">
{
    "course_id": "uilayout-terminal",
    "title": "Scenario with Terminal UI",
    "description": "Katacoda Scenario Example"
},
</pre>

The **course_id** is the scenario name directory within the course directory. For example `ls katacoda-scenario-examples/uilayouts/uilayout-terminal`{{execute}}. The **title** and **description** are shown on the course page.
