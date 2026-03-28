  
**GETTING STARTED GUIDE**

**Product Shaping Plugin**

for Claude Desktop (Cowork Mode)

**Author:** Prabhat Ramesh

**Version:** 1.2.0

**Repository:** [github.com/Prabhat-NR/pm-claude-skills](https://github.com/Prabhat-NR/pm-claude-skills)

This guide walks you through downloading, installing, and using the Product Shaping plugin in Claude Desktop’s Cowork mode. No prior experience with plugins is required.

# **Contents**

1\. What Is the Product Shaping Plugin?

2\. Prerequisites: Setting Up Figma

3\. Downloading the Plugin

4\. Installing the Plugin in Claude Desktop

5\. Using the Skills

6\. Troubleshooting

# **1\. What Is the Product Shaping Plugin?**

The Product Shaping plugin gives Claude two powerful product management skills that work together to help you go from a loose collection of user stories to a fully mapped, risk-assessed delivery plan. Both skills output their results directly into Figma, so your team can collaborate on the artifacts visually.

## **Skill 1: User Story Map**

The User Story Map skill takes your user stories, epics, or feature descriptions and organizes them into a structured story map. It arranges work along two dimensions: horizontally across the user’s journey (Activities and Steps) and vertically by priority (Release 1, 2, 3+). The output is a four-layer hierarchy:

* **Activities** — The big goals the user is trying to accomplish (e.g., “Purchase a product”)

* **Steps** — Specific actions within each activity (e.g., “Complete payment”)

* **Stories** — User stories describing what the user needs, with release-tier color coding

* **Requirements** — Functional (FR) and non-functional (NFR) specifications that define “done” for each story

The skill also identifies gaps in your stories — missing steps in the journey, unaddressed security or accessibility concerns, activities without a Release 1 story — and fills them with clearly marked “\[Gap\]” stories so your map is always complete and actionable.

The entire map is built in Figma using nested auto-layout frames, which means you can add, remove, reorder, and edit any element and the layout reflows automatically.

## **Skill 2: Identify Product Risks**

The Identify Product Risks skill analyzes your story map (or a product description) and produces a structured risk register using Teresa Torres’ five-risk framework from Continuous Discovery Habits:

| Risk Category | Core Question | What It Covers |
| :---- | :---- | :---- |
| **Value** | *Will customers want this?* | Unvalidated assumptions, weak problem-solution fit, features users don’t need |
| **Usability** | *Can users figure it out?* | Complex flows, missing onboarding, cognitive overload, poor error recovery |
| **Feasibility** | *Can we build it?* | Unproven tech, tight timelines, missing skills, complex integrations |
| **Viability** | *Does it work for the business?* | Regulatory gaps, unsustainable costs, missing monetization, legal exposure |
| **Ethics** | *Should we build it?* | Data consent issues, bias, dark patterns, accessibility exclusion |

Each risk is scored on likelihood and impact, given a severity rating (Severe, High, Medium, Low), and paired with a concrete mitigation strategy. The risk register is also written back into your Figma file as a dedicated page, keeping it co-located with the story map.

| Important: Recommended Workflow Always create the story map first using the User Story Map skill, then use that completed map as the input to the Identify Product Risks skill. The risk skill reads directly from your Figma story map, which gives it richer context and allows it to trace every risk back to a specific story, requirement, or gap. |
| :---- |

# **2\. Prerequisites: Setting Up Figma**

Both skills in this plugin output their results to Figma. Before you can use either skill, you need to have Figma set up with the Desktop Bridge plugin running. Here’s how:

### **What You Need**

* A Figma account (free or paid)

* The Figma desktop app installed on your computer

* A Figma Design file open (not FigJam)

### **Setting Up the Figma Desktop Bridge**

The Figma Desktop Bridge is a plugin that allows Claude to communicate with your Figma file. Without it, Claude cannot read from or write to your designs.

1. **Open Figma Desktop** and create a new Design file (or open an existing one). Make sure it is a **Figma Design** file, not a FigJam board.

2. **Open the Plugin Menu.** In the Figma toolbar, go to **Plugins → Development → Figma Desktop Bridge**. If you don’t see it listed, you may need to install it from the Figma Community first.

3. **Run the Plugin.** Click on Figma Desktop Bridge to launch it. A small plugin window will appear — keep this open. The plugin must be running the entire time you use the Product Shaping skills.

4. **Keep the correct page active.** When Claude builds the story map, it creates a new page in your Figma file. When you later run the risk assessment, make sure the story map page is the active (visible) page in Figma.

| Tip If Claude reports that it cannot connect to Figma, the most common fix is to re-open the Desktop Bridge plugin. Go to Plugins → Development → Figma Desktop Bridge and click it again. |
| :---- |

# **3\. Downloading the Plugin**

The Product Shaping plugin is hosted on GitHub. You’ll download it as a ZIP file and extract it to your computer.

1. **Go to the GitHub repository.** Open your web browser and navigate to:

   [https://github.com/Prabhat-NR/pm-claude-skills](https://github.com/Prabhat-NR/pm-claude-skills)

2. **Download the repository.** Click the green **Code** button near the top-right of the page, then select **Download ZIP**.

3. **Extract the ZIP file.** Locate the downloaded file (usually in your Downloads folder) and unzip it. You’ll get a folder called something like *pm-claude-skills-main*.

4. **Locate the plugin folder.** Inside the extracted folder, find the **product-shaping** directory. This is the plugin. It should contain a **.claude-plugin** folder, a **skills** folder, and a **README.md** file.

5. **Save the plugin somewhere accessible.** Move or copy the **product-shaping** folder to a location on your computer where you’ll keep it long-term. A good choice is a dedicated folder like **Documents/Claude Plugins/** or anywhere you store project files. You’ll point Claude to this location during installation.

| Alternative: Git Clone If you’re familiar with Git, you can also clone the repository directly: git clone https://github.com/Prabhat-NR/pm-claude-skills.git |
| :---- |

# **4\. Installing the Plugin in Claude Desktop**

Once you have the plugin folder on your computer, you need to tell Claude Desktop about it. There are two ways to do this:

## **Option A: Using the Plugin Manager (Recommended)**

1. **Open Claude Desktop** and start a new Cowork session (or open an existing one).

2. **Open the Plugin Manager.** In the chat input area, type **/plugin** and press Enter. This opens the interactive plugin manager.

3. **Add a local marketplace.** If the plugin is in a local folder, you’ll first add it as a local marketplace. Run:

   **/plugin marketplace add /path/to/pm-claude-skills**

   Replace the path with the actual location where you saved the extracted repository on your computer.

4. **Install the plugin.** Once the marketplace is added, install the plugin:

   **/plugin install product-shaping**

5. **Choose your scope.** You’ll be asked where to install the plugin:

   * **User scope** — Available in all your projects and sessions (recommended)

   * **Project scope** — Shared with anyone who works on the same project

   * **Local scope** — Only available to you in this specific project

6. **Activate the plugin.** Type **/reload-plugins** to activate the newly installed plugin without restarting Claude.

## **Option B: Quick Start with \--plugin-dir**

If you’re using Claude Code from the command line, you can load the plugin directly for a single session:

**claude \--plugin-dir /path/to/product-shaping**

This is great for testing, but the plugin won’t persist between sessions.

# **5\. Using the Skills**

Once the plugin is installed, you can use both skills directly from your Claude conversation. Here’s the recommended workflow:

## **Step 1: Create a User Story Map**

Start by asking Claude to build a story map. You can trigger this skill by using natural language or the skill command.

### **How to trigger the skill**

Simply describe what you want in the chat. Any of these will work:

* *“Create a story map for my e-commerce checkout flow”*

* *“Help me organize these user stories into a map”*

* *“Shape my backlog into a user story map”*

* *“Map my stories”*

### **What Claude will ask you**

Claude will walk you through a guided flow, asking one question at a time:

1. **Product scope** — Describe what you’re building in 2–3 sentences. You can also upload a backlog, PRD, journey map, or feature list.

2. **User persona(s)** — Who is your primary user? Claude will suggest options based on your description.

3. **User goal** — What is the user trying to achieve?

4. **Constraints** — Any technical, regulatory, or platform requirements (e.g., HIPAA, mobile-first, Stripe integration).

5. **Activities** — The high-level goals in the user’s journey.

6. **Steps** — The specific actions within each activity.

7. **Confirmation** — Claude shows you the complete backbone and asks you to confirm before building.

### **What gets created**

After you confirm, Claude builds the story map directly in your Figma file. You’ll see a new page appear with the complete map containing all your stories, auto-generated requirements, release-tier color coding, and any gap stories Claude identified.

## **Step 2: Identify Product Risks**

Once your story map is complete in Figma, use the risk skill to analyze it.

### **How to trigger the skill**

Ask Claude to assess risks. Any of these will work:

* *“Identify the product risks from my story map”*

* *“What could go wrong with this plan?”*

* *“Create a risk register for my product”*

* *“De-risk my story map”*

### **What Claude will ask you**

Claude will ask whether you have a Figma story map to analyze or want to describe your product instead. Choose the Figma option and provide the URL of your Figma file (the one containing the story map you just created).

### **What gets created**

Claude reads your story map directly from Figma and produces two outputs:

* **A markdown risk register** displayed in the chat — a complete, scored list of risks with mitigation strategies, organized by severity.

* **A visual risk register page in Figma** — added to the same Figma file as your story map, so your team can review both artifacts side by side.

| Reminder: Make Sure Figma Is Ready Before running either skill, confirm that: (1) The Figma Desktop Bridge plugin is running, (2) You have a Figma Design file open (not FigJam), and (3) The correct page is active in Figma. If anything goes wrong, the most common fix is re-launching the Desktop Bridge plugin. |
| :---- |

# **6\. Troubleshooting**

| Problem | Solution |
| :---- | :---- |
| Claude doesn’t recognize the skill commands | Make sure the plugin is installed and active. Type /reload-plugins to refresh. If using \--plugin-dir, ensure the path points to the correct folder. |
| Claude can’t connect to Figma | Re-open the Desktop Bridge plugin in Figma: Plugins → Development → Figma Desktop Bridge. Make sure you’re using a Figma Design file, not FigJam. |
| The story map doesn’t appear in Figma | Check that the Desktop Bridge was running before you triggered the skill. If it timed out, try running the skill again — Claude will resume where it left off. |
| Risk skill says it can’t find the story map | Make sure the story map page is the active page in your Figma file. Navigate to the “Story Map: \[Your Product\]” page before running the risk skill. |
| Plugin not found after installation | Type /plugin to open the plugin manager and check the Installed tab. Verify the plugin name and scope. Try /reload-plugins to refresh. |

**Need more help?** Visit the repository at [github.com/Prabhat-NR/pm-claude-skills](https://github.com/Prabhat-NR/pm-claude-skills) to file an issue or check for updates.