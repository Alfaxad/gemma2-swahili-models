![D](https://github.com/user-attachments/assets/85d65364-360c-40f6-b144-14543757b26b)

# Gemma 2 Swahili 🌍

[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)
[![Hugging Face](https://img.shields.io/badge/🤗%20Hugging%20Face-Models-yellow)](https://huggingface.co/collections/Alfaxad/gemma-2-swahili-678c96591c0169c0bc1d4c34)
[![Kaggle](https://img.shields.io/badge/Kaggle-Models-blue)](https://www.kaggle.com/models/alfaxadeyembe/gemma-2-swahili)
[![Documentation](https://img.shields.io/badge/Documentation-Technical%20Reports-green)](Technical-Reports/)

Gemma 2 Swahili is a comprehensive suite of language models specifically adapted for Swahili language understanding and generation. This project brings advanced AI capabilities to over 200M Swahili speakers through efficient adaptation of Google's Gemma 2 models.

## Models 🚀

| Model | Parameters | Type | Memory | Links |
|-------|------------|------|---------|-------|
| Gemma2-2B-Swahili-Preview | 2B | Base | ~4GB | [HF](https://huggingface.co/Alfaxad/gemma2-2b-swahili-preview) \| [Kaggle](https://www.kaggle.com/models/alfaxadeyembe/gemma-2-swahili/transformers/gemma2-2b-swahili-preview) |
| Gemma2-2B-Swahili-IT | 2B | Instruction-tuned | ~4GB | [HF](https://huggingface.co/Alfaxad/gemma2-2b-swahili-it) \| [Kaggle](https://www.kaggle.com/models/alfaxadeyembe/gemma-2-swahili/transformers/gemma2-2b-swahili-it) |
| Gemma2-9B-Swahili-IT | 9B | Instruction-tuned | ~18GB | [HF](https://huggingface.co/Alfaxad/gemma2-9b-swahili-it) \| [Kaggle](https://www.kaggle.com/models/alfaxadeyembe/gemma-2-swahili/transformers/gemma2-9b-swahili-it) |
| Gemma2-27B-Swahili-IT | 27B | Instruction-tuned | ~54GB | [HF](https://huggingface.co/Alfaxad/gemma2-27b-swahili-it) \| [Kaggle](https://www.kaggle.com/models/alfaxadeyembe/gemma-2-swahili/transformers/gemma2-27b-swahili-it) |

## Features ✨

- Native Swahili language generation
- Advanced instruction following in Swahili
- Strong performance on academic and professional tasks
- Cultural context awareness for East African content
- Efficient deployment options across different scales

## Performance 📊

### Benchmark Results

| Model | MMLU (SW) | Sentiment | Translation |
|-------|-----------|-----------|-------------|
| 2B-IT | 34.17% (+19.17) | 66.50% (+17.50) | 0.3735 BLEU-1 |
| 9B-IT | 55.83% (+12.50) | 86.50% (+3.08) | 0.4709 BLEU-1 |
| 27B-IT | 54.17% (+34.17) | 88.50% (+1.00) | 0.4994 BLEU-1 |

## Quick Start 🚀

### Installation

```bash
pip install transformers accelerate
```

### Basic Usage

```python
import torch
from transformers import AutoTokenizer, AutoModelForCausalLM

# Load model and tokenizer
model_path = "gemma2-swahili/gemma2-2b-swahili-it"
tokenizer = AutoTokenizer.from_pretrained(model_path)
model = AutoModelForCausalLM.from_pretrained(
    model_path,
    device_map="auto",
    torch_dtype=torch.bfloat16
)

# Generate text
prompt = "Eleza umuhimu wa teknolojia ya kidijitali"
inputs = tokenizer(prompt, return_tensors="pt")
outputs = model.generate(
    **inputs,
    max_new_tokens=500,
    do_sample=True,
    temperature=0.7,
    top_p=0.95
)
print(tokenizer.decode(outputs[0], skip_special_tokens=True))
```

### Using 4-bit Quantization (for 9B and 27B models)

```python
from transformers import BitsAndBytesConfig

# Quantization config
bnb_config = BitsAndBytesConfig(
    load_in_4bit=True,
    bnb_4bit_quant_type="nf4",
    bnb_4bit_compute_dtype=torch.bfloat16,
    bnb_4bit_use_double_quant=True
)

# Load model with quantization
model = AutoModelForCausalLM.from_pretrained(
    model_path,
    quantization_config=bnb_config,
    device_map="auto",
    trust_remote_code=True
)
```

## Documentation 📚

- [Technical Reports](Technical-Reports)
- [Training Notebooks](Notebooks)
- [Benchmarking Results](Technical-Reports/Gemma2%20Swahili%20Models%20Benchmarking%20Report.pdf)
- [Model Cards](https://huggingface.co/collections/Alfaxad/gemma-2-swahili-678c96591c0169c0bc1d4c34)

## Benchmarks 📊

Comprehensive evaluation across multiple tasks:
- Swahili MMLU (14,042 questions)
- Sentiment Analysis (3,925 samples)
- Translation Quality (Wikimedia corpus)

## Training Methodology 🔬

Models were fine-tuned using:
- LoRA for 2B and 9B models
- QLoRA for 27B model
- Mixed precision training
- Gradient checkpointing
- Optimized batch sizes

## Citations 📖

```bibtex
@software{gemma2_swahili,
  title = {Gemma 2 Swahili: Efficient Adaptation of Large Language Models},
  author = {Eyembe, Alfaxad and Mtenga, Mrina},
  year = {2025},
  publisher = {GitHub},
  url = {https://github.com/Gemma-2-Swahili}
}
```

## Acknowledgments 🙏

- Google's Gemma team for the base models
- Lelapa AI for the Inkuba-Mono dataset
- Neurotech for the Swahili Sentiment Analysis dataset
- GouRMET project for translation data
- Bactrian X for instruction data
- Chris Ngiongolo for Swahili MMLU

## License 📝

This project is licensed under the Apache License 2.0 - see the [LICENSE](LICENSE) file for details.

## Contributing 🤝

We welcome contributions! Please see our [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.
