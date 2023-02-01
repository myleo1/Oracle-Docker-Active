FROM alpine:3.17.1
LABEL maintainer="leo <leo@leosgo.com>" \
	version="v1.0.0" \
	description="Oracle-Docker-Active"
RUN apk update \
    && apk add --no-cache stress-ng \
    && echo '20       19      *       *       *       /usr/bin/stress-ng --cpu 1 --cpu-load 30 --timeout 90m' > /etc/crontabs/root
# 每天凌晨3点20分 UTC+8 占用CPU30%负载,假设有2核,CPU占用则为15%,持续1.5h
CMD ["crond","-f"]