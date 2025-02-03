# SignLLM: Sign Languages Production Large Language Models

---

## The main Contributions in this work

- A new multilingual Dataset for 8 Sign Languages. <mark>Prompt2Sign</mark>
  
- The first Multilingual Sign Production model. <mark>SignLLM</mark>
  

---

## Abstract

- The authors proposed the first multilingual sign language dataset named "Prompt2Sign", which has built from public data including American Sign Language and Seven others.
  
- The authors claimed that their dataset transform vast amount of videos into a streamlined model-friendly format, optimized for training with translation models like seq2seq and text2text.
  
- Building on this new dataset, the authors proposed **SignLLM** the first multilingual sign languge production model (SLP) which includes two novel multilingual SLP modes that allow for the generation of sign language gesture from input text or prompt.
  

---

## Introduction

- Deep Learning -based Sign Language Production approached typically involves sequential steps
  
  - From text to gloss
    
  - From gloss to pose
    
  - Rendering Pose Videos into more engaing human-like avatar videos.
    

- By proposing the new "**Prompt2Sign**" dataset, the authors tried to tackle different problems
  
  - The existing dataset contains complex formats files including images, scripts, OpenPose skeletal keypoints and graph (or possibly other preprocessing formats)
    
  - The existing data formats lacks actionable information that can be directly trained.
    
  - Manual annotation for gloss is labor-intensive and time-consuming.
    
  - Some of the Sign videos datasets have been obtained from Sign Language Professionals which makes scaling these datasets up is challenging.
    

- <mark>Major Components of the **Prompt2Sign** dataset</mark>.
  
  ![](file:///C:/Users/Microsoft/AppData/Roaming/marktext/images/2024-12-31-03-54-12-image.png?msec=1738599800580)
  
  - **Text**
    
  - **Prompt**
    
  - **Data of Keypoints :** is the posture data that has been reprocessed, which is more useful data that is suitable for training.
    
  - **Frames of Videos**
    

- <mark>**Creating this dataset** </mark>
  
  - The orignal material of this dataset is the **Frames of Video** , the Corresponding **Text**.
    
  - The authors first used the **OpenPose** to for video processing to standardize pose information of video frames into their predefined formats.
    
  - The authors stored the results of the OpenPose in their standaradized format (**Data of Keypoints**) to reduce redandancy and facilitate future model's training.
    
  - The authors reduced the reliance on the manual annotations by auto-creating **prompt** words to improve cost-effectiveness.
    

- By proposing the new "**SignLLM**" model, the authors tried to tackle different problems
  
  - Different sign language data can't be concurrently be trained due to the differences in the sign language of the different countries.
    
  - Handling more languages and large dataset results in slow and challenging training process, so is neccessary to explore high-speed training methods.
    
  - The existing model structure can't grasp more language and more complex natural human conversational input. in other words the model structure can't understand prompt.
    

- <mark>SignLLM</mark>
  
  - Based on their new Prompt2Sign dataset, the authors built the SignLLM, which is the first multilingual model.
    
  - SignLLM produce the sign language skeletal poses of 8 languages from input text of prompt.
    
  - The SignLLM model has two modes:
    
    - Multi-language Switching framework. (**MLSF**)
      
      - which allows multiple sign languages production in parallel by dynamically adding encoder-decoder groups.
    - Prompt2LangGloss
      
      - allowing SignLLM to support static single-set encoder-decoder generation.
  - Two modes for two different usecases:
    
    - The **MLSF** is to acheive efficient multilingual Sign Language Production without causing semantic confusion.
      
    - The **Prompt2LangGloss** is a user-friendly multilingual sign language production mode that aims to understand more complex natural language input.
      
- ![](file:///C:/Users/Microsoft/AppData/Roaming/marktext/images/2024-12-31-05-53-25-image.png?msec=1738599800581)
  
- **As the figure shows**
  
  - The figure represent the input and the output of the SignLLM model.
    
  - As mentioned earlier, the model has two modes :
    
    - For the First mode : (**Multi-Language switching framework**) , the input is (**text**)
      
    - For the second mode : (**Prompt2LangGloss**) the input is (**Prompt**)
      

- To address the problem of the extended training time caused by more languages and larger datasets, the authors presented a **new loss function with a unique module based on Reinforcement learning concept**to accelerate the training process of models on more languages and larger datasets.

---

## The Contribution of this paper can be summarized as:

- **The first comprehensive multilingual sign language dataset: Prompt2Sign.**
  
  - more vocab
    
  - eight languages
    
  - accommodates a greate varaity of models.
    
  - accompanying tools that facilitate the automate/clean sign language processing.
    
- **The first large sign language production model: SignLLM**.
  
  - it has two modes to for more accuratly generating and understanding complex inputs in two use cases, respectively.
- **A novel Loss function, accompanied by a corresponding functional module**.
  
  - it was introduced as a training strategy based on reinforcement learning in sign language, aiming to reduce time cost in training.

---

## Related Work

- The authors claimed that most of the research work in the recent years only focus on sign language recognition and translation.
  
- The authors claimed that the data preprocessing involved in sign language research is highly complex. that is why the one of the main contribution in this study was to standardize the processing to address challenges related to data collection, utilization, and storage.
  

---

## The new Dataset: Prompt2Sign

- The authors claimed that the mismatch between the sign language translation and the sign language productions models can lead to complex challenges:
  
  - The results of the sign language translation can't be used as a training data for the sign language production model.
    
  - The results of the sign language production can't be used as an input to the sign language translation, as evaluation experiments must be conducted first.
    
  - The output of the Sign language production is not suitable as input for the most style transfer models.
    

---

## Data Collection

1. downloading sign language videos of a specific language
  
2. editing and aligning those videos
  
3. use OpenPose to extract each frame of them into :
  
  1. 2D keypoint json files : serve as an input for the standardized data preprocessing pipeline inplemented by the authors.
    
  2. and 2D visualized videos
    

- The key steps of the standardized data preprocessing tool that the author implemented.
  
  - Json (2D keypoints) to h5
    
  - h5 to txt (3D keypoints)
    
  - txt to skels (standard pose storage, data of keypoints)
    

---

## The model: SignLLM