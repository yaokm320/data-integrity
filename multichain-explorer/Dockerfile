FROM tc_master_multichain-master

RUN apt-get -qy update && apt-get -qy install \
	git \
	libsqlite3-dev \
	python-dev \
	python-pip \
	sqlite3\
	vim \
	wget

RUN yes | pip install --upgrade pip
RUN yes | pip install pycrypto py-ubjson

RUN git clone https://github.com/MultiChain/multichain-explorer.git
WORKDIR multichain-explorer
RUN python setup.py install

WORKDIR /root

COPY explorer.sh /root/explorer.sh
RUN chmod +x /root/explorer.sh

COPY chain.conf /root/multichain-explorer/chain.conf

EXPOSE 2750

ENTRYPOINT './explorer.sh'
