FROM pytorch/pytorch:1.9.0-cuda11.1-cudnn8-devel
RUN apt-key adv --keyserver keyserver.ubuntu.com --recv-keys A4B469963BF863CC
RUN apt update && apt install language-pack-es libfreetype6-dev pkg-config git screen vim -y
RUN echo "export LANG=es_ES.UTF-8; export LANGUAGE=es_ES.UTF-8" > /root/.bashrc
#COPY waveglow/requirements.txt waveglow/requirements.txt
COPY ./ .
RUN pip3 install -r waveglow/requirements.txt
RUN git submodule update --init --remote
RUN cd waveglow && git submodule update --init
RUN cd waveglow/apex && git checkout 22.04-dev && pip3 install -v --disable-pip-version-check --no-cache-dir --global-option="--cpp_ext" --global-option="--cuda_ext" ./
CMD tail -f /dev/null
