# Navin
<CopilotTextarea />

Hooks
useCopilotReadable
useCopilotAction
useCopilotChat
useCopilotChatSuggestions

Classes
CopilotRuntime
CopilotTask
Example
Constructor Parameters
Contributing
Code Contributions
How To Contribute
Advanced: Package Linking
Documentation Contributions
Extras
Anonymous Telemetry
Reference
Classes
CopilotTask
CopilotTask
This class is used to execute one-off tasks, for example on button press. It can use the context available via useCopilotReadable and the actions provided by useCopilotAction, or you can provide your own context and actions.

Example
In the simplest case, use CopilotTask in the context of your app by giving it instructions on what to do.

import { CopilotTask, useCopilotContext } from "@copilotkit/react-core";
 
export function MyComponent() {
  const context = useCopilotContext();
 
  const task = new CopilotTask({
    instructions: "Set a random message",
    actions: [
      {
        name: "setMessage",
      description: "Set the message.",
      argumentAnnotations: [
        {
          name: "message",
          type: "string",
          description:
            "A message to display.",
          required: true,
        },
      ],
 
      implementation: async (message) => {
        // ...
      },
    }
    ]
  });
 
  const executeTask = async () => {
    await task.run(context, action);
  }
 
  return (
    <>
      <button onClick={executeTask}>
        Execute task
      </button>
    </>
  )
}
