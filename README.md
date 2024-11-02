---
library_name: transformers
tags:
- lora
- poetry
- art
license: llama3.2
language:
- en
base_model:
- meta-llama/Llama-3.2-1B-Instruct
---

# Poetry Fusion Model: A Creative Exploration in AI-Generated Poetry

This repository contains a unique poetry generation model that blends stylistic and emotional nuances from selected poets. Our focus is on exploring the creative capacities of large language models, using fine-tuning techniques to emulate and merge the poetic styles of celebrated authors. 

## Model Details

### Model Description

The Poetry Fusion model is a transformer-based language model fine-tuned to produce poetry that captures elements from various renowned poets. The model aims to blend linguistic, thematic, and emotional features, creating novel verses that resonate with the stylistic depth of human poetry.

#### Key Poets in Focus
This model was fine-tuned to capture and fuse the stylistic nuances of poets such as:
- **William Shakespeare**
- **Walt Whitman**
- **John Donne**
- **Edgar Allan Poe**
- **Emily Dickinson**
- **E.E. Cummings**
- **Elizabeth Barrett Browning**
- **A.E. Stallings**
- **W.B. Yeats**
- **Wallace Stevens**

These poets were chosen for their distinctive styles, themes, and emotional depth, providing a rich spectrum of characteristics for the model to emulate and blend.

- **Developed by:** Natalie Mladenova, Karolina Kozikowska, Kajetan Karbowski
- **Model Type:** Transformer-based language model, fine-tuned with LoRa
- **Languages:** English
- **License:** Llama 3.2 Community License

### Model Sources
- **Repository (the same, but initially submitted on huggingface):** https://huggingface.co/karbolak/llama3.2-qlora-finetunined-poetry-fusion/tree/main
- **Project Paper:** Attached on brightspace.

## Uses

### Direct Use
The model is suited for tasks involving poetry generation, with particular relevance for creative applications in AI, literature studies, or projects within the humanities.

### Out-of-Scope Use
This model is not designed for fact-based or research-intensive tasks as it prioritizes stylistic and emotional resonance over factual accuracy.

## Bias, Risks, and Limitations

This model is influenced by the poetic styles and linguistic nuances specific to a Western, English-speaking tradition, as represented in its training data. Users should be mindful of potential stylistic biases and limitations in cultural diversity.

### Recommendations
For broader applicability, further fine-tuning with culturally diverse poetic datasets may be necessary. We recommend awareness of inherent biases in creative projects and contextually adjusting outputs as needed.

## How to Get Started with the Model

You may find all necessary information about the model deployment in the Jupyter Notebook "Poetry_Fusion_using_Llama_3.2.ipynb".

## Training Details

You may find all necessary information about the model training in the Jupyter Notebook "Poetry_Fusion_using_Llama_3.2.ipynb".

### Training Data
The model was fine-tuned on a subset of a larger poetry dataset "LLM_Dataset.csv" which may be found in the repository files. It includes 524 English poems, with 227 poems specifically from our selected poets. This curated set allowed the model to focus on the unique attributes of each poet’s work while providing additional data for improved generalization.

### Training Procedure
To achieve high-quality output, the model was fine-tuned using the following parameters:
- **Tokens per Prompt:** 256
- **Temperature:** 0.8 (adjusted to enhance creativity)
- **Sampling:** top_p = 0.85, top_k = 40
- **LoRa Hyperparameters:** `alpha=16`, `dropout=0.1`, `r=64`

## Evaluation

The model’s effectiveness was assessed through both human and automated evaluations. Human evaluators examined poetic characteristics and emotional depth, using a framework based on stylistic features specific to each poet in our selection. Additionally, GPT-4 cross-validated stylistic adherence.

### Metrics
Evaluation focused on creativity, coherence, thematic depth, and stylistic consistency to gauge the model’s capacity to blend distinct poetic styles effectively.

## License

This project is licensed under the Meta's Llama 3.2 Community License.

## Citation

If you reference this work, please use the following citation:

**BibTeX:**

```bibtex
@article{poetry_fusion_project,
  author = {Mladenova, Natalie and Kozikowska, Karolina and Karbowski, Kajetan},
  title = {Poetry Fusion - The Generation of New Poems Based on a Selection of Authors},
  year = {2024},
  institution = {University of Groningen},
}
```

## Contact

For questions or further information, please reach out to the authors:
- **Natalie Mladenova** - n.mladenova@student.rug.nl
- **Karolina Kozikowska** - k.kozikowska@student.rug.nl
- **Kajetan Karbowski** - k.j.karbowski@student.rug.nl
