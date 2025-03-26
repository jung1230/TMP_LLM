# finetune 

CUDA_VISIBLE_DEVICES=0 llamafactory-cli train \
    --stage sft \
    --do_train \
    --model_name_or_path /home/sky-lab/codes/Llama-3.1-8B-Instruct \
    --dataset alpaca_data\
    --dataset_dir /home/sky-lab/Alan/TMP_LLM/data \
    --template llama3 \
    --finetuning_type lora \
    --output_dir /home/Alan/TMP_LLM/saves/LLaMA3.1-8B_v1-1/lora/sft_2025-03-24 \
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
    --learning_rate 5e-5 \
    --num_train_epochs 15.0 \
    --max_samples 1000 \
    --val_size 0.1 \
    --plot_loss \
    --fp16

# Run with Gradio

CUDA_VISIBLE_DEVICES=0 llamafactory-cli webchat \
    --model_name_or_path /home/sky-lab/codes/Llama-3.1-8B-Instruct \
    --adapter_name_or_path /home/sky-lab/SHENG_code/LLM-TMP/saves/LLaMA3.1-8B/lora/sft  \
    --template llama3 \
    --finetuning_type lora