# SuperTokenizer

A high-performance tokenizer built to rival GPT-4, trained on the C4 dataset.

## Overview
SuperTokenizer is a custom Byte Pair Encoding (BPE) tokenizer designed to optimize token efficiency, multilingual support, and speed. Built using the `tokenizers` library from Hugging Face and trained on the Colossal Clean Crawled Corpus (C4), this project aims to push the boundaries of tokenization for large language models (LLMs).

## Features
- **Byte-Level BPE**: Inspired by GPT-4, uses byte-level pre-tokenization for robust handling of diverse text.
- **C4 Training Data**: Leverages the massive, cleaned web crawl dataset from AllenAI.
- **Customizable**: Adjustable vocabulary size (default: 30k) and sample size.
- **GPU-Accelerated**: Optimized for NVIDIA A100 GPUs in Google Colab.

## Installation
Run in Google Colab with an A100 GPU runtime:
```bash
!pip install datasets tokenizers tiktoken
```

## Usage
1. **Load Data**: Streams 100k examples (configurable) from C4’s English subset.
2. **Train**: Builds a BPE tokenizer with a 30k-token vocabulary.
3. **Test**: Compares token efficiency against GPT-4’s tokenizer.

```python
# Example
text_file = load_c4_data(sample_size=100000)
tokenizer = train_tokenizer(text_file, vocab_size=30000)
test_tokenizer(tokenizer)
```

## Sample Output
```
GPU Available: True
GPU Name: NVIDIA A100-SXM4-40GB
Loading C4 dataset from Hugging Face...
C4 sample (100000 examples) saved to c4_sample.txt
Training tokenizer...
Training complete!
Original: The quick brown fox jumps over the lazy dog.
Tokens: ['ĠThe', 'Ġquick', 'Ġbrown', 'Ġfox', 'Ġjumps', 'Ġover', 'Ġthe', 'Ġlazy', 'Ġdog', '.']
Token IDs: [5, 6, 7, 8, 9, 10, 11, 12, 13, 14]
Decoded: The quick brown fox jumps over the lazy dog.

GPT Tokenizer Comparison:
GPT Tokens: ['The', ' quick', ' brown', ' fox', ' jumps', ' over', ' the', ' lazy', ' dog', '.']
GPT Token Count: 10
Custom Token Count: 10
```

## Scaling Up
- Increase `sample_size` to 1M+ examples (requires more disk space).
- Set `vocab_size=100000` for GPT-4-level coverage.
- Use `allenai/c4/multilingual` for multilingual support.

## Requirements
- Google Colab Pro/Pro+ with A100 GPU
- Python 3.7+
- Libraries: `datasets`, `tokenizers`, `tiktoken`, `torch`, `tqdm`

## License
MIT License

## Acknowledgments
- Hugging Face for `tokenizers` and `datasets`.
- AllenAI for the C4 dataset.
- Writer.com for inspiration via Palmyra.

