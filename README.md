# Cross-Age Speaker Verification

This repository contains the trial files and VoxCeleb1&2 age information of the paper "Cross-Age Speaker Verification: Learning Age-Invariant Speaker Embeddings". Following is the download source. We provide Google Drive Link and Baidu Pan resource. 

|  Files | Download Link | 
|  ----  | ---- |
| Trial files | <a href="https://drive.google.com/drive/folders/1caO11O7xqjpa8KNLrT8BWx_V6IhdmQlQ?usp=sharing">Google Drive Link </a> |
| Vox1 Age info  |  <a href="https://drive.google.com/drive/folders/1x-FipNnDtVd6CLy2CblViphyODj3rFS4?usp=sharing">Google Drive Link </a>  |
| Vox1dev Age info |  <a href="https://drive.google.com/drive/folders/1aSYbdoWp9Pvnbd4y6IRneykSlFneat_I?usp=sharing">Google Drive Link </a>  |

or

Download Link: https://pan.baidu.com/s/1m3lDeAEt0lJj-CPHqM4e1Q 
Passwd: qv90

# 0.Introduction

In this paper, we adopt the face age estimation method to predict the speaker age value from the associated visual data, then label the audio recording with the estimated age. We construct multiple Cross-Age test sets on VoxCeleb (Vox-CA), which deliberately select the positive trials with large age-gap. Finally, we propose an age-decoupling adversarial learning (ADAL) to alleviate the negative effect of the age gap and reduce intra-class variance. 
The main contribution of this paper is:
<ol>
  <li>Propose cross-age speaker verification task</li>
  <li>Proposed an age-decoupling adversarial learning mothod </li>
</ol>

<a href=" ">Paper arxiv </a>  |


# 1.Cross-age speaker verification task
## 1.1 Construction Detail
The construction pipelines adopt the following steps:
<ol>
  <li> Gathering the face image from meta-data of VoxCeleb1 and VoxCeleb2</li>
  <li> Estimating the age of each face image. </li>
  <li> Labeling the estimated age value for each audio utterance.  </li>
  <li> Selecting large age-gap audios as positive pairs and the pairs of same nationality and gender as negative pair  </li>
</ol>

Faces from video -> Face Age Estimation module -> faces age -> age average -> audio age

For the sake of clarity, the key stages are described in the following paragraphs:
**Estimating and labeling age for audio**: We use the Dex to estimate the age for each face image, and the average age value of faces is used as the estimated age for the segment.
**Forming positive/negative pairs**:
First, the positive pairs must be the cross-age case. 
Second, all negative pairs are constructed within the same nationality and gender.
Following the rules mentioned above, there are four VoxCA sets are constructed according to different age-gap categories:
<ol>
  <li> Vox-CA5. The age gap of the positive pair is 5 years at least. The candidate speakers must possess more than 7 years of max age-gap data.</li>
  <li> Vox-CA10. The age gap of the positive pair is 10 years at least. The candidate speakers must possess more than 12 years of max age-gap data.</li>
  <li> Vox-CA15. The age gap of the positive pair is 15 years at least. The candidate speakers must possess more than 17 years of max age-gap data. </li>
  <li> Vox-CA20. The age gap of the positive pair is 20 years at least. The candidate speakers must possess more than 22 years of max age-gap data. </li>
</ol>

## 1.2 Comparsion with Vox-E, Vox-H and Vox-CA
In this part, we consider three cases of trial pairs.
Case 1. Positive pair within intra-segment. The pair audios are selected from the same video segment.
Case 2. Positive pair within the cross-age.
Case 3. Negative pair within the same nationality and gender.

The following table is the statistics of VoxCeleb test trials and our proposed trials. 
![image](https://github.com/qinxiaoyi/Cross-Age_Speaker_Verification/blob/main/imgs/table2.jpg)

The following is the results on different test set based on the ResNet-GSP-ArcFace model. The our-E and our-H is our implemented test set following the VoxCeleb rules.

|  **Test set**    | **Construct**             | **EER[%]**  | **mDCF0.01** | 
|  ----        | ----                  | ----    | ----     |
| **Vox official** |                       |         |          |
| Vox-O        | random                | 0.962%  | 0.100    |
| Vox-E        | random                | 1.094%  | 0.122    |
| Vox-H        | nation & gender       | 1.939%  | 0.200    |
|**our proposed** |                       |         |          |
| our-E        | random                | 1.202%  | 0.123    |
| our-H        | nation & gender       | 2.044%  | 0.192    |
| only-N       | nation                | 1.568%  | 0.164    |
| only-H       | gender                | 1.534%  | 0.146    |
| only-I       | intra-segment         | 0.227%  | 0.015    |
| only-CA5     | age                   | 1.953%  | 0.177    |
| only-CA10    | age                   | 3.437%  | 0.272    |
| only-CA15    | age                   | 5.927%  | 0.352    |
| only-CA20    | age                   | 8.185%  | 0.464    |
| Vox-CA5      | age & nation & gender | 3.407%  | 0.300    |
| Vox-CA10     | age & nation & gender | 4.974%  | 0.370    |
| Vox-CA15     | age & nation & gender | 8.028%  | 0.481    |
| Vox-CA20     | age & nation & gender | 10.419% | 0.646    |

The Vox-CA provides new benchmarks for crossage matching scenarios and hard tasks.


# 2. Learning Age-invariant Speaker Embeddings

![image](https://github.com/qinxiaoyi/Cross-Age_Speaker_Verification/blob/main/imgs/network_ADAL.png)

