# **Advanced Context Engineering for AI in Software Engineering: Lessons Learned & Best Practices**  
*Based on the presentation “No Vibes Allowed: Solving Hard Problems in Complex Codebases” by Dex Horthy (HumanLayer) at the AIE/Code Summit, presented by Google DeepMind*

---

## **Introduction & Key Takeaways**
The integration of AI, particularly coding agents, into software engineering workflows is not uniformly beneficial. Its effectiveness depends heavily on **project maturity**, **task complexity**, and how teams manage **context, workflow, and collaboration**. The core insight: **Coding agents will be commoditized—the real challenge is team and workflow transformation.**

---

## **Lessons Learned**

### **1. AI Often Increases Rework in Complex or Brownfield Projects**
- Data from real deployments (May–Dec 2024) shows that AI-assisted development can lead to significant **rework and refactoring**, especially in existing, complex codebases.
- **Brownfield projects** (legacy systems, intricate dependencies) see smaller productivity gains and higher rework rates compared to **Greenfield projects**.

### **2. Productivity Gains Are Highly Variable**
The impact of AI on engineering productivity is not uniform:

| Task Complexity | Greenfield Projects | Brownfield Projects |
|----------------|---------------------|---------------------|
| **High**       | +10–15%             | +0–10%              |
| **Low**        | +35–40%             | +15–20%             |

- **High-complexity tasks** still require deep human insight and contextual understanding.
- **Low-complexity, repetitive tasks** see the largest gains, even in brownfield environments.

### **3. Without Workflow Adaptation, Teams Are “Hosed”**
- Simply adding an AI coding tool without transforming team workflows, communication, and planning leads to suboptimal outcomes.
- The **hardest part** is not the AI tool itself, but the **people and process change** required to use it effectively.

---

## **Best Practices for Effective AI-Powered Engineering**

### **1. Context Engineering is Critical**
- **Optimize the context window** for:
  - **Correctness** – include the right files and dependencies.
  - **Completeness** – ensure enough background to avoid faulty assumptions.
  - **Size** – keep it manageable to avoid noise.
  - **Trajectory** – maintain a coherent thread of progress and decisions.

### **2. Use Intentional Compaction**
- Regularly summarize progress, decisions, and current failures into a structured document (e.g., `progress.md`).
- Example prompt:  
  *“Write everything we did so far to progress.md, ensure to note the approach we're taking, the steps we've done so far, and the current failure we're working on.”*
- This resets the context intelligently and maintains momentum without losing history.

### **3. Know When to Restart vs. Re-steer**
- Sometimes it’s better to **start with a fresh context** than to continue debugging a misdirected session.
- Clear re-steering prompts can help:  
  *“Make sure you use XYZ approach.”*

### **4. Scope Tasks Appropriately**
Match the problem to the right level of AI support:

| Task Type                          | Recommended Approach                |
|------------------------------------|--------------------------------------|
| **Hardest problems**               | Human-led, phased research & planning |
| **Medium complexity / small features** | AI-assisted with clear plans        |
| **Small fixes, copy changes**      | Direct AI execution                  |

### **5. Adopt a Structured Workflow**
For non-trivial tasks:
1. **Research phase** – understand the codebase and dependencies.
2. **Planning phase** – break down into clear, implementable steps.
3. **Implementation** – execute phase-by-phase, with compaction between stages.
4. **Multiple sessions may be needed** – don’t force a single continuous session.

### **6. Build a Robust Coding Agent Stack**
A mature coding agent system includes:
- **Project Engineering** – structuring work for AI.
- **Memory & RAG** – retrieving relevant context.
- **State / History Management** – tracking progress.
- **Harness Engineering** – commands, hooks, sweepers.
- **Codebase Design** – organizing for AI readability.

### **7. Treat AI Like a Junior Developer with a Short Attention Span**
- Provide clear, concise, and structured guidance.
- Assume it will forget or drift – build in checkpoints and summaries.
- Use **explicit mappings and overrides** in UI components (as seen in the Bash/Terminal icon example) to ensure consistency.

---

## **Future Outlook**

### **Coding Agents Will Be Commoditized**
- The technology itself will become widely available and undifferentiated.
- **Competitive advantage will come from workflow and team transformation**, not from the agent alone.

### **Teams Must Evolve**
- Engineers need to become **orchestrators of AI workflows**.
- Focus on:
  - **Decomposition** of problems into AI-solvable units.
  - **Context design** – curating what the AI sees.
  - **Validation & integration** – ensuring AI output fits the system.

### **If You Can’t Figure This Out, You’re Hosed**
- Organizations that fail to adapt their engineering practices around AI will fall behind in velocity, quality, and developer satisfaction.

---

## **Conclusion**
Successfully integrating AI into software engineering requires:
- **Honest assessment** of where AI adds value vs. overhead.
- **Investment in context engineering** and workflow design.
- **Willingness to transform team structures** and development rituals.
- **Continuous learning and adaptation** as tools and practices evolve.

The era of “vibes-based” AI tooling is over. The future belongs to teams that engineer their context, their workflows, and their collaboration with intention.
