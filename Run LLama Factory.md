# finetune 
### LLaMA
CUDA_VISIBLE_DEVICES=0 llamafactory-cli train \
    --stage sft \
    --do_train \
    --model_name_or_path /home/sky-lab/codes/Llama-3.1-8B-Instruct \
    --dataset train_data\
    --dataset_dir /home/sky-lab/Alan/TMP_LLM/data \
    --template llama3 \
    --finetuning_type lora \
    --output_dir /home/sky-lab/Alan/TMP_LLM/saves/LLaMA3.1-8B_v1-1/lora/sft_2025-04-08 \
    --overwrite_cache \
    --overwrite_output_dir \
    --cutoff_len 4096 \
    --preprocessing_num_workers 16 \
    --per_device_train_batch_size 2 \
    --per_device_eval_batch_size 1 \
    --gradient_accumulation_steps 8 \
    --lr_scheduler_type cosine \
    --logging_steps 50 \
    --warmup_steps 20 \
    --save_steps 100 \
    --eval_steps 50 \
    --evaluation_strategy steps \
    --load_best_model_at_end \
    --learning_rate 1e-5 \
    --num_train_epochs 15.0 \
    --val_size 0.1 \
    --plot_loss \
    --fp16


    **Removed**
    --max_samples 1000  # Remove it if you want to train on the entire dataset.
 
### Deepseek
CUDA_VISIBLE_DEVICES=1 llamafactory-cli train \
    --stage sft \
    --do_train \
    --model_name_or_path /home/sky-lab/codes/DeepSeek-R1-Distill-Llama-8B \
    --dataset train_data \
    --dataset_dir /home/sky-lab/Alan/TMP_LLM/data \
    --template deepseek3 \
    --finetuning_type lora \
    --output_dir /home/sky-lab/Alan/TMP_LLM/saves/DeepSeek-R1-Distill-Llama-8B/lora/sft_2025-04-07 \
    --overwrite_cache \
    --overwrite_output_dir \
    --cutoff_len 4096 \
    --preprocessing_num_workers 16 \
    --per_device_train_batch_size 2 \
    --per_device_eval_batch_size 1 \
    --gradient_accumulation_steps 8 \
    --lr_scheduler_type cosine \
    --logging_steps 50 \
    --warmup_steps 20 \
    --save_steps 100 \
    --eval_steps 50 \
    --learning_rate 1e-5 \
    --num_train_epochs 15.0 \
    --val_size 0.1 \
    --plot_loss \
    --fp16

### Qwen
CUDA_VISIBLE_DEVICES=1 llamafactory-cli train \
    --stage sft \
    --do_train \
    --model_name_or_path /home/sky-lab/codes/Qwen2.5-7B-Instruct-1M \
    --dataset train_data \
    --dataset_dir /home/sky-lab/Alan/TMP_LLM/data \
    --template qwen  \
    --finetuning_type lora \
    --output_dir /home/sky-lab/Alan/TMP_LLM/saves/qwen/lora/sft_2025-04-08 \
    --overwrite_cache \
    --overwrite_output_dir \
    --cutoff_len 4096 \
    --preprocessing_num_workers 16 \
    --per_device_train_batch_size 2 \
    --per_device_eval_batch_size 1 \
    --gradient_accumulation_steps 8 \
    --lr_scheduler_type cosine \
    --logging_steps 50 \
    --warmup_steps 20 \
    --save_steps 100 \
    --eval_steps 50 \
    --evaluation_strategy steps \
    --load_best_model_at_end \
    --learning_rate 1e-5 \
    --num_train_epochs 15.0 \
    --val_size 0.1 \
    --plot_loss \
    --fp16



# Run with Terminal
### LLaMA
CUDA_VISIBLE_DEVICES=0 llamafactory-cli chat \
    --model_name_or_path /home/sky-lab/codes/Llama-3.1-8B-Instruct \
    --adapter_name_or_path /home/sky-lab/Alan/TMP_LLM/saves/LLaMA3.1-8B_v1-1/lora/sft_2025-03-24  \
    --template llama3 \
    --finetuning_type lora

### Qwen
CUDA_VISIBLE_DEVICES=0 llamafactory-cli chat \
    --model_name_or_path /home/sky-lab/codes/Qwen2.5-7B-Instruct-1M \
    --adapter_name_or_path /home/sky-lab/Alan/TMP_LLM/saves/qwen/lora/sft_2025-04-04  \
    --template qwen \
    --finetuning_type lora

# Run with Gradio
### LLaMA
CUDA_VISIBLE_DEVICES=0 llamafactory-cli webchat \
    --model_name_or_path /home/sky-lab/codes/Llama-3.1-8B-Instruct \
    --adapter_name_or_path /home/sky-lab/Alan/TMP_LLM/saves/LLaMA3.1-8B_v1-1/lora/sft_2025-03-24  \
    --template llama3 \
    --finetuning_type lora

### Qwen
CUDA_VISIBLE_DEVICES=0 llamafactory-cli webchat \
    --model_name_or_path /home/sky-lab/codes/Qwen2.5-7B-Instruct-1M \
    --adapter_name_or_path /home/sky-lab/Alan/TMP_LLM/saves/qwen/lora/sft_2025-04-04  \
    --template qwen \
    --finetuning_type lora

# Batch Eval
### LLaMA
CUDA_VISIBLE_DEVICES=1 llamafactory-cli train \
    --stage sft \
    --do_predict \
    --model_name_or_path /home/sky-lab/codes/Llama-3.1-8B-Instruct \
    --adapter_name_or_path /home/sky-lab/Alan/TMP_LLM/saves/LLaMA3.1-8B_v1-1/lora/sft_2025-04-08  \
    --eval_dataset eval_data \
    --dataset_dir /home/sky-lab/Alan/TMP_LLM/data \
    --template llama3 \
    --finetuning_type lora \
    --output_dir /home/sky-lab/Alan/TMP_LLM/saves/LLaMA3.1-8B_v1-1/lora/predict_2025-04-08 \
    --overwrite_cache \
    --overwrite_output_dir \
    --cutoff_len 4096 \
    --preprocessing_num_workers 16 \
    --per_device_eval_batch_size 1 \
    --predict_with_generate

### QWEN
CUDA_VISIBLE_DEVICES=1 llamafactory-cli train \
    --stage sft \
    --do_predict \
    --model_name_or_path /home/sky-lab/codes/Qwen2.5-7B-Instruct-1M \
    --adapter_name_or_path /home/sky-lab/Alan/TMP_LLM/saves/qwen/lora/sft_2025-04-08  \
    --eval_dataset eval_data \
    --dataset_dir /home/sky-lab/Alan/TMP_LLM/data \
    --template qwen \
    --finetuning_type lora \
    --output_dir /home/sky-lab/Alan/TMP_LLM/saves/qwen/lora/predict_2025-04-04 \
    --overwrite_cache \
    --overwrite_output_dir \
    --cutoff_len 4096 \
    --preprocessing_num_workers 16 \
    --per_device_eval_batch_size 1 \
    --predict_with_generate

### Deepseek
CUDA_VISIBLE_DEVICES=0 llamafactory-cli train \
    --stage sft \
    --do_predict \
    --model_name_or_path /home/sky-lab/codes/DeepSeek-R1-Distill-Llama-8B \
    --adapter_name_or_path /home/sky-lab/Alan/TMP_LLM/saves/DeepSeek/lora/sft_2025-04-07  \
    --eval_dataset eval_data \
    --dataset_dir /home/sky-lab/Alan/TMP_LLM/data \
    --template deepseek3 \
    --finetuning_type lora \
    --output_dir /home/sky-lab/Alan/TMP_LLM/saves/DeepSeek/lora/predict_2025-04-07  \
    --overwrite_cache \
    --overwrite_output_dir \
    --cutoff_len 4096 \
    --preprocessing_num_workers 16 \
    --per_device_eval_batch_size 1 \
    --predict_with_generate