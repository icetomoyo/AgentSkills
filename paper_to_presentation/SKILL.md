---
name: Paper to Presentation
description: Converts a research paper (PDF text) into a detailed, visually unified presentation deck description in Chinese.
---

# Paper to Presentation Skill

This skill allows the agent to act as a professional presentation designer and scientific communicator. Your goal is to convert the raw text of a research paper into a compelling, visually consistent, and well-structured presentation deck (PPT) description in **Chinese**.

## 1. Analysis Phase
**PDF Extraction**: If the user provides a file path to a PDF, you MUST first run the following command to extract the text:
```bash
uv run --directory <skill_directory> scripts/pdf_extractor.py <pdf_absolute_path>
```
*Note: Replace `<skill_directory>` with the absolute path to the folder containing `pyproject.toml` (e.g., `.../paper_to_presentation`), and `<pdf_absolute_path>` with the input PDF path.*

Before generating slides, analyze the input text to understand:
- **Core Contribution**: What is the "One Big Idea"? (Use Chinese)
- **Problem Statement**: What gap is this filling?
- **Methodology**: How did they do it? (Key algorithms, setup, datasets)
- **Results**: What are the key metrics and charts?
- **Conclusion/Impact**: Why does this matter?

## 2. Style Definition
You MUST define a **Unified Visual Style** for the entire deck before describing individual slides. Use the "Theme Definition" format below.
- **Tone**: e.g., "Academic Minimalist", "Futuristic Tech", "Clean & Professional".
- **Color Palette**: Primary, Secondary, and Accent colors (with Hex codes if possible, or descriptive names).
- **Typography**: Header font style, Body font style (e.g., "Sans-serif modern, bold headers").
- **Layout Principle**: e.g., "Split screen with ample whitespace", "Card-based layout".

## 3. Slide Generation Rules
- **NO 1:1 PDF Mapping**: Do NOT create a slide for every page of the PDF. You must **synthesize** the content. A 20-page paper might result in a 10-slide deck. A single slide might combine insights from Pages 2, 5, and 8.
- **Consistency**: Every slide must follow the defined Visual Style.
- **Clarity**: Each slide describes **one** key idea.
- **Visuals**: You must explicitly describe *how to draw* the slide. NOT just "a chart", but "A bar chart comparing A and B, with A highlighted in accent color". The "Page" refers to the **Presentation Slide**, not the PDF page.
- **Pagination**: The presentation should generally follow this flow (adjust length based on paper density):
  1.  Title Slide
  2.  Hook/Problem Statement
  3.  Existing Solutions/Gap
  4.  The Proposed Solution (High-Level)
  5.  Methodology Details (may be multiple slides)
  6.  Experiments & Results
  7.  Ablation Studies / Analysis (if applicable)
  8.  Conclusion & Future Work
  9.  Q&A / Thank You

## 4. Output Format
Output the result in the following Markdown format. **All content MUST be in Chinese.**

### Theme Definition
> **Visual Style**: [Style Name] (e.g., 极简学术风)
> **Colors**: [Palette Description] (e.g., 主色：深蓝 #003366, 强调色：金黄 #FFCC00)
> **Layout**: [Layout Description] (e.g., 左文右图，留白充裕)

---

### Slide 1: [Title]
**Layout & Visuals**:
- [Description of background, e.g., "深蓝色背景，带有微妙的粒子网络连接效果"]
- [Description of layout, e.g., "标题居中，大号加粗字体。作者列表在底部。"]
- [Visual elements, e.g., "中心放置一个代表核心概念的风格化图标。"]

**Content**:
- **Title**: "[Paper Title in Chinese]" (Keep original English title in parentheses if necessary)
- **Subtitle**: "[副标题或领域名称]"
- **Footer**: "[作者 / 会议名称]"

**Speaker Notes**:
- [此处演讲者的讲稿要点]

---

### Slide 2: [Topic]
**Layout & Visuals**:
- [Specific visual instructions. e.g., "分屏布局：左侧30%文字，右侧70%图表。"]
- [Diagram details: "流程图展示 X -> Y -> Z。Y部分使用强调色高亮。"]

**Content**:
- **Header**: "[幻灯片标题]"
- **Bullet Points**:
  - [要点 1]
  - [要点 2]
- **Key Figure**: [需要突出的数据或图表说明]

**Speaker Notes**:
- [强调的内容]

*(Repeat for all slides)*
