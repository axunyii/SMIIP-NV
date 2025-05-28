# SMIIP-NV: A Multi-Annotation Non-Verbal Expressive Speech Corpus

## Dataset Description

SMIIP-NV is a multi-annotated non-verbal expressive speech corpus designed for training and evaluating LLM-based text-to-speech systems. It contains a diverse set of non-verbal sounds (e.g., laughter, crying, coughing) along with emotion labels (happy, sad, neutral, angry, surprised), enabling the synthesis of natural and expressive speech.

**Key Features:**

- **Multi-dimensional annotations:** Detailed emotion and non-verbal sound categories for each clip.
- **Rich non-verbal expressions:** Over 33 hours of audio from 37 speakers, covering laughter, crying, coughing, etc.
- **Precise timestamps:** Start and end times for every non-verbal event for fine-grained control.

This corpus empowers researchers and developers to build more natural and emotionally expressive TTS systems that seamlessly integrate non-verbal cues. 

## Dataset Structure

```plaintext
SMIIP_NV/
├── MIC-0001/
│   ├── neutral/
│   │   ├── annotation.txt
│   │   ├── MIC-0001_0001.wav
│   │   └── ...
│   ├── sad/
│   │   ├── annotation.txt
│   │   ├── MIC-0001_0013.wav
│   │   └── ...
│   ├── surprised/
│   │   ├── annotation.txt
│   │   ├── MIC-0001_0029.wav
│   │   └── ...
│   ├── angry/
│   │   ├── annotation.txt
│   │   ├── MIC-0001_0041.wav
│   │   └── ...
│   └── happy/
│       ├── annotation.txt
│       ├── MIC-0001_0048.wav
│       └── ...
├── MIC-0002/
│   ├── neutral/
│   │   └── ...
│   └── ...
└── ...
```

## 🚀 Demo

We provide both a static preview and an interactive online demonstration:

- **Static Preview:**
  - Visit our demo page: https://axunyii.github.io/SMIIP-NV
- **Interactive Demo:**
  - Live on Hugging Face Spaces: https://huggingface.co/spaces/xunyi/SMIIP-NV_Finetuned_CosyVoice2

## 🛠️ Fine-Tuning CosyVoice2 Process

1. **Clone & Environment Setup**

   ```bash
   git clone https://huggingface.co/xunyi/SMIIP-NV_finetune_CosyVoice2.git
   cd SMIIP-NV_finetune_CosyVoice2
   conda create -n SMIIP_NV_finetune -y python=3.10
   conda activate SMIIP_NV_finetune
   conda install -y -c conda-forge pynini==2.1.5
   pip install -r requirements.txt \
       -i https://mirrors.aliyun.com/pypi/simple/ \
       --trusted-host mirrors.aliyun.com
   ```

2. **Prepare Data**

   - Unzip `SMIIP_NV_SPK_finetune.zip` into `corpus/` under the repository root.

   - Navigate to the example directory:

     ```bash
     cd examples/nv/cosyvoice2
     ```

3. **Run Fine-Tuning**

   - Edit `run.sh`: set `stage=0` and `stop_stage=3` for initial data prep.

   - Execute training:

     ```bash
     bash run.sh
     ```

   - To continue full training, adjust `stop_stage=5` and rerun:

     ```bash
     bash run.sh
     ```

## 🔍 Inference Process

- **Batch Inference:**

  - Set `stage=4` and `stop_stage=4` in `run.sh`, then:

    ```bash
    bash run.sh
    ```

- **Single Utterance Inference:**

  - Use Python script:

    ```bash
    python inference.py
    ```

- **Visualization & Web UI:**

  - Launch the web interface as described below.

## 🖥️ Web UI Implementation

The demo UI is built with [Gradio](https://gradio.app/).

**Start Web UI:**

```bash
python3 webui.py --port 50000 \
    --model_dir pretrained_models/CosyVoice2-0.5B
```

Then open `http://localhost:50000/` in your browser.

## 📜 License & Citation

This project is released under **CC BY-NC-SA 4.0**. Details at https://creativecommons.org/licenses/by-nc-sa/4.0/.

Please cite:

> **SMIIP-NV: A Multi-Annotation Non-Verbal Expressive Speech Corpus**
