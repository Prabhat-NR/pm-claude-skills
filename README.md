# pm-claude-skills
This repo contains Claude skills that I have created to automate product management use cases


Setup required for users of your plugin:
Figma desktop app — The Figma desktop app must be open (not just the browser version).
Figma Desktop Bridge plugin — This is a Figma plugin that runs inside Figma and bridges communication between Claude and the Figma file. Users activate it from Figma via Plugins → Development → Figma Desktop Bridge. It enables all the figma_execute, figma_create_child, figma_set_fills, etc. calls that your skills use.
The figma-console MCP connector in Cowork — This is the MCP server on the Claude side that provides the Figma tools. It's what appears in the tool list as mcp__figma-console__figma_execute and the other figma_* tools.
