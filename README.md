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


3. :heavy_check_mark: The output remains text, based on multimodal inputs - text, image, and audio.

4. :heavy_check_mark: The deployment page should look like ChatGPT only, where we can send in images, text, or upload audio (live recording or file).



## Phi2 : Pretraining LLM from Scratch
### Details
1. Model used: [Microsoft Phi2](https://huggingface.co/microsoft/phi-2)
2. Dataset used: Tiny Stories dataset(100k samples) & Realtime data(100k samples) from finetuned Phi2 model via Ollama
3. Pretraining approach: Pretraining using QLoRA


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

```python
class AudioLanguageConnector:
```

- This class prepares and tokenizes audio-related text data using the "microsoft/phi-2" model's tokenizer. The <audio_start> and <audio_end> tokens are added to the input text to provide context for audio-related processing. The tokenized output is then returned as a tensor. This class acts as a connector to process text data in a format suitable for the specified audio model.

```python
class WhisperWithProjection:
```
- This class transcribes audio by encapsulating the necessary steps. It uses a pre-trained model called "openai/whisper-tiny" to convert audio files into text transcriptions.

```python
class MultiModalPhi2:
```
 - This class takes input text, audio, and images and constructs a conversation prompt with appropriate formatting for the model. It tokenizes the prompt, preprocesses the image, and concatenates audio embeddings if available, and generates new tokens using the pre-trained model, considering input modalities.
Decodes and returns the generated output, handling special tokens and potential mismatches.


  
### Pretraining
#### Training Loss Curve and Learning Rate
<img src="https://github.com/GunaKoppula/ERAV1-CAPSTONE/assets/61241928/c9e205b9-44aa-4ef3-b7da-f6d69b5f0f2a.type" width="400">  <img src="https://github.com/GunaKoppula/ERAV1-CAPSTONE/assets/61241928/a82cf4b6-0cc4-47d9-ad7e-f504677a5074.type" width="393">

#### Training Logs
![image](https://github.com/GunaKoppula/ERAV1-CAPSTONE/assets/61241928/83cbd14a-9626-410c-99be-5757c089c9b2)

### Finetuning 
#### Training Loss Curve and Learning Rate
<img src="https://github.com/GunaKoppula/ERAV1-CAPSTONE/assets/61241928/ceb9d187-14cb-4372-8370-bdbf7f7a3812.type" width="388"> <img src="https://github.com/GunaKoppula/ERAV1-CAPSTONE/assets/61241928/5d1fe7b3-5cec-46c8-aaac-a1e3ae5b7f6c.type" width="400">

#### Training Logs
![image](https://github.com/GunaKoppula/ERAV1-CAPSTONE/assets/61241928/3aebd889-d120-466f-8751-9c7e37023ab1)


### Results
![image](https://github.com/GunaKoppula/ERAV1-CAPSTONE/assets/61241928/4b54c0bd-b078-4dc9-932a-49640d0297dc)

### Deployed on HF
#### Text & Image:
![image](https://github.com/GunaKoppula/ERAV1-CAPSTONE/assets/61241928/4a41ada0-3174-413f-86c5-323456168915)

#### Audio & Image:
**Question Asked: Tell me about this image**



### Future Scope:
- Incorporating the original Llava model's finetuning on a larger set of BLIP captions (558k) could lead to significant improvements.
- Using GPTQ or AWQ can reduce latency, making the model more efficient.

