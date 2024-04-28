1. Evaluation Metric
    
    For the performance of our two selected BERT models on Chinese and English sentiment datasets, we need to measure it by a set of evaluation metrics, of which the simplest and most intuitive is the accuracy by testing the system, however, the accuracy into counting the number of times the model makes correct predictions throughout the entire dataset, if the dataset is class-balanced, the metrics have a certain degree of reliability, but if the dataset is highly varied in the number of classes, the accuracy may not be a valid reflection of the model's performance. F1 score is another model evaluation metric that assesses the predictive power of a model by detailing its categorization performance rather than its overall performance through accuracy. F1 score combines the competing metrics of model accuracy and recall to somewhat address the problem of imbalance in the categories of a dataset. In our project, we used HuggingFace's Evaluate library to calculate the Metric for Accuracy and F1 score.(Pedregosa et al., 2020)
    
2. Training Argument & Trainer 
    
    We use Huggingface's API “Trainer” to help us simplify the process of fine-tuning on pre-trained models.Trainer is a high-level API of Huggingface transformers library, which helps us to quickly set up a training framework to fine-tune pre-trained models on our own Chinese, English sentiment dataset.
    
    Before defining a Trainer, we first need to define a TrainingArguments class, which will contain all the hyper-parameters used by the Trainer for training and evaluation. Then we can define a Trainer based on the existing BERT pre-training model by passing it all the previously constructed objects, including the model, training hyper-parameters, training and validation datasets, and tokenizer.(Wolf et al., 2020)
    
3. Hyperparameter Tuning & Optuna
    
    In order to make the model have better performance and efficiency, we need to constantly adjust the hyperparameters, which is a long and complicated process. In this regard, we chose the Optuna-based automatic parameter tuning technique for transformers model, which enables the model to automatically find the optimal hyper-parameters during the training process, saves the time and effort of manual parameter tuning, avoids human bias and error, and improves the generalization ability of the model.
    
    Optuna is an open-source Hyper-parameter Optimization (HPO) framework for automatically performing hyper-parameter search spaces. In order to find the optimal set of hyper-parameters, Oputna uses Bayesian methods to automatically tune the hyper-parameters based on each trail within a given parameter range.  Specifically, given a hyper-parameter search space, Oputna uses F1 score as the standard to measure the model performance, and finds the optimal hyper-parameter combination by continuously trying different hyper-parameter combinations, evaluating the function value of the target, and automatically tuning the parameters in the direction of maximizing the F1 score of the model. Our hyper-parameter tuning for BERT pre-trained models mainly focuses on the learning rate, training epoch, batch size, and the learning rate scheduler which dynamically adjusts the learning rate.
    
4. Best trail with correspond setting and performance
    1. Chinese
        
        F1 score：0.8555
        
        | Epoch | Training Loss | Validation Loss | Accuracy | F1 |
        | --- | --- | --- | --- | --- |
        | 1 | 0.698700  | 0.635335 | 0.793375 | 0.785509 |
        | 2 | 0.366900 | 0.618071 | 0.849632 | 0.839630 |
        | 3 | 0.129500 | 0.727743 | 0.865405 | 0.855450 |
        
        Hyper-parameter:
        
        - 'learning_rate': 2.783008594309693e-05
        - 'num_train_epochs': 3
        - 'per_device_train_batch_size': 8
        - lr_scheduler_type': 'linear'
        
    2. English
        
        F1 score：0.8982
        
        | Epoch | Training Loss | Validation Loss | Accuracy | F1 |
        | --- | --- | --- | --- | --- |
        | 1 | 0.661100 | 0.631993 | 0.771753 | 0.819770 |
        | 2 | 0.438900 | 0.486949 | 0.819357 | 0.873858 |
        | 3 | 0.238900 | 0.538820 | 0.819987 | 0.879396 |
        | 4 | 0.140500 | 0.595383 | 0.835435 | 0.895633 |
        | 5 | 0.068500 | 0.796915 | 0.838588 | 0.898174 |
        
        Hyper-parameter:
        
        - 'learning_rate': 3.21812825512821e-05
        - 'num_train_epochs': 5
        - 'per_device_train_batch_size': 32
        - lr_scheduler_type': 'linear'
    
    The F1 score of both models on their respective datasets is above 0.85, which indicates that our models have good prediction for sentiment recognition of sentences.
