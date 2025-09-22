<p align="center">
  <img src="https://miro.medium.com/v2/resize:fit:1200/1*Zd6-LUzmkhuaBWAXVjZ1CQ.png" alt="EEG Signals">
</p>

### Motor Imagery EEG Classification with CSP and EEGNet (BCI-IV 2a)

This project presents the development and evaluation of deep learning models for classifying motor imagery (MI) EEG signals into four categories: left hand, right hand, feet, and tongue. The complete workflow demonstrates the full data science pipeline, beginning with EEG preprocessing and epoching, moving through model development with EEGNet and CSP + EEGNet, and concluding with thorough evaluation and interpretation of the results. The goal is to illustrate a practical EEG-based brain–computer interface (BCI) pipeline, showing how hybrid approaches can improve classification performance and interpretability.

### Overview

Accurate decoding of motor imagery EEG is a central challenge in brain–computer interfaces, with direct applications in neuroprosthetics, rehabilitation, and assistive communication systems. Traditional pipelines often rely on handcrafted features such as Common Spatial Patterns (CSP) combined with linear classifiers, but these methods typically achieve moderate performance and struggle with generalization across subjects. Deep learning models like EEGNet offer improved feature extraction but may be sensitive to limited data and inter-subject variability.  

This project addresses these challenges by comparing baseline EEGNet models with a hybrid CSP + EEGNet approach on the BCI Competition IV-2a dataset. The results show that subject-specific models significantly outperform pooled models, and that integrating CSP features into EEGNet yields substantial accuracy gains, supporting the value of hybrid pipelines for EEG classification.

### Getting Started

To run this project on your own machine, begin by cloning or downloading the repository. Ensure that Python 3.10+ (or a compatible Python 3.x version) is installed, then install all necessary dependencies using the included [requirements.txt file](https://github.com/HamiHekmati/motor-imagery-eeg-classification/blob/main/requirements.txt) with the command  

<pre> ``` pip install -r requirements.txt ``` </pre>  

Once your environment is set up, open the Jupyter notebook file [Motor_Imagery_EEG_Classification.ipynb](https://github.com/HamiHekmati/motor-imagery-eeg-classification/blob/main/Motor_Imagery_EEG_Classification.ipynb) in Jupyter Notebook, JupyterLab, or upload it to Google Colab for a cloud-based workflow. Adjust dataset paths to match the location of your BCI Competition IV-2a dataset files. Run all notebook cells in sequence to reproduce preprocessing, model training, and evaluation. This setup enables you to fully reproduce the analysis, interpret the results, and experiment with your own modifications.

### Dataset

The dataset used in this project is [BCI Competition IV-2a](https://bbci.de/competition/iv/), a benchmark dataset for motor imagery BCI research. It contains EEG recordings from nine healthy subjects, each performing four distinct motor imagery tasks: left hand, right hand, feet, and tongue.  

Recordings were made with 22 EEG channels at a sampling rate of 250 Hz, along with three EOG channels for ocular artifact detection. Each subject contributed 288 trials per session, across two sessions, resulting in 576 trials per subject. Trials were labeled with standardized event codes, and trials flagged as contaminated were excluded from analysis.  

This dataset is widely used because it is both challenging and realistic: it involves four-class classification, contains noise and artifacts, and exhibits strong inter-subject variability, making it well-suited for evaluating advanced BCI methods.

### Project Workflow

The workflow begins with EEG preprocessing and epoching. Signals are band-pass filtered (8–30 Hz) to isolate motor-related rhythms in the alpha and beta frequency bands, ocular channels are removed, and data are mapped to the 10–20 electrode system. Each trial is segmented into a 0.5–3.5 second post-cue window and standardized via z-scoring.  

Two classification strategies are implemented. The first uses EEGNet, a compact convolutional neural network designed for EEG, which captures temporal, spatial, and separable features of the signals. The second uses a hybrid approach where CSP features are extracted per subject and concatenated with the raw EEG input before passing into EEGNet, improving discriminative power and interpretability.  

Training is performed in two modes: pooled training across all subjects with cross-validation, and subject-specific training with an 80/20 split. Performance is evaluated with accuracy, precision, recall, F1-score, and confusion matrices, alongside visualization of training loss and accuracy curves.

### Key Features & Techniques

This project features a full EEG preprocessing pipeline, integration of CSP for interpretable spatial filtering, and a deep learning classifier optimized for EEG data. The hybrid CSP + EEGNet pipeline demonstrates how classical feature extraction can complement deep learning to improve classification robustness. Results are transparently presented with plots of training curves and confusion matrices, and the code is structured to ensure reproducibility and flexibility for future extensions.

### Results

In pooled training across all nine subjects, classification accuracy averaged only 25–35%, near chance level, highlighting the challenge of cross-subject generalization. In contrast, subject-specific models performed much better. EEGNet alone achieved accuracies in the range of 50–70% depending on the subject, while CSP + EEGNet consistently outperformed EEGNet, boosting accuracy by 10–40% and enabling several subjects to reach 80% or higher.  

These results confirm that individualized pipelines are far more reliable for MI-EEG classification than pooled models, and that hybrid CSP + deep learning approaches offer a strong path forward for robust BCI systems.

### Contact

For questions, suggestions, or collaboration opportunities, please reach out via [LinkedIn](https://www.linkedin.com/in/hami-hekmati-399932154/) or by opening an issue in this repository. This project was developed by Hami Hekmati as part of a data science and neuroengineering portfolio to demonstrate skills in EEG signal processing, deep learning, and brain–computer interfaces.
