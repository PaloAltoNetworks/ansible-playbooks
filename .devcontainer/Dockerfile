FROM python:3.7.3-stretch
  
ENV ANSIBLE_VERSION=2.8.1
ENV ANSIBLE_PAN_VERSION=2.2.3

RUN pip install --no-cache-dir ansible==${ANSIBLE_VERSION} && \
    pip install --no-cache-dir pandevice pan-python xmltodict && \
    ansible-galaxy install PaloAltoNetworks.paloaltonetworks,v${ANSIBLE_PAN_VERSION}
