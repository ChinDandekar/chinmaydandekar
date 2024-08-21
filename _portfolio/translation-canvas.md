---
title: "Translation Canvas"
excerpt: "A Python package that helps machine translation model developers analyze and compare their models outputs <br/><br/><img src='/chinmaydandekar/images/translation-canvas/render-workflow.png'>"
collection: portfolio
---

[![PyPI version](https://badge.fury.io/py/translation-canvas.svg)](https://badge.fury.io/py/translation-canvas)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

## Translation Canvas: An Explainable Interface to Pinpoint and Analyze Translation Systems

### Overview:

Translation Canvas is an advanced explainable interface designed for machine translation researchers to deeply analyze and compare the performance of various translation models. It serves as a sophisticated tool that not only highlights common errors within translations but also facilitates instance-level and system-level performance evaluations. By offering intuitive visualizations and powerful analytical capabilities, Translation Canvas helps users pinpoint specific weaknesses in translation models, enabling more informed model improvements.

---

**Technical Details**:

1. **Architecture**:
   - **Backend**: Translation Canvas is built on a Python Flask framework. The backend handles data processing, analysis, and interaction with the front-end through a Flask-based API.
   - **Frontend**: The interface uses Jinja templates, which are dynamically rendered based on the user’s interactions. The UI is designed to be intuitive, enabling easy navigation and exploration of different translation models and their outputs.
   - **Database**: DuckDB is utilized for managing and querying the dataset, allowing efficient storage and retrieval of translation instances, error annotations, and model performance metrics.

2. **Key Features**:
   - **Instance-Level Analysis**: 
     - Translation Canvas provides detailed comparisons between different models' outputs at the instance level. Errors are highlighted in the text (e.g., red for major errors, orange for minor errors), with tooltips providing additional explanations.
     - Users can perform complex searches across translation instances based on error types, text content, and more. SQL-like query capabilities enable filtering for highly specific instances, facilitating focused analysis.
    <img src='/chinmaydandekar/images/translation-canvas/instance-compare.png'>

   - **System-Level Analysis**:
     - A comprehensive dashboard offers insights into the overall performance of translation models. Users can view distributions of error types, InstructScore, and COMET scores across the entire dataset.
     - Translation Canvas supports multiple evaluation metrics, including BLEU, COMET, and InstructScore, providing both quantitative and qualitative assessments of translation quality.
    <img src='/chinmaydandekar/images/translation-canvas/system-3-compare.png'>

3. **User Interaction**:
   - **Manual Input & File Upload**:
     - Users can manually input translation instances or upload text-based files for evaluation. The system offers an integrated development environment for custom file processing, ensuring flexibility in data submission.
     <img src='/chinmaydandekar/images/translation-canvas/submit-workflow.png'>

4. **Advanced Features**:
   - **Error Span Highlighting**: When errors are identified in a translation, they are visually marked within the text. Hovering over these highlights reveals a tooltip with a detailed explanation, aiding users in understanding specific error types.
   - **Model Comparison**: Models can be compared directly, with predictions sorted by quality and user feedback (e.g., up/down arrows). This feature allows researchers to identify why one model may outperform another in specific instances.
   - **Instance Re-Ranking**: Users can manually re-rank translations to reflect expert judgments, contributing data for refining future evaluations.

---

**Visualization and User Experience**:
Translation Canvas prioritizes a clear and informative presentation of data, making complex translation errors and model comparisons accessible to users. Visual aids such as color-coded error highlights, comparison dashboards, and interactive tooltips enhance the usability of the system.

<img src='/chinmaydandekar/images/translation-canvas/render-workflow.png'>

---

**Conclusion**:
Translation Canvas is a crucial tool for the translation research community, offering deep insights and enabling fine-grained analysis of translation model performance. Its user-friendly design, coupled with powerful analytical tools, makes it an invaluable resource for improving machine translation systems.

### Links:
Check out a demo video for this package: [Demo Submission Video](https://youtu.be/IoK4yAwK1II)\
Check out the paper for this package: [Demo Submission Paper](/chinmaydandekar/files/translation_canvas.pdf)\
Check out the source code for this package: [Source Code](https://github.com/ChinDandekar/translation_canvas)