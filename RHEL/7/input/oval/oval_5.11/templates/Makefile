templates: services

SHARED_DIR=../../../../../../shared/oval/templates

OUTPUT:=$(shell mkdir -p output)

services:
	${SHARED_DIR}/create_services_enabled.py services_enabled.csv
	${SHARED_DIR}/create_services_disabled.py services_disabled.csv

sockets:
	${SHARED_DIR}/create_sockets_disabled.py sockets_disabled.csv

compare:
	diff output/ ../ | grep -v "Only in ../"

copy:
	cp output/*.xml ../
	cp output/*.sh ../../remediations/bash/

find-untemplated: templates
	${SHARED_DIR}/find_untemplated.py

clean:
	rm -f output/*.xml
	rm -f output/*.sh
	rm -rf output/
