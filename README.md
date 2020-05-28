## Axial Attention

[![PyPI version](https://badge.fury.io/py/axial-attention.svg)](https://badge.fury.io/py/axial-attention)

Implementation of Axial attention for Pytorch. A simple but powerful technique to attend to multi-dimensional data efficiently.

Simply add some positional encoding to your data and pass it into this handy class, specifying which dimension is considered the embedding, and how many axial dimensions to rotate through. All the permutating, reshaping, will be taken care of for you.

### Install

```bash
$ pip install axial_attention
```

### Usage

Image

```python
import torch
from axial_attention import AxialAttention

img = torch.randn(1, 3, 256, 256)

attn = AxialAttention(
	dim = 3, 			 # embedding dimension
	dim_index = 1,       # where is the embedding dimension
	heads = 1,			 # number of heads for multi-head attention
	num_dimensions = 2,  # number of axial dimensions (images is 2, video is 3, or more)
)

attn(img)
```

Channel-last image latents

```python
import torch
from axial_attention import AxialAttention

img = torch.randn(1, 20, 20, 512)

attn = AxialAttention(
	dim = 512, 			 # embedding dimension
	dim_index = -1,      # where is the embedding dimension
	heads = 8,			 # number of heads for multi-head attention
	num_dimensions = 2,  # number of axial dimensions (images is 2, video is 3, or more)
)

attn(img)
```

Video

```python
import torch
from axial_attention import AxialAttention

video = torch.randn(1, 5, 128, 256, 256)

attn = AxialAttention(
	dim = 128, 			 # embedding dimension
	dim_index = 2,       # where is the embedding dimension
	heads = 8,			 # number of heads for multi-head attention
	num_dimensions = 3,  # number of axial dimensions (images is 2, video is 3, or more)
)

attn(video)
```

## Citation

```bibtex
@misc{ho2019axial,
    title = {Axial Attention in Multidimensional Transformers},
    author = {Jonathan Ho and Nal Kalchbrenner and Dirk Weissenborn and Tim Salimans},
    year = {2019},
    archivePrefix = {arXiv}
}
```