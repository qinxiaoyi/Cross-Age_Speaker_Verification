# Cross-Age_Speaker_Verification

This repository contains the trial files and VoxCeleb1&2 age information of the paper "Cross-Age Speaker Verification: Learning Age-Invariant Speaker Embeddings" .

|  Files | Download Link |
|  ----  | ---- |
| Trial files | <a href="https://drive.google.com/drive/folders/1caO11O7xqjpa8KNLrT8BWx_V6IhdmQlQ?usp=sharing">Google Drive Link </a> |
| Vox1 Age info  |  <a href="https://drive.google.com/drive/folders/1x-FipNnDtVd6CLy2CblViphyODj3rFS4?usp=sharing">Google Drive Link </a>  |
| Vox1dev Age info |  <a href="https://drive.google.com/drive/folders/1aSYbdoWp9Pvnbd4y6IRneykSlFneat_I?usp=sharing">Google Drive Link </a>  |

The following is the results on different test set based on the ResNet-GSP-ArcFace model.
|  Test set    | Construct             | EER[%]  | mDCF0.01 | 
|  ----        | ----                  | ----    | ----     |
| Vox official |                       |         |          |
| Vox-O        | random                | 0.962%  | 0.100    |
| Vox-E        | random                | 1.094%  | 0.122    |
| Vox-H        | nation & gender       | 1.939%  | 0.200    |
|  ----        | ----                  | ----    | ----     |
| our proposed |                       |         |          |
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
