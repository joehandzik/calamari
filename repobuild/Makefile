precise:
	reprepro --confdir=./conf/precise --noskipold -b ./precise/ update
	reprepro --confdir=./conf/precise -b ./precise/ remove precise diamond
	reprepro --confdir=./conf/precise --noskipold -b ./precise/ includedeb precise ../../Diamond/build/*.deb
	tar czf calamari-repo-precise.tar.gz precise/

trusty:
	reprepro --confdir=./conf/trusty --noskipold -b ./trusty/ update
	reprepro --confdir=./conf/trusty -b ./trusty/ remove trusty diamond
	reprepro --confdir=./conf/trusty --noskipold -b ./trusty/ includedeb trusty ../../Diamond/build/*.deb
	tar czf calamari-repo-trusty.tar.gz trusty/

wheezy:
	reprepro --confdir=./conf/wheezy --noskipold -b ./wheezy/ update
	reprepro --confdir=./conf/wheezy -b ./wheezy/ remove wheezy diamond
	reprepro --confdir=./conf/wheezy --noskipold -b ./wheezy/ includedeb wheezy ../../Diamond/build/*.deb
	tar czf calamari-repo-wheezy.tar.gz wheezy/

el6:
	mkdir el6 || true
	yumdownloader --destdir=el6 --archlist=x86_64 -x '*i686*' salt-minion m2crypto openpgm python-babel python-jinja2 python-msgpack PyYAML python-zmq salt sshpass zeromq3 python-crypto libyaml
	cp ../../Diamond/dist/*.noarch.rpm el6/
	createrepo el6
	tar czf calamari-repo-el6.tar.gz el6/

rhel6:
	mkdir rhel6 || true
	sudo yumdownloader --destdir=rhel6 --archlist=x86_64 -x '*i686*' salt-minion m2crypto openpgm python-babel python-jinja2 python-msgpack PyYAML python-zmq salt sshpass zeromq3 python-crypto libyaml
	cp ../../Diamond/dist/*.noarch.rpm rhel6/
	createrepo rhel6
	tar czf calamari-repo-rhel6.tar.gz rhel6/

rhel7:
	mkdir rhel7 || true
	yumdownloader --destdir=rhel7 m2crypto openpgm python-babel python-jinja2 python-msgpack PyYAML python-zmq sshpass zeromq3 python-crypto libyaml salt salt-minion
	cp ../../Diamond/dist/*.noarch.rpm rhel7/
	createrepo rhel7
	tar czf calamari-repo-rhel7.tar.gz rhel7/

clean:
	rm -rf el6 rhel6 rhel7 precise trusty wheezy

.PHONY: precise trusty wheezy el6 rhel6 rhel7 clean
