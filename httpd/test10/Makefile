test=test10
domain=tls-o-matic.com

all:
	@cp ../../certs/$(test)* .
	@cp ../../certs/TLS-o-matic-intermediate-1.cert .
	@echo "Starting HTTPD server for $(test).$(domain)"
	@/usr/sbin/httpd -f /usr/local/tls-o-matic/httpd/$(test)/server.conf
	@sleep 1	# Wait for apache to create PID file
	@if ! test -f /var/run/httpd-$(test).pid;then (echo " ❌  ERROR no pid file";exit 1);fi
	@echo "✅  done!"

kill:
	@if ! test -f /var/run/httpd-$(test).pid;then (echo " ❌  ERROR no pid file";exit 1);fi
	@kill `cat /var/run/httpd-$(test).pid`
	@echo "✅  done!"
