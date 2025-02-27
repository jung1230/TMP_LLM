conda create --name TMPLLM python=3.13

conda activate TMPLLM

pip3 install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu118

pip install marker-pdf
