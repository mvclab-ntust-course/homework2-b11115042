FROM nvidia/cuda:12.1.0-base-ubuntu22.04
RUN apt-get update && apt-get install -y python3 python3-pip
WORKDIR /docker

ENV DISPLAY=host.docker.internal:0.0

COPY requirements.txt ./
RUN pip install -r requirements.txt

RUN pip uninstall -y torch torchvision
RUN pip install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu121

RUN apt-get update && apt-get install -y libgl1-mesa-glx libglib2.0-dev libxcb-util1 libqt5gui5 && rm -rf /var/lib/apt/lists/*

ENV QT_DEBUG_PLUGINS=1

RUN pip install timm
ADD . ./

CMD ["/usr/bin/python3", "detect.py", "--view-img","--nosave","--weights","yolov5x.pt","--source","video/argoverse/argoverse.mp4","--run-liteMono","--run-bev","--classes","2","5","7"]