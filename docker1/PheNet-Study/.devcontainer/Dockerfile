ARG PYTORCH="1.6.0"
ARG CUDA="10.1"
ARG CUDNN="7"

FROM pytorch/pytorch:${PYTORCH}-cuda${CUDA}-cudnn${CUDNN}-devel

COPY build.txt .
RUN pip install -r build.txt

# RUN pip install --no-cache-dir -e .