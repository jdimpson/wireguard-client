FROM alpine:latest
ENV LOCALSUBNET= \
    IPINFOAPI= \
    RATE=
RUN mkdir /etc/wireguard
RUN apk add --update wireguard-go && apk add tinyproxy bash && sed -e '/^Allow/ s/^/#/' -i /etc/tinyproxy/tinyproxy.conf && apk add curl iptables speedtest-cli tcpdump iproute2-tc jq ip6tables
COPY tc.sh /tc.sh
RUN chmod a+x /tc.sh
COPY entrypoint.sh /entrypoint.sh
RUN chmod a+x /entrypoint.sh
#COPY overrides.ovpn /overrides.ovpn
EXPOSE 51820/udp
ENTRYPOINT ["/entrypoint.sh"]
