# Scribble-Guided Diffusion for Training-free Text-to-Image Generation



Seonho Lee, Jiho Choi, Seohyun Lim, Jiwook Kim, Hyunjung Shim<br>

<br/>


## Setup
```bash
conda create --name highlight-guided python==3.8.0
conda activate highlight-guided
conda install pytorch torchvision torchaudio pytorch-cuda=11.7 -c pytorch -c nvidia

pip install -r environments/requirements_all.txt
# if this does not work, try the following
pip install -r environments/requirements.txt

pip install git+https://github.com/CompVis/taming-transformers.git
pip install git+https://github.com/openai/CLIP.git
```

Download the model [GLIGEN](https://huggingface.co/gligen/gligen-generation-text-box/blob/main/diffusion_pytorch_model.bin) trained with box-grounding tokens with text and put them in `checkpoints/gligen`



## Inference 

To draw a scribble for the guidance:
```bash
python draw_scribble.py
```

To run with user input text prompts:
```bash
python inference.py --ckpt checkpoints/gligen/text-box/diffusion_pytorch_model.bin
```

Configuration files are provided in the `configs` directory. To run the model with the default configuration:
```bash
python inference.py --config configs/config.json
```


## Important Files

```
args.py
data.py
draw_highlight.py
inference.py
losses/loss_config.py
losses/loss_scheduler.py
losses/loss.py
losses/utils.py
scribble_propagation.py
ldm/models/diffusion/plms.py
```


## Acknowledgments

This project is built on the following resources:

- [**Attention Refocusing**](https://github.com/Attention-Refocusing/attention-refocusing): This is the baseline model we used in our paper.

- [**GLIGEN**](https://github.com/gligen/GLIGEN): Our code is built upon the foundational work provided by GLIGEN. 




## Related Works

[BoxDiff: Text-to-Image Synthesis with Training-Free Box-Constrained Diffusion](https://github.com/showlab/BoxDiff)

[Dense Text-to-Image Generation with Attention Modulation](https://github.com/naver-ai/DenseDiffusion)
