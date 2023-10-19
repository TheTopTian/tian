---
layout: page
title:  Stable diffusion
description: Use stable diffusion on medical images
img: assets/img/stable_diffusion/title.png
importance: 1
category: work
---
## Dataset
I used two public datasets **MIMIC CXR** and **CheXpert**. I created the prompts myself based on the labels.

***
## Normal Stable Diffusion.

I tried to use the normal stable diffusion model to keep training, the result was really terrible. The images looked like some chest x-rays but as we all know human's ribs didn't look like that. Then I realized that the model was always keeping finding to best tokens to regenerate your images input, but since the original dataset they used didn't have so many medical images, it was impossible for the model to generate the images we wanted.

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/stable_diffusion/Normal_stable_diffusion_result.png" class="img-fluid rounded z-depth-1" zoomable=true%}
    </div>
</div>

***
## DreamBooth

After 20000 training iterations, you could see from the images below that most of the generated images were laterals. As long as the machine could tell the difference between frontal and lateral images, it could also tell the difference between different diseases then.

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/stable_diffusion/Different_iterations.png" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
</div>

These are the images generated with different diseases' prompts:

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/stable_diffusion/Different_diseases_2000_iterations.png" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
</div>

I also tried the eyeball dataset as well, but I couldn't tell the difference between the RG and NRG myself. :joy: 

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/stable_diffusion/RG_NRG.png" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
</div>

***
## The main difference in code
The main difference inside the code is that **Stable Diffusion** trained the text_encoder but **DreamBooth** trained the unet part.

### Stable diffusion

{% raw %}
```python
# Move vae and Unet to device
vae.to(accelerator.device)
unet.to(accelerator.device)
# Keep vae and Unet in eval model as we don't train these
vae.eval()
unet.eval()
-------------------------
for epoch in range(num_train_epochs):
    text_encoder.train()
    ...
```
{% endraw %}

### DreamBooth

{% raw %}
```python
# Move text_encoder and vae to gpu
text_encoder.to(accelerator.device)
vae.to(accelerator.device)
-------------------------
for epoch in range(num_train_epochs):
    unet.train()
    ...
```
{% endraw %}

***
## AUC of Generated Images

I wanted to use the generated images to build a dataset and compared the classification performance between it and the original dataset. The accuracy of generated images were all higher compared with the original-images but the mean AUC was 10 percent lower. Only the disease Edema's AUC was higher. 

<table border="1">
 <colgroup>
    <col width="150">
    <col width="150">
    <col width="150">
    <col width="150">
    <col width="150">
    <col width="150">
 </colgroup>
 <tr> 
    <th>AUC (Best)</th>
    <th>Cardiomegaly</th>
    <th>Edema</th>
    <th>Consolidation</th>
    <th>Atelectasis</th>
    <th>Pleural Effusion</th>
  </tr>
  <tr>
    <td>Original images</td>
    <td>0.737</td>
    <td>0.8449</td>
    <td>0.8021</td>
    <td>0.7603</td>
    <td>0.7967</td>
  </tr>
  <tr> 
    <td>50000 iterations</td>
    <td>0.6215</td>
    <td>0.8754</td>
    <td>0.5716</td>
    <td>0.405 (Lowest)</td>
    <td>0.7435</td>
 </tr>
 <tr> 
    <td>30000 iterations</td>
    <td>0.6167</td>
    <td>0.88</td>
    <td>0.2762 (Lowest)</td>
    <td>0.2849 (Lowest)</td>
    <td>0.8169</td>
 </tr>
</table>