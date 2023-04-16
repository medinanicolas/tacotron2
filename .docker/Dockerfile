FROM pytorch/pytorch:1.9.0-cuda11.1-cudnn8-devel
RUN apt-key adv --keyserver keyserver.ubuntu.com --recv-keys A4B469963BF863CC
RUN apt update && apt install libfreetype6-dev pkg-config git -y
#ADD waveglow/reqs.txt requirements.txt
COPY ./ .
RUN pip3 install -r waveglow/requirements.txt
RUN git submodule init; git submodule update
RUN cd waveglow/apex && git checkout 22.04-dev && pip3 install -v --disable-pip-version-check --no-cache-dir --global-option="--cpp_ext" --global-option="--cuda_ext" ./
WORKDIR waveglow
CMD tail -f /dev/null
