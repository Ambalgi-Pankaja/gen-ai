# Step 1: Install All the Required Packages
1. accelarate - for running in distributed system, training and inference at scale made simple, efficient and adaptable
2. peft - for using Lora technique for fine tuning
3. bitsandbytes - enables accessible large language models via k-bit quantization for PyTorch
4. transformers - provides APIs and tools to easily download and train state-of-the-art pretrained models
5. trl - enables accessible large language models via k-bit quantization for PyTorch

# Step 2:  Import All the Required Libraries

# Step 3: Set Lora, Bitsandbytes, Training parameters
Below are the link to find more details about the parameters:

Bitsandbytes - https://huggingface.co/docs/transformers/main/en/main_classes/quantization#transformers.BitsAndBytesConfig

Trainingparameters - https://huggingface.co/docs/transformers/v4.42.0/en/main_classes/trainer#transformers.TrainingArguments


# Step 4: Load everything and start the fine-tuning process
1. First step is to load the dataset
2. Create bitsandbytes object by passing all the parameter to class - BitsAndBytesConfig. This is required for quantization.
3. Load the base model, in this case we are going with Llama2(Llama-2-7b-chat-hf). Pass the bnb config for 4 bit quantization. This enables loading larger models you normally wouldn’t be able to fit into memory, and speeding up inference.
4. We're loading the Llama 2 model in 4-bit precision on a GPU with the corresponding tokenizer.
5. Create a tokenizer from the base model. Required to prepare the input for the model.
6. Create a Lora config object by passing Lora parameters to the class - LoraConfig. The parameters can be found from the documentation provided in the above link.
7. Set the training parameters by passing values to class - TrainingArguments. The parameters can be found from the documentation provided in the above link.
8. Now create a trainer using SFTTrainer(Supervised Fine-Tuning) by passing 
   1. base_model
   2. dataset
   3. lora_configuration
   4. tokenizer
   5. training_parameters
9. Finally, run train to the trainer.

