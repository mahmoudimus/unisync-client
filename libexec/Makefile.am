
pkglibexec_SCRIPTS = unisync-client-connect unisync-client-syncinit unisync-client-sync

EXTRA_DIST = unisync-client-connect.sh unisync-client-syncinit.sh unisync-client-sync.sh
CLEANFILES = $(pkglibexec_SCRIPTS)

pkgsysconfdir = $(sysconfdir)/$(PACKAGE)

do_subst = sed -i -e 's,[@]pkgsysconfdir[@],$(pkgsysconfdir),g' \
			      -e 's,[@]VERSION[@],$(VERSION),g' \
				  -e 's,[@]pkglibexecdir[@],$(pkglibexecdir),g'

conn_cmd = `echo unisync-client-connect | sed '$(program_transform_name)'`

cmd_subst = sed -i "s/[@]unisync-client-connect[@]/$(conn_cmd)/g"


$(pkglibexec_SCRIPTS):%: %.sh
	rm -f $@
	echo "#!" $(BASH) > $@
	cat $^ >> $@
	$(do_subst) $@
	$(cmd_subst) $@
	chmod u+x $@
