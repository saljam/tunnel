from alpine
run apk add --no-cache strongswan iptables
expose 500 4500
entrypoint ["ipsec", "start", "--nofork"]
