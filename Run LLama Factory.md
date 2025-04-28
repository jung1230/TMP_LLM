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
    --dataset alpaca_data_before_7000 \
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
    --evaluation_strategy steps \
    --load_best_model_at_end \
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


# Multi-GPU Training

### this overfits(train loss 0.1, eval loss 0.6)
CUDA_VISIBLE_DEVICES=0,1,2,3 python -m torch.distributed.run --nproc_per_node=4 src/train.py \
    --stage sft \
    --do_train True \
    --model_name_or_path ./../deepseek70B \
    --preprocessing_num_workers 16 \
    --finetuning_type lora \
    --template alpaca \
    --flash_attn auto \
    --dataset_dir ./../data \
    --dataset train_data \
    --cutoff_len 4096 \
    --learning_rate 5e-05 \
    --num_train_epochs 15.0 \
    --max_samples 100000 \
    --per_device_train_batch_size 1 \
    --gradient_accumulation_steps 4 \
    --lr_scheduler_type cosine \
    --max_grad_norm 1.0 \
    --logging_steps 5 \
    --save_steps 100 \
    --warmup_steps 20 \
    --packing False \
    --report_to none \
    --output_dir ./../saves/Deepseek70B/lora/train_2025-04-27 \
    --fp16 True \
    --plot_loss True \
    --trust_remote_code True \
    --ddp_timeout 180000000 \
    --include_num_input_tokens_seen True \
    --optim adamw_torch \
    --lora_rank 4 \
    --lora_alpha 8 \
    --lora_dropout 0 \
    --loraplus_lr_ratio 16 \
    --lora_target all \
    --val_size 0.1 \
    --eval_strategy steps \
    --eval_steps 100 \
    --per_device_eval_batch_size 2 \
    --deepspeed ./../ds_z3_config.json


# try this
##### In practice most folks leave α ≈ rank or α ≈ 2×rank—and focus their tuning effort on lr, dropout, and warmup instead.
CUDA_VISIBLE_DEVICES=0,1,2,3 python -m torch.distributed.run --nproc_per_node=4 src/train.py \
    --stage sft \
    --do_train True \
    --model_name_or_path ./../deepseek70B \
    --preprocessing_num_workers 16 \
    --finetuning_type lora \
    --template alpaca \
    --flash_attn auto \
    --dataset_dir ./../data \
    --dataset train_data \
    --cutoff_len 4096 \
    --learning_rate 2e-05 \
    --num_train_epochs 5.0 \
    --max_samples 100000 \
    --per_device_train_batch_size 1 \
    --gradient_accumulation_steps 4 \
    --lr_scheduler_type cosine \
    --max_grad_norm 1.0 \
    --logging_steps 5 \
    --save_steps 100 \
    --warmup_steps 300 \
    --packing False \
    --report_to none \
    --output_dir ./../saves/Deepseek70B/lora/train_2025-04-27 \
    --fp16 True \
    --plot_loss True \
    --trust_remote_code True \
    --ddp_timeout 180000000 \
    --include_num_input_tokens_seen True \
    --optim adamw_torch \
    --lora_rank 4 \
    --lora_alpha 8 \
    --lora_dropout 0.1 \
    --loraplus_lr_ratio 16 \
    --lora_target all \
    --val_size 0.1 \
    --eval_strategy steps \
    --eval_steps 100 \
    --per_device_eval_batch_size 2 \
    --deepspeed ./../ds_z3_config.json


# eval
CUDA_VISIBLE_DEVICES=0,1,2,3 python -m torch.distributed.run --nproc_per_node=4 src/train.py \
  --stage sft \
  --do_eval True \
  --predict_with_generate True \
  --model_name_or_path ./../deepseek70B \
  --adapter_name_or_path ./../saves/Deepseek70B/lora/train_2025-04-27 \
  --preprocessing_num_workers 16 \
  --finetuning_type lora \
  --template alpaca \
  --flash_attn auto \
  --dataset_dir ./../data \
  --eval_dataset eval_data \
  --cutoff_len 4096 \
  --per_device_eval_batch_size 1 \
  --generation_max_length 512 \
  --generation_num_beams 4 \
  --output_dir ./../saves/Deepseek70B/lora/eval_2025-04-27 \
  --report_to none \
  --trust_remote_code True \
  --fp16 True \
  --deepspeed ./../ds_z2_offload_config.json

CUDA_VISIBLE_DEVICES=0,1,2,3 python -m torch.distributed.run --nproc_per_node=4 src/train.py \
  --stage sft \
  --do_eval True \
  --predict_with_generate True \
  --model_name_or_path ./../deepseek70B \
  --adapter_name_or_path ./../saves/... \
  --template alpaca \
  --dataset_dir ./../data \
  --eval_dataset eval_data \
  --cutoff_len 4096 \
  --per_device_eval_batch_size 1 \
  --generation_max_length 512 \
  --generation_num_beams 4 \
  --output_dir ./../saves/... \
  --report_to none \
  --trust_remote_code True \
  --fp16 True \
  --deepspeed ./../ds_z2_offload_config.json
