+++
author = "James DeVries"
title = "Fooocus - Running on Macbook Pro M1"
date = "2024-02-24"
description = "How to run Fooocus with improved performance on a M1 Pro Macbook"
tags = [
    "ai", "llm", "image"
]
+++

![Image Closeup image of a chameleon on a black background](chameleon_foocus_dreamshaperXL.png "Generated with prompt: studio photograph closeup of a chameleon over a black background ")

## Making Fooocus Faster:

[Fooocus](https://github.com/lllyasviel/Fooocus) is an image 
generation tool that you can run locally on your own computer. 

Following the installation instructions it does run on a 2021 Macbook Pro with
an M1 Pro processor but the image generation times are slow.

Adding the following parameters improved the speed to 3-4s/it leading to
a complete image in less than a minute using Extreme Speed performance mode.

``` sh
python entry_with_update.py \
    --all-in-fp16 \
    --attention-pytorch \
    --always-high-vram \
    --disable-offload-from-vram
```



Also added following to `config.txt` to enable Extreme Speed mode and show
the Advanced settings by default.
```
    "default_advanced_checkbox": true,
    "default_performance": "Extreme Speed"
```

