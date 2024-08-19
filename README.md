# Large Language Models for Enhancing Feature and Structure of Text-Attributed Graphs

## 0. Python environment setup 
```
conda create --name graph-llm python=3.8
conda activate graph-llm

conda install pytorch==2.2.2 torchvision==0.17.2 torchaudio==2.2.2 pytorch-cuda=12.1 -c pytorch -c nvidia
conda install -c pyg pytorch-sparse
conda install -c pyg pytorch-scatter
conda install -c pyg pytorch-cluster
conda install -c pyg pyg
pip install -r requirements.txt
```


## 1. Download TAG datasets
| Dataset | Description |
| ----- |  ---- |
|Citeseer| Download the dataset [here](https://drive.google.com/drive/folders/1eEolZRVIRjgJhxKujauLO26REB3FcmPd?usp=sharing), unzip and move it to `dataset/citeseer`.|
|Cora| Download the dataset [here](https://drive.google.com/drive/folders/1PCQyFUADUikqcgvF3LMVTfDUvJ57dqIY?usp=sharing), unzip and move it to `dataset/cora`.|
|PubMed| Download the dataset [here](https://drive.google.com/drive/folders/1Fo6WPrGRtYo9JdoMBQIQYzPU252n5CDS?usp=sharing), unzip and move it to `dataset/pubmed`.|
| ogbn-arxiv  | Download the dataset [here](https://drive.google.com/drive/folders/1U1De8nabia2Frfu1otqMO4aiv1EEJuH4?usp=sharing), unzip and move it to `dataset/ogbn_arxiv`.|
## 2. Download LLM responses
| Dataset | Description |
| ----- |  ---- |
|Citeseer| Download the dataset [here](https://drive.google.com/drive/folders/1qoU3W3d_nG-i23m_O0W0A95qlwOLETKr?usp=sharing), unzip and move it to `enhance/gpt_responses/citeseer`.|
|Cora| Download the dataset [here](https://drive.google.com/drive/folders/1ZV4aMYQ_PwP2D7fOWTRTZ4KekNJSnFO5?usp=sharing), unzip and move it to `enhance/gpt_responses/cora`.|
|PubMed | Download the dataset [here](https://drive.google.com/drive/folders/1LXKcCmkhEKMUmbnSXIkZxsYkaZ9F7lPN?usp=sharing), unzip and move it to `enhance/gpt_responses/pubmed`.|
| ogbn-arxiv  | Download the dataset [here](https://drive.google.com/drive/folders/19d9sjCyGlC8Ia4RRWUfQEEyL4LI04roj?usp=sharing), unzip and move it to `enhance/gpt_responses/ogbn_arxiv`.|

## 3. Fine-tuning the LMs
### To use the orginal text attributes
```
CUDA_VISIBLE_DEVICES=0 python -m core.trainLM dataset citeseer
```
### To use the GPT responses
```
CUDA_VISIBLE_DEVICES=0 python -m core.trainLM dataset citeseer lm.train.use_gpt True
```
## 4. Training the EdgePredictor
```
python -m core.trainEdge_Predictor dataset citeseer
```
## 5. Training the GNNs
```
python -m core.trainEnsemble dataset citeseer 
```

## 4. Reproducibility

We provide the trained LM `(*.ckpt)`, EdgePredictor `(*_edge_predictor.pth)`, improved node features `(*.emb)` and graph structure `(*_edge.npy)`. Please donwload them [here](https://drive.google.com/drive/folders/1OdD0203mp9PO7NvuiqWki9Klk5nIzDP8?usp=sharing). 
