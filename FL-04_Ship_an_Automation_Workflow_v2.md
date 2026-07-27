# FL-04 – Ship an Automation Workflow v2

## Student
**Name:** Evelyn Anastasia

## Objective
Design and evaluate a no-code AI workflow that automates technical writing through three predefined stages.

## Workflow Overview
This workflow converts a short project description into a structured technical report.

### Workflow Diagram

```text
Project Description
        │
        ▼
Step 1
Research & Analyze Requirements
        │
        ▼
Step 2
Generate Technical Report Draft
        │
        ▼
Step 3
Review, Improve & Format
        │
        ▼
Final Technical Report
```

## Tools Used
- Claude Desktop
- Claude Projects
- AI Project Instructions (No-code)

## Project Instructions

You are an engineering and AI technical writing assistant.

Your task is to generate clear, well-structured technical reports from a short project description.

Always follow this workflow:

1. Understand the project and identify its purpose.
2. Extract important technical components, technologies, and objectives.
3. Generate a structured report with:
   - Introduction
   - Objectives
   - System Overview
   - Technologies Used
   - Expected Results
   - Conclusion
4. Review the report for clarity, grammar, and logical consistency.
5. If information is missing, clearly state assumptions instead of inventing facts.

## Workflow Steps

### Step 1 – Research & Analyze
The AI identifies the project's objective, expected functionality, and required technologies.

**Output Handoff:** Project understanding.

### Step 2 – Generate Draft
The AI generates a structured technical report containing:
- Introduction
- Objectives
- System Overview
- Technologies Used
- Expected Results
- Conclusion

**Output Handoff:** Complete first draft.

### Step 3 – Review & Improve
The AI checks grammar, organization, readability, and consistency before producing the final report.

**Final Output:** Technical report ready for review.

# Five Test Runs

## Run 1
**Input:** ESP32-based Water Quality Monitoring System

**Output Sections**
- Introduction
- Objectives
- System Overview
- Technologies Used
- Expected Results
- Conclusion

**Screenshot:** *(Insert Screenshot 1)*

---

## Run 2
**Input:** Smart Parking IoT System

**Output Sections**
- Introduction
- Objectives
- System Overview
- Technologies Used
- Expected Results
- Conclusion

**Screenshot:** *(Insert Screenshot 2)*

---

## Run 3
**Input:** AI Resume Analyzer

**Output Sections**
- Introduction
- Objectives
- System Overview
- Technologies Used
- Expected Results
- Conclusion

**Screenshot:** *(Insert Screenshot 3)*

---

## Run 4
**Input:** Student Attendance System using Face Recognition

**Output Sections**
- Introduction
- Objectives
- System Overview
- Technologies Used
- Expected Results
- Conclusion

**Screenshot:** *(Insert Screenshot 4)*

---

## Run 5
**Input:** Library Management Website

**Output Sections**
- Introduction
- Objectives
- System Overview
- Technologies Used
- Expected Results
- Conclusion

**Screenshot:** *(Insert Screenshot 5)*

# Time Analysis

| Activity | Time |
|-----------|------|
| Claude Project setup | 15 minutes |
| Run 1 | 1 minute |
| Run 2 | 1 minute |
| Run 3 | 1 minute |
| Run 4 | 1 minute |
| Run 5 | 1 minute |
| **Total Workflow Time** | **20 minutes** |

Estimated manual creation of five reports: **100 minutes**

Estimated workflow completion: **20 minutes**

**Estimated time saved:** **80 minutes (approximately 80%)**

## Known Failure Points

- The AI may make assumptions if project descriptions are incomplete.
- Technical specifications should always be verified manually.
- Generated reports may require formatting adjustments.
- Domain-specific terminology should be reviewed by a human.
- Final review is required before submission.

## Human Review

Human review remains essential to:
- Verify technical accuracy.
- Confirm assumptions.
- Improve clarity where needed.
- Ensure the report matches the actual project.

## Reflection

Building this workflow demonstrated how a structured AI pipeline can automate repetitive writing tasks while maintaining consistency. Organizing the work into research, drafting, and review stages significantly reduced the time required to produce technical reports. Although the workflow improved efficiency, human verification is still necessary to ensure technical correctness and completeness. This project also strengthened my understanding of workflow design and prepared me for learning the differences between workflows and autonomous AI agents.

## Conclusion

This project successfully implemented a three-step no-code AI workflow using Claude Projects. The workflow completed five different technical writing tasks consistently and reduced the overall time required compared to manual writing. The results show that structured AI workflows are effective for repetitive writing tasks while still benefiting from human oversight.
