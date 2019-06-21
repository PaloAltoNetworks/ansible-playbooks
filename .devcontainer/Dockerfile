FROM python:3.7.3-stretch
  
ENV ANSIBLE_VERSION=2.8.1

RUN pip install ansible==${ANSIBLE_VERSION} && \
    pip install pandevice pan-python xmltodict && \
    ansible-galaxy install PaloAltoNetworks.paloaltonetworks
