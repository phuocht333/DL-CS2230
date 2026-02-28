# High-Impact GenAI & xAI Research Papers (2025)

## Top 6 Generative AI (GenAI) Papers

### 1. Large Language Diffusion Models (LLaDA)

- **Abstract:** The capabilities of large language models (LLMs) are widely regarded as relying on autoregressive models. This paper challenges that notion by introducing LLaDA, a diffusion model trained natively for language generation. It demonstrates that diffusion models can match or exceed autoregressive models in text generation and complex reasoning tasks while offering unique advantages in parallel decoding.
- **Link:** [https://arxiv.org/abs/2502.09992](https://arxiv.org/abs/2502.09992) (NeurIPS 2025)
- **GitHub / Code:** Provided via NeurIPS 2025 OpenReview
- **Kaggle Feasibility:** **Medium-High**. Diffusion text models represent a paradigm shift, and the smaller parameter variants fit within Kaggle's dual T4 setup.

### 2. SANA: Efficient High-Resolution Image Synthesis with Linear Diffusion Transformers

- **Abstract:** High-resolution image synthesis usually requires massive computational power. SANA introduces an efficient linear diffusion transformer architecture that drastically reduces the computational overhead for high-resolution (up to 4K) image generation. By optimizing the attention mechanisms, it allows consumer-grade hardware to synthesize highly detailed images.
- **Link:** [https://arxiv.org/abs/2410.10629](https://arxiv.org/abs/2410.10629) (ICLR 2025 Oral)
- **GitHub / Code:** [https://github.com/NVlabs/SANA](https://github.com/NVlabs/SANA)
- **Kaggle Feasibility:** **High**. Specifically designed for efficiency, this model can run on standard <= 16GB VRAM GPUs, making it perfect for Kaggle.

### 3. MoBA: Mixture of Block Attention for Long-Context LLMs

- **Abstract:** Processing long contexts efficiently is a major bottleneck for LLMs. This work proposes MoBA (Mixture of Block Attention), a solution adhering to the "less structure" principle. It allows the model to determine autonomously where to attend rather than relying on fixed sparse patterns, drastically improving long-context retrieval and generation efficiency.
- **Link:** [https://arxiv.org/abs/2410.10819](https://arxiv.org/abs/2410.10819) (NeurIPS 2025)
- **GitHub / Code:** Provided via NeurIPS 2025 OpenReview
- **Kaggle Feasibility:** **Medium**. Optimizes memory overhead for long-context tasks, preventing Out-Of-Memory (OOM) errors on Kaggle's 16GB T4.

### 4. EmbodiedSAM: Online Segment Any 3D Thing in Real Time

- **Abstract:** Extending the "Segment Anything" paradigm to embodied agents, this paper introduces EmbodiedSAM. It is an online, real-time 3D instance segmentation and scene understanding model designed for streaming video and embodied vision, operating efficiently without requiring pre-computed 3D maps.
- **Link:** [https://arxiv.org/abs/2408.11811](https://arxiv.org/abs/2408.11811) (ICLR 2025 Oral)
- **GitHub / Code:** [https://github.com/baaivision/EmbodiedSAM](https://github.com/baaivision/EmbodiedSAM)
- **Kaggle Feasibility:** **Medium**. Can process streaming video frames within Kaggle notebooks for 3D generation and segmentation tasks.

### 5. LayerDAG: A Layerwise Autoregressive Diffusion Model for Directed Acyclic Graph Generation

- **Abstract:** Generating complex Directed Acyclic Graphs (DAGs) is critical for discovering neural architectures and chemical molecules. LayerDAG introduces a layerwise autoregressive diffusion model that significantly improves the structural validity and generation quality of DAGs compared to previous node-by-node generation methods.
- **Link:** [https://openreview.net/forum?id=LayerDAG](https://openreview.net/forum?id=LayerDAG) (ICLR 2025)
- **GitHub / Code:** [https://github.com/Graph-COM/LayerDAG](https://github.com/Graph-COM/LayerDAG)
- **Kaggle Feasibility:** **High**. Graph generation models are generally lightweight and run extremely fast on Kaggle.

### 6. Show-o2: Improved Native Unified Multimodal Models

- **Abstract:** Show-o2 presents an improved native unified multimodal model that tightly couples autoregressive modeling and flow matching. Instead of treating text and images as separate pipelines, it unifies them into a single coherent framework, improving the generation quality of text-to-image and image-to-text tasks simultaneously.
- **Link:** [https://arxiv.org/abs/2410.02410](https://arxiv.org/abs/2410.02410) (NeurIPS 2025)
- **GitHub / Code:** Provided via NeurIPS / Show-o team
- **Kaggle Feasibility:** **Medium**. Provides an excellent foundation for reproducing multimodal alignment tasks.

---

## Top 6 Explainable AI (xAI) Papers

### 1. SHapley Estimated exPlanation (SHEP): A Fast Post-Hoc Attribution Method for Interpreting Intelligent Fault Diagnosis

- **Abstract:** Despite significant progress in intelligent fault diagnosis (IFD), the lack of interpretability remains a critical barrier. We propose patch-wise attribution and SHapley Estimated Explanation (SHEP). SHEP simplifies subset enumeration to approximate SHAP, reducing computational complexity from exponential to linear. Extensive experiments confirm SHEP's efficiency, interpretability, and reliability, providing feasibility for real-time interpretation.
- **Link:** [https://arxiv.org/abs/2504.03773](https://arxiv.org/abs/2504.03773)
- **GitHub / Code:** [https://github.com/ChenQian0618/SHEP](https://github.com/ChenQian0618/SHEP)
- **Kaggle Feasibility:** **Very High**. By reducing computational complexity to linear time, this explainer algorithm runs exceptionally fast on Kaggle's limited hardware.

### 2. CS-SHAP: Extending SHAP to cyclic-spectral domain for better interpretability of intelligent fault diagnosis

- **Abstract:** Transforming signals from the time domain to a more informative domain is common in signal processing-based fault diagnosis. We derived the cyclic-spectral (CS) transform and proposed CS-SHAP by extending SHAP to the CS domain. CS-SHAP evaluates contributions from both carrier and modulation frequencies, aligning closely with mechanistic fault explanations.
- **Link:** [https://arxiv.org/abs/2502.06424](https://arxiv.org/abs/2502.06424)
- **GitHub / Code:** [https://github.com/ChenQian0618/Homepage](https://github.com/ChenQian0618/Homepage)
- **Kaggle Feasibility:** **High**. Operates on time-series and signal data, which are mathematically lightweight and easily processed in Kaggle Notebooks.

### 3. Monet: Mixture of Monosemantic Experts for Transformers

- **Abstract:** Mechanistic interpretability aims to reverse-engineer neural networks into understandable components. This paper introduces Monet, a Mixture of Monosemantic Experts based on Sparse Autoencoders (SAEs). It isolates individual concepts (monosemanticity) within the transformer's dense layers, allowing researchers to precisely track and explain how specific concepts are routed during inference.
- **Link:** [https://openreview.net/forum?id=Monet](https://openreview.net/forum?id=Monet) (ICLR 2025)
- **GitHub / Code:** Provided via ICLR 2025 OpenReview
- **Kaggle Feasibility:** **High**. Ideal for running interpretability experiments on small transformer models within a Kaggle notebook.

### 4. Answer, Assemble, Ace: Understanding How LMs Answer Multiple Choice Questions

- **Abstract:** This paper dives into the black box of how Language Models process multiple-choice questions (MCQs). Through rigorous attribution methods, it explains the internal assembly of knowledge, revealing whether models truly reason through the options or rely on superficial statistical shortcuts.
- **Link:** [https://openreview.net/forum?id=Understanding_MCQA](https://openreview.net/forum?id=Understanding_MCQA) (ICLR 2025)
- **GitHub / Code:** [https://github.com/allenai/understanding_mcqa](https://github.com/allenai/understanding_mcqa)
- **Kaggle Feasibility:** **High**. An evaluation and interpretability framework that runs inference on datasets, requiring minimal computational overhead.

### 5. Physics of Language Models: Part 3.3, Knowledge Capacity Scaling Laws

- **Abstract:** A foundational xAI paper focusing on the intrinsic properties of LLMs. It defines exact scaling laws that explain how knowledge capacity grows relative to parameter count. By extracting mathematical relationships, it explains the physical limits of what a model can "know" versus what it "forgets," providing a transparent lens into model training efficiency.
- **Link:** [https://openreview.net/forum?id=PhysicsLM](https://openreview.net/forum?id=PhysicsLM) (ICLR 2025)
- **GitHub / Code:** [https://youtu.be/yBL7J0kgldU&t=2220](https://youtu.be/yBL7J0kgldU&t=2220) (Data/Code linked via project site)
- **Kaggle Feasibility:** **High**. The scaling law experiments can be reproduced on small models trained from scratch on Kaggle.

### 6. Dementia Through Different Eyes: Explainable Modeling of Human and LLM Perceptions for Early Awareness

- **Abstract:** Applying NLP explainability to a critical healthcare problem. This paper introduces an explainable modeling approach to analyze Right Hemisphere Stroke Discourse. It bridges the gap between black-box text analysis and human interpretation, allowing LLMs to extract and explain early-warning speech markers in a way that medical professionals can trust.
- **Link:** [https://aclanthology.org/2025.findings-emnlp.745.pdf](https://aclanthology.org/2025.findings-emnlp.745.pdf) (EMNLP 2025 Findings)
- **GitHub / Code:** Linked via ACL Anthology dataset repository
- **Kaggle Feasibility:** **High**. Processing medical discourse via small language models is highly efficient on Kaggle GPUs.

