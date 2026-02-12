<div align="center">

<h2>COMI: Coarse-to-fine Context Compression via Marginal Information Gain</h2>

<p>
  <a href="https://scholar.google.com/citations?user=v7oMH04AAAAJ&hl=zh-CN">Jiwei Tang</a><sup>1</sup> · 
  Shilei Liu<sup>2</sup> · 
  Zhicheng Zhang<sup>1</sup> · 
  Yujin Yuan<sup>2</sup> · 
  Libin Zheng<sup>3,†</sup> · 
  Wenbo Su<sup>2</sup> · 
  Bo Zheng<sup>2,†</sup>
</p>
<p>
  <sup>1</sup> Tsinghua University · <sup>2</sup> Future Living Lab of Alibaba · <sup>3</sup> Sun Yat-sen University· <sup>†</sup> Corresponding Author
</p>

</div>

<div align="center">
  <a href="https://iclr.cc/virtual/2026/poster/">
    <img src="https://img.shields.io/badge/ICLR-2026-9065CA" alt="ICLR 2026">
  </a>
  <a href='https://arxiv.org/abs/2602.01719'><img src='https://img.shields.io/badge/Paper-ArXiv-d63031?logo=arxiv&logoColor=white'></a>
  <a href='https://huggingface.co/datasets/Twwilght/RAM-NQ'><img src='https://img.shields.io/badge/%F0%9F%A4%97%20Datasets-Huggingface-yellow'></a>
</div>

This is the official implementation for our **ICLR 2026** paper "COMI: Coarse-to-fine Context Compression via Marginal Information Gain". Our work introduces a context compression method that jointly optimizes semantic relevance and diversity through Marginal Information Gain (MIG), enabling effective long-context processing under high compression rates (up to 32×) while eliminating redundant information.

<div align="center">
  <img src="./imgs/framework.png" width="90%" height="auto" />
  <p>Compression Process of COMI.</p>
</div>

<div align="center">
  <img src="./imgs/training_paradigm.png" width="90%" height="auto" />
  <p>Training Process of COMI.</p>
</div>

## Release
- [02/12] Initial Release. The models and code for training and inference are coming soon!

## Motivation
Existing task-aware compression methods focus solely on relevance to the query, ignoring semantic redundancy among retained tokens—leading to accumulation of *"relevant but redundant"* content that misleads LLMs.

<div align="center">
  <img src="./imgs/heatmap.png" width="50%" height="auto" />
  <p>Top Query-Related Tokens Similarity.</p>
</div>

We propose:
- **Marginal Information Gain (MIG)**: A novel metric defined as *relevance to query minus semantic redundancy with other units*, jointly optimizing information value and diversity
- **Coarse-to-Fine Compression Strategy**:
  - **Coarse-Grained Group Reallocation**: Dynamically assigns compression rates across context segments based on inter-group MIG
  - **Fine-Grained Token Merging**: Fuses tokens within groups using intra-group MIG-weighted averaging to preserve key semantics while eliminating redundancy

## Main Results
COMI achieves superiority performance across QA and summarization tasks under high compression rates:
<div align="center">
  <img src="./imgs/result.png" width="85%" height="auto" />
</div>

## BibTeX
If you find our repo helpful, please consider leaving a star and cite our paper

```bibtex
@misc{tang2026comicoarsetofinecontextcompression,
      title={COMI: Coarse-to-fine Context Compression via Marginal Information Gain}, 
      author={Jiwei Tang and Shilei Liu and Zhicheng Zhang and Yujin Yuan and Libin Zheng and Wenbo Su and Bo Zheng},
      year={2026},
      eprint={2602.01719},
      archivePrefix={arXiv},
      primaryClass={cs.CL},
      url={https://arxiv.org/abs/2602.01719}, 
}
```