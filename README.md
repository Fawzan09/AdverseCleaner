# AdverseCleaner

The shortest ever code (**16 lines of Python codes**) to remove some [adversarial noise](https://arxiv.org/abs/1412.6572) from images.

It does not even use deep learning.

And I personally think anisotropic filtering methods are more effective than training noise-removal neural networks because convolution operations are essentially non-anisotropic. 

In frequency domain, anisotropic methods are usually more “killing”.

No GPU is needed. Each 1024px image only need less than 3 seconds on my laptop CPU.

# Update

2023 Sep 03: The previous considerations seem unnecessary now after SDXL release – Since SDXL is an architecture only designed for inference (rather than gradient computation) on consumer-level devices, computing gradients of SDXL need 23.5 GB RAM/VARM even in float16 (more than 30GB if float32) and more than 45 seconds each iteration if on CPU (and even CPU gradient will need users to must have 26GB system memory when most users only have 16GB), making adversarial attack nearly impossible on consumer-level devices, plus considering that a robust attack will also need to consider other models like SD 1.5 and Kandinsky 2.2 .

2023 Mar 28: Seems that using guided filter is not safe enough because the guidance already has adversarial noise in it; the guided filter may bring the adversarial noise back. Perhaps a ‘safer’ idea is to use some other things to process the initial anisotropic filtered image. I will try some random ideas when I have free time but it seems that I do not have so much free time recently.

# Run

    conda env create -f environment.yaml
    conda activate advc
    python clean.py

Feel free to take a look at the code to change input images.

# Result

The test image is from [here](https://twitter.com/aifurryart/status/1636208457715187714).

Input (with adversarial noise):

![p](input.png)

Output (removing adversarial noise, 2.13 seconds on my laptop CPU):

![p](output.png)

# Implementations

Thank the community for making more implementations!

[HuggingFace Space](https://huggingface.co/spaces/p1atdev/AdverseCleaner)

[Automatic1111's Webui Plugin (with Script)](https://github.com/gogodr/AdverseCleanerExtension)

[Automatic1111's Webui Plugin (with Tab)](https://github.com/p1atdev/stable-diffusion-webui-adverse-cleaner-tab)
