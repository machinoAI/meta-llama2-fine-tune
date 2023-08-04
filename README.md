# meta-llama2-fine-tune
The Llama-2-13b-chat-hf model was fine-tuned using the following steps:
1. The model was requested from Hugging Face using the user's Hugging Face email ID. This process takes just a few minutes to get approved.
2. The model was loaded onto the GPU with a quantization configuration to reduce GPU memory usage. This required the `bitsandbytes` library and a `BitsAndBytesConfig` object was created with specific parameters.
3. The tokenizer for the model was initialized and the pad token was set to the eos token. The model's token embeddings were resized to match the length of the tokenizer.
4. The model was prepared for int8 training using the `prepare_model_for_int8_training` function. A `LoraConfig` object was created with specific parameters such as `r`, `lora_alpha`, `lora_dropout`, `bias`, and `task_type`.
5. A `SFTTrainer` object was created with specific training arguments such as `output_dir`, `per_device_train_batch_size`, `optim`, `logging_steps`, `learning_rate`, `fp16`, `warmup_ratio`, `lr_scheduler_type`, `num_train_epochs`, and `save_strategy`. The trainer object was also configured with a train dataset, a tokenizer, and a maximum sequence length.
6. The norm modules in the model were converted to float32 using a for loop and the `.to()` method. Finally, the trainer object was used to train the model using the `.train()` method.

Do reach out to `ravikk87@gmail.com` for any help required.
