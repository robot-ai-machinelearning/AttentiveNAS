# AttentiveNAS: Improving Neural Architecture Search via Attentive Sampling
This repository contains PyTorch evaluation code, training code and pretrained models for AttentiveNAS. 

For details see [AttentiveNAS: Improving Neural Architecture Search via Attentive Sampling](https://arxiv.org/pdf/2011.09011.pdf "AttentiveNAS: Improving Neural Architecture Search via Attentive Sampling") by Dilin Wang, Meng Li, Chengyue Gong and Vikas Chandra.

If you find this project useful in your research, please consider cite:

```BibTex
@article{wang2020attentivenas,
  title={AttentiveNAS: Improving Neural Architecture Search via Attentive Sampling},
  author={Wang, Dilin and Li, Meng and Gong, Chengyue and Chandra, Vikas},
  journal={arXiv preprint arXiv:2011.09011},
  year={2020}
}
```

## Pretrained models and data 
Download our [pretrained AttentiveNAS models](https://drive.google.com/file/d/1cCla-OQNIAn-rjsY2b832DuP59ZKr8uh/view?usp=sharing) and a [(sub-network, FLOPs) lookup table](https://drive.google.com/file/d/1ZYeKDoxg8ELFJUtAIEJoH1iJ8eANKpDB/view?usp=sharing) from Google Drive and put them under folder *./attentive_nas_data*

## Evaluation 
To evaluate our pre-trained AttentiveNAS models, from AttentiveNAS-A0 to A6, on ImageNet val with a single GPU, run:

```python
python test_attentive_nas.py --config-file ./configs/eval_attentive_nas_models.yml --model a[0-6]
```

Expected results:

| Name  | MFLOPs  | Top-1 (%) |
| :------------ |:---------------:| -----:|
| AttentiveNAS-A0      | 203 | 77.3 |
| AttentiveNAS-A1     | 279 | 78.4 |
| AttentiveNAS-A2     | 317 | 78.8 |
| AttentiveNAS-A3    | 357 | 79.1 |
| AttentiveNAS-A4     | 444 | 79.8 |
| AttentiveNAS-A5     | 491 | 80.1 |
| AttentiveNAS-A6     | 709 | 80.7 |


## Training
To train our AttentiveNAS models from scratch, run
```
python train_supernet.py --config-file configs/train_attentive_nas_models.yml --machine-rank ${machine_rank} --num-machines ${num_machines} --dist-url ${dist_url}
```
We adopt SGD training on 64 GPUs. The mini-batch size is 32 per GPU; all training hyper-parameters are specified in [train_attentive_nas_models.yml](configs/train_attentive_nas_models.yml). 

## License 
The majority of AttentiveNAS is licensed under CC-BY-NC, however portions of the project are available under separate license terms: Once For All is licensed under the Apache 2.0 license.

## Contributing 
We actively welcome your pull requests! Please see [CONTRIBUTING](CONTRIBUTING.md) and [CODE_OF_CONDUCT](CODE_OF_CONDUCT.md) for more info.



