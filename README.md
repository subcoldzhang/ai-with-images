# Giving AI Images, Not Just Words
> *"The Weirdest thing isn't that AI can see images—it's that most people still only talk to it in text."*
[English](./README.md) | [中文版](./README_CN.md)
---
## The Problem
Since 2023, mainstream LLMs (GPT-4V, Claude 3, Gemini) have gained stable visual understanding. They can read screenshots, analyze charts, recognize layouts, and spot anomalies in waveforms.
But most people's habits haven't caught up. We still translate what we see into text before sending it to AI—like we're stuck in the "telegraph era" while the model is already multimodal.
This creates real inefficiency:
- More rounds of clarification
- Frequent misunderstandings
- Time wasted "translating images into text"
**What if we just... gave it the image?**
---
## What Happens When You Add Images
### Example 1: Analysis Assistant
<div align="center">

![example chart](./images/chart.png)

</div>

In our practice, we found a powerful pattern: **let AI visualize data first, then analyze the visualization**.
- 100k data points → AI struggles, high token cost, misses global patterns
- Same data as a line chart → AI instantly spots trends, outliers, periodic fluctuations
**Key insight**: Images are compressed expressions of data, not data loss.

### Example 2: DeepSeek-OCR — Text Compression via Vision
Paper: [DeepSeek_OCR_paper.pdf](https://github.com/deepseek-ai/DeepSeek-OCR/blob/main/DeepSeek_OCR_paper.pdf)
Experiment: Can long text be compressed into images and still be read back?
- 100 pages of English docs (600-1300 tokens per page)
- Compressed into 64-100 vision tokens (10x-20x compression)
- OCR accuracy: **97% at 10x compression**, **60% at 20x**
This proves: "Map text → image → compress to vision tokens" is viable.
<div align="center">
  
![DeepSeek OCR compression chart](./images/deepseek-ocr-chart.png)

</div>

### Example 3: Industrial Equipment Operation — Siemens & Munich University
Paper: [arXiv:2410.21943](https://arxiv.org/abs/2410.21943)
Question: "How to sync logs so DIGSI 5 can read indicator info?"
The answer requires both text instructions AND the button position in the image (marked as "Read log entries").
Result: Text + Image → **80% accuracy** vs Text-only or Image-only → **60%**
<div align="center">
  
![Industrial equipment example](./images/industrial-equipment.png)

</div>

---
## Why Adding Images Works
### 1. Higher Information Density
Text is lossy compression. When you translate visuals into words, you lose color, position, ratio, spatial relationships.
A screenshot usually doesn't need clarification. "The blue box on the left" could mean 10 different things in text, but one image nails it.
### 2. Screenshots Are Attention Markers
When you crop, circle, or add arrows—you're injecting your professional judgment into the input. AI knows "where to focus" without guessing.
### 3. Fewer Clarification Rounds
Describing a complex issue in text takes minutes + multiple follow-ups.  Adding a screenshot takes 10 seconds + one sentence of intent.

---
## When to Add Images
**Good candidates**:
- Spatial relationships (UI layout, system topology, circuit structure)
- Data charts (trends, outliers, patterns)
- Error/exception screens (screenshot > copying error text)
- Sketches, whiteboards, handwritten content
- UI implementation requests (reference image > verbal description)
**Not needed**:
- Pure logic/math reasoning
- Pure text writing/translation
- Abstract concepts without visual objects
**Best practices**:
1. Crop to key areas (don't dump a full-screen screenshot)
2. Add annotations (circles, arrows to show what you care about)
3. Combine text + image: text explains *intent*, image shows *context*

---
## Future Implications
### Ontology: Should Memory Be Stored as Images?
Traditional knowledge graphs require manual definition of concepts, relationships, rules—high cost, exponential maintenance.
But human memory isn't text. It's images. You remember your first bike ride as a *scene*, not a paragraph.
Maybe AI memory should be a collection of images too:
- One flowchart replaces hundreds of structured records
- One system screenshot replaces an API doc
- One dashboard frame replaces a numeric description
Structure extracted by AI, not defined by humans.
### Training Data: The Missing Piece Is Finally Available
**LLMs**: Past training missed diagrams, flowcharts, architecture charts. Multimodal training lets models learn from image-text pairs. Now we can generate synthetic data: image→text→image→text, self-reinforcing flywheel.
**Robotics**: YouTube's billions of human operation videos become training data. No need for expensive motion capture. RT-2, π0 are built on this logic.

---
## Takeaway
This isn't about abandoning text. It's about letting each medium do what it's best at:

<div align="center">

| Text | Image |
|------|-------|
| Intent, constraints, criteria | Context, details, evidence |
| What you want to solve | Where the problem is |

</div>

Next time you write a prompt, ask yourself: *"Is there something I can just screenshot?"*

---
## References
- [DeepSeek-OCR Paper](https://github.com/deepseek-ai/DeepSeek-OCR/blob/main/DeepSeek_OCR_paper.pdf)
- [arXiv:2410.21943 - Industrial Document QA](https://arxiv.org/abs/2410.21943)

---
## License
MIT License — feel free to share, remix, and build upon.

---
Questions? Reach me at zhangyuhao7@lixiang.com
