top_srcdir   = /home/runner/work/apache-ultimate-bad-bot-blocker/apache-ultimate-bad-bot-blocker/zlib-1.2.12/httpd-2.2.25
top_builddir = /home/runner/work/apache-ultimate-bad-bot-blocker/apache-ultimate-bad-bot-blocker/zlib-1.2.12/httpd-2.2.25
srcdir       = /home/runner/work/apache-ultimate-bad-bot-blocker/apache-ultimate-bad-bot-blocker/zlib-1.2.12/httpd-2.2.25/support
builddir     = /home/runner/work/apache-ultimate-bad-bot-blocker/apache-ultimate-bad-bot-blocker/zlib-1.2.12/httpd-2.2.25/support
VPATH        = /home/runner/work/apache-ultimate-bad-bot-blocker/apache-ultimate-bad-bot-blocker/zlib-1.2.12/httpd-2.2.25/support
DISTCLEAN_TARGETS = apxs apachectl dbmmanage log_server_status \
	logresolve.pl phf_abuse_log.cgi split-logfile envvars-std

CLEAN_TARGETS = suexec

PROGRAMS = htpasswd htdigest rotatelogs logresolve ab htdbm htcacheclean httxt2dbm $(NONPORTABLE_SUPPORT)
TARGETS  = $(PROGRAMS)

PROGRAM_LDADD        = $(UTIL_LDFLAGS) $(PROGRAM_DEPENDENCIES) $(EXTRA_LIBS) $(AP_LIBS)
PROGRAM_DEPENDENCIES = 

include $(top_builddir)/build/rules.mk

install:
	@test -d $(DESTDIR)$(bindir) || $(MKINSTALLDIRS) $(DESTDIR)$(bindir)
	@test -d $(DESTDIR)$(sbindir) || $(MKINSTALLDIRS) $(DESTDIR)$(sbindir)
	@test -d $(DESTDIR)$(libexecdir) || $(MKINSTALLDIRS) $(DESTDIR)$(libexecdir)
	@cp -p $(top_builddir)/server/httpd.exp $(DESTDIR)$(libexecdir)
	@for i in apxs apachectl dbmmanage; do \
	    if test -f "$(builddir)/$$i"; then \
	        cp -p $$i $(DESTDIR)$(sbindir); \
	        chmod 755 $(DESTDIR)$(sbindir)/$$i; \
	    fi ; \
	done
	@if test -f "$(builddir)/envvars-std"; then \
	    cp -p envvars-std $(DESTDIR)$(sbindir); \
	    if test ! -f $(DESTDIR)$(sbindir)/envvars; then \
	        cp -p envvars-std $(DESTDIR)$(sbindir)/envvars ; \
	    fi ; \
	fi

htpasswd_OBJECTS = htpasswd.lo
htpasswd: $(htpasswd_OBJECTS)
	$(LINK) $(htpasswd_LTFLAGS) $(htpasswd_OBJECTS) $(PROGRAM_LDADD) $(CRYPT_LIBS)

htdigest_OBJECTS = htdigest.lo
htdigest: $(htdigest_OBJECTS)
	$(LINK) $(htdigest_LTFLAGS) $(htdigest_OBJECTS) $(PROGRAM_LDADD)

rotatelogs_OBJECTS = rotatelogs.lo
rotatelogs: $(rotatelogs_OBJECTS)
	$(LINK) $(rotatelogs_LTFLAGS) $(rotatelogs_OBJECTS) $(PROGRAM_LDADD)

logresolve_OBJECTS = logresolve.lo
logresolve: $(logresolve_OBJECTS)
	$(LINK) $(logresolve_LTFLAGS) $(logresolve_OBJECTS) $(PROGRAM_LDADD)

htdbm_OBJECTS = htdbm.lo
htdbm: $(htdbm_OBJECTS)
	$(LINK) $(htdbm_LTFLAGS) $(htdbm_OBJECTS) $(PROGRAM_LDADD) $(CRYPT_LIBS)

ab_OBJECTS = ab.lo
ab_LDADD = $(PROGRAM_LDADD) $(SSL_LIBS)
ab: $(ab_OBJECTS)
	$(LINK) $(ab_LTFLAGS) $(ab_OBJECTS) $(ab_LDADD)

checkgid_OBJECTS = checkgid.lo
checkgid: $(checkgid_OBJECTS)
	$(LINK) $(checkgid_LTFLAGS) $(checkgid_OBJECTS) $(PROGRAM_LDADD)

suexec_OBJECTS = suexec.lo
suexec: $(suexec_OBJECTS)
	$(LINK) $(suexec_OBJECTS)

htcacheclean_OBJECTS = htcacheclean.lo
htcacheclean: $(htcacheclean_OBJECTS)
	$(LINK) $(htcacheclean_LTFLAGS) $(htcacheclean_OBJECTS) $(PROGRAM_LDADD)

httxt2dbm_OBJECTS = httxt2dbm.lo
httxt2dbm: $(httxt2dbm_OBJECTS)
	$(LINK) $(httxt2dbm_LTFLAGS) $(httxt2dbm_OBJECTS) $(PROGRAM_LDADD)

