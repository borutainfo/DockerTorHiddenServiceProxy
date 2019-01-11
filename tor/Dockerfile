FROM debian:jessie

ARG PRIVATE_KEY

RUN apt-get update
RUN apt-get -y install tor torsocks nginx

ADD ./torrc /etc/tor/torrc
ADD proxy.conf /etc/nginx/sites-available/proxy.conf
RUN ln -s /etc/nginx/sites-available/proxy.conf /etc/nginx/sites-enabled/proxy.conf
RUN rm /etc/nginx/sites-available/default

RUN mkdir -p /var/lib/tor/proxy
RUN echo "${PRIVATE_KEY}" > /var/lib/tor/proxy/private_key

CMD service nginx start && tor -f /etc/tor/torrc
