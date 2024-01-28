# ERA-CAPSTONE

🤗[**Space Link**](https://huggingface.co/spaces/GunaKoppula/MultiModal-Phi2)

## Phi2 : Pretraining LLM from Scratch
### Details
1. Model used: [Microsoft Phi2](https://huggingface.co/microsoft/phi-2)
2. Dataset used: Tiny Stories dataset(100k samples) & Realtime data(100k samples) from finetuned Phi2 model via Ollama
3. Pretraining approach: Pretraining using QLoRA

### Design
![image](https://github.com/GunaKoppula/ERAV1-CAPSTONE/assets/61241928/ae4525ed-f612-458d-a679-b88100e1d47d)

### Training Loss Curve
![image](https://github.com/GunaKoppula/ERAV1-CAPSTONE/assets/61241928/1692461c-de43-4b50-87d7-bdc0d72b5f69)

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
![image](https://github.com/GunaKoppula/ERAV1-CAPSTONE/assets/61241928/a09cc77d-2cd0-4aa9-ae04-7fea4edbb368)

### Pretraining
#### Training Loss Curve
![image](https://github.com/GunaKoppula/ERAV1-CAPSTONE/assets/61241928/c9e205b9-44aa-4ef3-b7da-f6d69b5f0f2a)

#### Learing Rate
![image](https://github.com/GunaKoppula/ERAV1-CAPSTONE/assets/61241928/a82cf4b6-0cc4-47d9-ad7e-f504677a5074)

#### Training Logs
![image](https://github.com/GunaKoppula/ERAV1-CAPSTONE/assets/61241928/83cbd14a-9626-410c-99be-5757c089c9b2)

### Finetuning
#### Training Loss Curve
![image](https://github.com/GunaKoppula/ERAV1-CAPSTONE/assets/61241928/ceb9d187-14cb-4372-8370-bdbf7f7a3812)

#### Learing Rate
![image](https://github.com/GunaKoppula/ERAV1-CAPSTONE/assets/61241928/5d1fe7b3-5cec-46c8-aaac-a1e3ae5b7f6c)

#### Training Logs
![image](https://github.com/GunaKoppula/ERAV1-CAPSTONE/assets/61241928/3aebd889-d120-466f-8751-9c7e37023ab1)

### Results
![image](https://github.com/RaviNaik/ERA-CAPSTONE/assets/23289802/f12a9f04-df32-413e-b957-774c30381b2b)

### Deployed on HF
#### Text & Image:
![image](https://github.com/RaviNaik/ERA-CAPSTONE/assets/23289802/485a2806-81ac-4229-97ee-87f58af578bc)
![image](https://github.com/RaviNaik/ERA-CAPSTONE/assets/23289802/ae2c14c4-6949-4fff-b2fb-cb37a29eac33)

#### Audio & Image:
**Question Asked: How many people are there in this image?**
![image](https://github.com/RaviNaik/ERA-CAPSTONE/assets/23289802/430310fc-1df9-459c-94f3-32d9691a1035)
![image](https://github.com/RaviNaik/ERA-CAPSTONE/assets/23289802/fd30a864-b289-469a-9c85-b6fd02f486a9)
On HF Space:
![image](https://github.com/RaviNaik/ERA-CAPSTONE/assets/23289802/efefee6e-98ee-4658-b2e9-f18d8f82a234)
