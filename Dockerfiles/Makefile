PARENT_DIR := $(abspath $(dir $(lastword $(MAKEFILE_LIST)))/../)

TARGETS := fedora27 centos7 fedora26 fedora25 centos6

.PHONY: all
all: pip_install.sh
	set -e; for i in $(TARGETS); do \
		docker build -f $$i/Dockerfile -t lp_$$i .; \
	done

test: all
	./run_tests.sh $(PARENT_DIR) $(TARGETS)

pip_install.sh: ../requirements.txt
	./gen_pip_install.sh

