# ERA-CAPSTONE

🤗[**Space Link**](https://huggingface.co/spaces/GunaKoppula/MultiModal-Phi2)


### Tasks:

1. Make a multi-modal LLM that can take these inputs: 

      - :heavy_check_mark: Text
      - :heavy_check_mark: Image
      - :heavy_check_mark: Audio

2. Training:
   
      - Image:

          :heavy_check_mark: Use the original Instruct 150k dataset, and use CLIP to get the image embeddings.
        
          :heavy_check_mark: Add projection layer from this CLIP embeddings to something that can be fed to Phi Model.
        
          :heavy_check_mark: Add an adapter to train (QLoRa) on the instruct 150k dataset.

      - Audio:
        
          :heavy_check_mark: Need to use Whisper to perform ASR.
        
          :heavy_check_mark: Add a projection layer for whisper output.

      - Text:
        
          :heavy_check_mark: Give any text to generate the related details.


3. :heavy_check_mark: The output remains text.

4. :heavy_check_mark: Deployment page should look like ChatGPT only, where we can send in images, text, or upload audio (live recording or file).



## Phi2 : Pretraining LLM from Scratch
### Details
1. Model used: [Microsoft Phi2](https://huggingface.co/microsoft/phi-2)
2. Dataset used: Tiny Stories dataset(100k samples) & Realtime data(100k samples) from finetuned Phi2 model via Ollama
3. Pretraining approach: Pretraining using QLoRA

### Design
<img src="https://github.com/GunaKoppula/ERAV1-CAPSTONE/assets/61241928/ae4525ed-f612-458d-a679-b88100e1d47d.type" width="500">

### Training Loss Curve
<img src="https://github.com/GunaKoppula/ERAV1-CAPSTONE/assets/61241928/1692461c-de43-4b50-87d7-bdc0d72b5f69.type" width="500">

### Training Logs
![image](https://github.com/GunaKoppula/ERAV1-CAPSTONE/assets/61241928/2672a350-7786-4773-b1bc-ea99a3e7091c)


## Phi2 : Multimodal Finetuning
### Details
1. LLM Backbone: [Phi2](https://huggingface.co/microsoft/phi-2)
2. Vision Tower: [clip-vit-large-patch14-336](https://huggingface.co/openai/clip-vit-large-patch14-336)
3. Audio Model: [Whisper Tiny](https://huggingface.co/openai/whisper-tiny)
4. Pretraining Dataset: [LAION-CC-SBU dataset with BLIP captions(200k samples)](https://huggingface.co/datasets/liuhaotian/LLaVA-Pretrain)
5. Finetuning Dataset: [Instruct 150k dataset based on COCO](https://huggingface.co/datasets/liuhaotian/LLaVA-Instruct-150K)

### Design
<img src="https://github.com/GunaKoppula/ERAV1-CAPSTONE/assets/61241928/a09cc77d-2cd0-4aa9-ae04-7fea4edbb368.type" width="500">

### Pretraining
#### Training Loss Curve
<img src="https://github.com/GunaKoppula/ERAV1-CAPSTONE/assets/61241928/c9e205b9-44aa-4ef3-b7da-f6d69b5f0f2a.type" width="500">

#### Learning Rate
<img src="https://github.com/GunaKoppula/ERAV1-CAPSTONE/assets/61241928/a82cf4b6-0cc4-47d9-ad7e-f504677a5074.type" width="500">

#### Training Logs
<img src="https://github.com/GunaKoppula/ERAV1-CAPSTONE/assets/61241928/83cbd14a-9626-410c-99be-5757c089c9b2.type" width="500">

### Finetuning 
#### Training Loss Curve
<img src="https://github.com/GunaKoppula/ERAV1-CAPSTONE/assets/61241928/ceb9d187-14cb-4372-8370-bdbf7f7a3812.type" width="500">

#### Learning Rate
<img src="https://github.com/GunaKoppula/ERAV1-CAPSTONE/assets/61241928/5d1fe7b3-5cec-46c8-aaac-a1e3ae5b7f6c.type" width="500">

#### Training Logs
![image](https://github.com/GunaKoppula/ERAV1-CAPSTONE/assets/61241928/3aebd889-d120-466f-8751-9c7e37023ab1)

















### Results
![image](https://github.com/RaviNaik/ERA-CAPSTONE/assets/23289802/f12a9f04-df32-413e-b957-774c30381b2b)

### Deployed on HF
#### Text & Image:
![image](https://github.com/RaviNaik/ERA-CAPSTONE/assets/23289802/485a2806-81ac-4229-97ee-87f58af578bc)

#### Audio & Image:
**Question Asked: How many people are there in this image?**
![image](https://github.com/RaviNaik/ERA-CAPSTONE/assets/23289802/430310fc-1df9-459c-94f3-32d9691a1035)
