## Annotation Guidelines for eBay Title Translation Pipeline

### 1. Introduction

These guidelines define the process, taxonomy, and quality standards for human annotation in the eBay Title Translation pipeline. Annotators will translate English product titles from eBay UK into Chinese and evaluate machine-generated translations. Consistency, accuracy, and adherence to taxonomy are critical.

### 2. Annotation Tasks

#### 2.1 Translation Review

* **Input**: Original English title and machine-generated Chinese translation.
* **Output**: Rating of the translated results, and whenever necessary please also provide additional comments on either 1) how the title should be translated or 2) how parts of the title (words, phrases) should be translated.
* **Decision Scale**:

  * **1 (Accurate)**: Translation is accurate, fluent, preserves meaning and style.
  * **2 (Minor Error)**: Minor issues (e.g. word order, minor terminology), but overall correct.
  * **3 (Major Error)**: Noticeable errors (e.g. missing context, slight mistranslation) that require correction.
  * **4 (Unintelligible)**: Significant errors (e.g. wrong meaning, missing key details) that necessitate full re-translation.

### 3. Taxonomy & Label Definitions

| Label | Description                   |
| ----- | ----------------------------- |
| 1     | Accurate                      |
| 2     | Minor Error                   |
| 3     | Major Error                   |
| 4     | Unintelligible                |

### 4. Guidelines & Examples

#### 4.1.1 Positive Example

* **Original**: "Samsung Galaxy S21 Ultra 5G Android Smartphone"
* **Machine Translation**: "三星 Galaxy S21 Ultra 5G 安卓智能手机"
* **Label**: 1
* **Comment**: 

#### 4.1.1 Negative Example

* **Original**: "Potato Chipper Chip Chopper Cutter Slicer Maker and 2 Steel Edges French Fries"
* **Machine Translation**: "土豆切片器切丁切割机制片器及2钢边法式炸薯条机"
* **Label**: 4
* **Comment**: should be "多功能土豆切条器 薯条切割机·2款不锈钢刀片可换·家用手动切片切丝器" 

#### 4.2 Common Pitfalls

* **Over-translation**: Adding extra descriptors not in the original.
* **Under-translation**: Omitting brand or model numbers.
* **Literal translation**: Preserving word order that reads awkwardly in Chinese.
* **No Spacing or Separation**: Cramping the translated keywords together.

### 5. Annotation Workflow

1. Load batch of translations in the Jupyter interface.
2. Review each sample:

   * Check fidelity to original meaning.
   * Ensure fluency and proper terminology.
3. Assign a label (1-4) and confidence score.
4. Whenever necessary based on your judgement, provide corrected translation and brief explanation.
5. Submit annotations; system will record metadata (annotator\_id, timestamp, pipeline\_version).

---

*Thank you for your careful and consistent work!*
