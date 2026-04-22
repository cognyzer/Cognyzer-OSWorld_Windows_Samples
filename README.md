# Cognyzer OSWorld Windows — Sample Dataset

A sample dataset of Windows desktop automation tasks built for Supervised Fine-Tuning (SFT) of AI agents. Each task targets real-world productivity workflows across Microsoft Excel, Word, PowerPoint, and multi-app scenarios.

---

## Repository Structure

```
Cognyzer-OSWorld_Samples/
├── task_definitions/               # Task JSON specs (instructions + evaluators)
│   ├── excel/
│   ├── word/
│   ├── ppt/
│   └── multi_app/
└── completed_samples/              # Human-recorded SFT trajectories
    ├── excel/
    │   └── <task_name>/
    │       ├── <task_name>.json    # Task definition
    │       └── SFT/
    │           ├── Trajectory and Screenshot/
    │           └── Colab/
    ├── word/
    └── ppt/
```

---

## Task Definitions

Task definitions are JSON files that specify the task instruction, setup config (file downloads, app launch), and automated evaluator. They are the ground truth used to evaluate agent performance.

| Task | App | Description |
|------|-----|-------------|
| `excel_task_01_sales_analysis` | Excel | Enter revenue formulas, add TOTAL row, bold headers |
| `excel_task_02_expense_dashboard` | Excel | Add percentage column, format as %, freeze top row |
| `word_task_01_quarterly_report` | Word | Double-space document, set Times New Roman 19, highlight a quote |
| `word_task_02_research_paper` | Word | Center-align title, bold/italic author, color "agriculture" blue |
| `ppt_task_01_company_overview` | PowerPoint | Bold slide 1 title, 4-item bullet list on slide 2, Fade transition |
| `ppt_task_02_training_presentation` | PowerPoint | Add subtitle, speaker notes, cyan background on all slides |
| `multi_task_01_sales_report` | Excel + PowerPoint | Create bar chart in Excel, paste onto PPT slide 3 |
| `multi_task_02_project_proposal` | Excel + Word | Compute formulas in Excel, insert result value into Word doc |

---

## Completed Samples

Each completed sample contains a full human-recorded SFT trajectory for the task.

```
completed_samples/<app>/<task_name>/
├── <task_name>.json                    # Task definition (instruction + evaluator)
└── SFT/
    ├── Trajectory and Screenshot/
    │   ├── trajectory.jsonl            # Recorded action sequence (step-by-step)
    │   ├── evaluation_score.txt        # Automated evaluation result (0.0 – 1.0)
    │   ├── step_00_before.png          # Screenshot before each step
    │   ├── step_00_before.xml          # Accessibility tree snapshot per step
    │   └── ...
    └── Colab/
        └── <task_name>.ipynb           # Colab notebook version of the trajectory
```

### Completed Tasks

| Task | App | Score |
|------|-----|-------|
| `excel_task_01_sales_analysis` | Excel | 1.0 |
| `excel_task_02_expense_dashboard` | Excel | 1.0 |
| `word_task_01_quarterly_report` | Word | 1.0 |
| `word_task_02_research_paper` | Word | 1.0 |
| `ppt_task_01_company_overview` | PowerPoint | 1.0 |
| `ppt_task_02_training_presentation` | PowerPoint | 1.0 |

---

## Data Format

### `trajectory.jsonl`
Each line is a JSON object representing one recorded action:
```json
{ "step": 1, "action": "pg.click(477, 406)", "python_command": "pyautogui.click(477, 406)", "note": "" }
```

### `<task_name>.json`
Defines the task instruction, file setup, and evaluator logic used to score agent performance.

### `<task_name>.ipynb`
Colab notebook version of the trajectory for easy viewing and replay.

---

## Source

Tasks created by [Cognyzer](https://github.com/cognyzer) as part of the OSWorld Windows dataset.
