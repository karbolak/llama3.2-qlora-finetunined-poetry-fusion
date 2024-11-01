---
library_name: transformers
tags:
- lora
- poetry
- art
license: mit
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
- **License:** MIT License

### Model Sources
- **Repository:** [TBD]
- **Project Paper:** [TBD]

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

Use the following code snippet to begin generating poetry with the model:

```python
from transformers import pipeline

generator = pipeline('text-generation', model='your-model-id')
system_message = """
You are an expert in poetry fusion, specializing in blending the distinct styles of two poets. Focus on emotional depth, unique metaphor usage, symbolic imagery, and rhythmic patterns. Your task is to merge not only technical elements like word choice and structure but also the deeper conceptual and emotional richness that define each poet's work.
"""

Poet_1, Poet_2 = "William Shakespeare", "Edgar Allan Poe"
user_message = f"""
Generate a new poem that fuses the styles of {Poet_1} and {Poet_2}. Combine their styles in the rest of the poem, merging their use of metaphor, rhythm, and tone. Make the poem to 150 words.
"""

prompt = f"{system_message}\nUser: {user_message}\nAssistant:"


device = "cuda:0"

# Custom decoding with temperature, top_p, and top_k for more creative output
def generate_with_constraints(prompt, temperature=0.7, top_p=0.9, top_k=50):
    inputs = tokenizer(prompt, return_tensors="pt").to("cuda:0")
    outputs = model.generate(
        **inputs,
        max_new_tokens=256,
        temperature=temperature,     # Added temperature for creativity
        top_p=top_p,                 # Nucleus sampling
        top_k=top_k,                 # Limit token selection for more focused choices
        no_repeat_ngram_size=3,
        num_beams=5                  # Beam search to enforce rhyme/meter constraints
    )
    return tokenizer.decode(outputs[0], skip_special_tokens=True)

# Now generate the poem with creativity-enhancing parameters
poetry_output = generate_with_constraints(prompt, temperature=0.8, top_p=0.85, top_k=40)
```

## Training Details

### Training Data
The model was fine-tuned on a subset of a larger poetry dataset, which includes 524 English poems, with 227 poems specifically from our selected poets. This curated set allowed the model to focus on the unique attributes of each poet’s work while providing additional data for improved generalization.

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

This project is licensed under the MIT License.

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
```
---