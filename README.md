
# Name Classification with RNN (PyTorch)

This project implements a simple **Recurrent Neural Network (RNN) from scratch** in PyTorch to classify names by their language of origin. Given a name like *"Albert"* or *"Satoshi"*, the model predicts the most likely category (e.g., English, Japanese, etc.).

The implementation follows a character-level RNN approach where each character is represented as a one-hot encoded vector, and the sequence of characters is fed into the model step by step.

***

### Features
- Custom-built RNN (no use of `nn.RNN`, only linear layers and manual recurrence).
- Trains on a dataset of names grouped by languages (`data/names/*.txt`).
- Provides both training with loss tracking and interactive prediction.
- Uses one-hot encoding for characters.
- Visualization of training loss.

***

### Project Structure
```
.
├── rnn.py            # Main RNN model + training and prediction
├── utils.py          # Data loading, preprocessing, helper functions
├── data/
│   └── names/        # Dataset of names (text files per language)
└── README.md
```

- **rnn.py**: Defines the `RNN` class, training loop, prediction function, and interactive CLI for user input.  
- **utils.py**: Data processing utilities (convert text to tensors, load language-category data, generate random training samples).  
- **data/names/**: Contains text files of names separated by language (e.g., `English.txt`, `French.txt`, etc.).  

***

### Requirements
- Python 3.8+
- PyTorch
- Matplotlib

Install dependencies:
```bash
pip install torch matplotlib
```

***

### Dataset
This project uses the [Names dataset](https://download.pytorch.org/tutorial/data.zip) from the PyTorch tutorial, which contains thousands of names from 18 languages. Each file in `data/names/` is formatted as:

```
Abate
Abbagnale
Abbandonato
...
```

Make sure to extract these `.txt` files into the `data/names/` folder.

***

### Training
Run the training loop by executing:

```bash
python rnn.py
```

- The script will train for 100,000 iterations.
- Loss values are tracked and plotted after training.
- Progress is printed every 5,000 steps with the model’s prediction vs. ground truth.

Example training output:

```
5000 5.0 2.3456 Albert / English CORRECT
10000 10.0 2.1023 Satoshi / Japanese WRONG (Japanese)
```

At the end, you will see a training loss graph plotted with Matplotlib.

***

### Prediction (Interactive Mode)
After training, the script enters an **interactive mode**. You can type any name, and the model will predict its category:

```
Input: Albert
> Albert
English

Input: Satoshi
> Satoshi
Japanese

Input: quit
```

Type `"quit"` to exit.

***

### Example Code Snippet
```python
from rnn import predict

predict("Albert")   # Predicts "English"
predict("Satoshi")  # Predicts "Japanese"
```

***


