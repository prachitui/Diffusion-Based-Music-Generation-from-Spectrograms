# Diffusion-Based-Music-Generation-from-Spectrograms
 This diffusion-based music generation model that synthesizes realistic audio waveforms directly from spectrograms. By leveraging a U-Net architecture with attention mechanisms and 
 MDCT-transformed spectrograms, the model generates high-quality music without using symbolic representations like MIDI.

# Overview
The model generates music by converting raw audio files into Modified Discrete Cosine Transform (MDCT) spectrograms and applying denoising diffusion techniques. The model is trained on the
GTZAN dataset, focusing on a single genre (classical) to produce high-quality, genre-specific music. It uses a U-Net-based architecture for audio generation, combined with diffusion steps 
that progressively refine the generated samples.

# Dataset
The project uses the GTZAN Music Genre dataset, which includes audio files from 10 different genres. For training, we focus on the classical genre. Each audio file is transformed into 
its MDCT spectrogram, a 2D representation, which allows us to treat the music generation task similarly to image generation.

# Model Architecture
The model follows a U-Net architecture with attention in the upsampling layers. This architecture, inspired by successful implementations in diffusion models for images, processes the 
MDCT spectrograms and generates high-quality audio by learning a denoising process. Key components include:

**Sinusoidal Embedding:** Used to handle diffusion steps.

**Residual Blocks:** For better gradient flow and improved learning.

**Attention Mechanism:** Applied in the bottom upsampling layer for better context understanding.

**Diffusion Process:** A denoising diffusion implicit model (DDIM) is used to generate the audio progressively, based on learned noise schedules.


# Training Process
The model is trained using the following:

**Optimizer:** AdamW with weight decay for stable training.

**Loss Functions:** Custom loss functions including spectral norm and time derivatives to better capture the structure of the generated audio.

**Steps:** 1000 diffusion steps with noise schedules.

**Data Preprocessing:** MDCT spectrograms were extracted from the classical genre audio files, and the model was trained to reconstruct clean spectrograms from noisy versions.


# Results
The model successfully generates spectrograms that resemble real musical patterns, which are converted back into audio. The generated audio shows potential for realistic music synthesis 
in the classical genre. 

You can listen to the generated audio samples in the [samples](https://github.com/prachitui/Diffusion-Based-Music-Generation-from-Spectrograms/tree/main/samples) folder.
