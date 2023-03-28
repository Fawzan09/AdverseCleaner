# AdverseCleaner

The shortest ever code (**16 lines of Python codes**) to remove some [adversarial noise](https://arxiv.org/abs/1412.6572) from images.

It does not even use deep learning.

And I personally think anisotropic filtering methods are more effective than training noise-removal neural networks because convolution operations are essentially non-anisotropic. 

In frequency domain, anisotropic methods are usually more “killing”.

No GPU is needed. Each 1024px image only need less than 3 seconds on my laptop CPU.

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
