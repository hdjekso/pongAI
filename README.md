# Training a Pong AI with PyTorch in Google Colab

## Overview
This notebook trains a Deep Q-Network (DQN) model using PyTorch to play the game Pong. The training process is designed to run in **Google Colab** and requires mounting Google Drive to save checkpoints and the final trained model.

## Setup Instructions

1. **Run in Google Colab**
   - Upload the notebook to your Google Drive.
   - Open the notebook in Google Colab.
   - Ensure your runtime is set to **GPU** for faster training.

2. **Mount Google Drive**
   - The notebook saves and loads models from Google Drive. Run the following cell in the notebook to mount your drive:
     ```python
     from google.colab import drive
     drive.mount('/content/drive')
     ```
   - Modify the `pthname` variable to point to the correct path in your Google Drive where you want to load the initial incomplete, pretrained model.
   - Modify the `saved_path` variable to point to the correct path in your Google Drive where you want to store the completely trained model.
   - Modify the path in the line: `torch.save(model.state_dict(), f"/content/drive/My Drive/Colab_Notebooks/Assignments/Deep_Q_Network/saves_2/{frame_idx}_model.pth")` to point to the correct path in your Google Drive where you want to store the model checkpoints.

## Training Process
- The training process involves playing **1 million frames** of Pong.
- A **partially trained model** is saved every **20,000 frames**.
- If you want to **continue training from a previous checkpoint**, update the `pthname` variable to use the last saved model instead of `model_pretrained.pth`. Additionally, update the `for` loop in the training section to start from the correct frame count. For example, if resuming from **200,000** frames, modify:
  ```python
  for frame_idx in range(0, num_frames + 1):
  ```
  to:
  ```python
  for frame_idx in range(200000, num_frames + 1):

Example:
```python
pthname = '/content/drive/MyDrive/pong_model_checkpoint_200000.pth'  # Load partially trained model and resume training from 200K frames
```

## Testing Your Model
- The "Test Your Model" section generates an **MP4 video** showing the trained model playing Pong.
- Ensure that the correct model file is loaded before running this section.

## Model Files
- **Partially trained models**: Saved every **20K frames** (e.g., `pong_model_checkpoint_200000.pth`).
- **Final trained model**: The completely trained model is saved as `PongNoFrameskip-v4-model.pth`.

## Notes
- Modify path variables (`pthname`) as needed based on where the notebook and model files are stored in Google Drive.
- Training may take several hours depending on available GPU resources in Colab.

