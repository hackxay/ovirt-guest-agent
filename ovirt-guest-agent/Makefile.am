
SUBDIRS = pam consoleapps

AGENT_NAME = ovirt-guest-agent

agentdir=/usr/share/ovirt-guest-agent
agent_PYTHON= \
    CredServer.py \
    GuestAgentLinux2.py \
    LockActiveSession.py \
    OVirtAgentLogic.py \
    VirtIoChannel.py \
    ovirt-guest-agent.py \
    $(NULL)

noinst_PYTHON=\
    GuestAgentWin32.py \
    setup.py \
    version.py \
    WinFile.py \
    OVirtGuestService.py \
    $(NULL)

agent_DATA=hibernate

agentconfdir=/etc
agentconf_DATA=ovirt-guest-agent.conf

dbusconfdir=/etc/dbus-1/system.d
dbusconf_DATA=org.ovirt.vdsm.Credentials.conf

rulesdir=/etc/udev/rules.d
rules_DATA = 55-$(AGENT_NAME).rules

55-$(AGENT_NAME).rules: $(AGENT_NAME).rules
	cp $(AGENT_NAME).rules 55-$(AGENT_NAME).rules

# Conditionally install the systemd service
if HAVE_SYSTEMD
systemdsystemunit_DATA = ovirt-guest-agent.service
endif

EXTRA_DIST= \
    $(agent_DATA) \
    $(agentconf_DATA) \
    $(daemon_DATA) \
    $(dbusconf_DATA) \
    $(AGENT_NAME).rules \
    ovirt-guest-agent \
    ovirt-guest-agent.service \
    ovirt-guest-agent.el5.rules \
    Makefile.el5 \
    README-windows.txt \
    win-guest-agent-build-exe.bat \
    ovirt-guest-agent.ini \
    $(NULL)

CLEANFILES = \
    *~ \
    55-$(AGENT_NAME).rules
