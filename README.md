<!-- # <p align=center>`CTINEXUS: Automatic Cyber Threat Intelligence Knowledge Graph Construction Using Large Language Models`</p>omit in toc -->
<div align="center">
  <img src="app/static/logo.png" alt="Logo" width="200">
  <h1 align="center">Automatic Cyber Threat Intelligence Knowledge Graph Construction Using Large Language Models</h1>
</div>

<p align="center">
  <a href="https://opensource.org/licenses/MIT"><img src="https://img.shields.io/badge/License-MIT-lavender.svg" alt="License: MIT"></a>
  <a href='https://github.com/peng-gao-lab/CTINexus'><img src='https://img.shields.io/badge/Project-Github-pink'></a>
  <a href='https://arxiv.org/abs/2410.21060'><img src='https://img.shields.io/badge/Paper-Arxiv-crimson'></a>  
  <a href='https://ctinexus.github.io/' target='_blank'><img src='https://img.shields.io/badge/Project-Blog-turquoise'></a>
</p>

This is a fork of the [CTINexus demo](https://github.com/peng-gao-lab/CTINexus/) which converts it into a containerized micro-service as a proof-of-concept use case, allowing the user to submit text and return the processed framework results along with a visualization of the graph.  It uses [Gradio](https://www.gradio.app/) for the UI.  Please see their project [here](https://ctinexus.github.io/).
<p align="center">
  <img src="app/static/webapp.png" alt="framework" width="500"/>
</p>


The repository of **CTINexus**, a novel framework leveraging optimized in-context learning (ICL) of large language models (LLMs) for data-efficient CTI knowledge extraction and high-quality cybersecurity knowledge graph (CSKG) construction. CTINexus requires neither extensive data nor parameter tuning and can adapt to various ontologies with minimal annotated examples.
<p align="center">
  <img src="app/static/overview.png" alt="framework" width="500"/>
</p>

## News
🌟 [2025/06/14] Community spotlight — Jeff’s [fork](https://github.com/eljeffeg/CTINexus) turns CTINexus into a containerized micro-service PoC with a Gradio UI. Submit text and instantly see the extracted intel and interactive graph!

🔥 [2025/04/21] We released the camera-ready paper on [arxiv](https://arxiv.org/pdf/2410.21060). 

🔥 [2025/02/12] CTINexus is accepted at 2025 IEEE European Symposium on Security and Privacy ([Euro S&P](https://eurosp2025.ieee-security.org/index.html)).


## Introduction
CTINexus composes of the following modules: 
* [IE](IE): A carefully designed automatic prompt construction strategy with optimal demonstration retrieval for extracting a wide range of cybersecurity entities and relations;
* A hierarchical entity alignment technique that canonicalizes the extracted knowledge and removes redundancy; 
   * [ET](ET): Groups mentions of the same type.
   * [EM](EM): Merges mentions referring to the same entity with IOC protection.
* [LP](LP): An long-distance relation prediction technique to further complete the CSKG with missing links.



## Quick Start

### 1. Prerequisites
```bash
pip install -r requirements.txt
```

### 2. Cybersecurity Triplet Extraction
1. Update the [configuration file](IE/config/example.yaml). To use the optimal settings, simply insert your `OpenAI API key`.
2. Run the following script to perform triplet extraction:
   ```bash
   sh tools/scripts/ie.sh
   ```

### 3. Hierarchical Entity Alignment
#### 3.1 Course-grained Entity Typing
1. Update the [configuration file](ET/config/example.yaml). To use the optimal settings, simply insert your `OpenAI API key`.
2. Run the following script to perform triplet extraction:
   ```bash
   sh tools/scripts/et.sh
   ```

#### 3.2 Fine-grained Entity Merging
1. Update the configuration files ([config1](EM/config/example.yaml), [config2](EM/postprocess/config/example.yaml)). To use the optimal settings, simply insert your `OpenAI API key`.
2. Run the following script to perform entity alignment:
   ```bash
   sh tools/scripts/em.sh
   ```

### 4. Long-Distance Relation Prediction
1. Update the [configuration file](LP/config/example.yaml). To use the optimal settings, simply insert your `OpenAI API key`.
2. Run the following script to predict long-distance relations:
   ```bash
   sh tools/scripts/lp.sh
   ```


## Citation
```
@inproceedings{cheng2025ctinexusautomaticcyberthreat,
      title={CTINexus: Automatic Cyber Threat Intelligence Knowledge Graph Construction Using Large Language Models}, 
      author={Yutong Cheng and Osama Bajaber and Saimon Amanuel Tsegai and Dawn Song and Peng Gao},
      booktitle={2025 IEEE European Symposium on Security and Privacy (EuroS\&P)},
      year={2025},
      organization={IEEE}
}
```

## License
The source code is licensed under the [MIT](LICENSE.txt) License. 
We warmly welcome industry collaboration. If you’re interested in building on CTINexus or exploring joint initiatives, please email yutongcheng@vt.edu—we’d be happy to set up a brief call to discuss ideas.