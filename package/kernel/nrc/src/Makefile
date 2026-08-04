# SPDX-License-Identifier: GPL-2.0

M_SRC = nrc

obj-m += $(M_SRC).o
$(M_SRC)-objs = \
		nrc-mac80211.o \
		nrc-mac80211-twt.o \
		nrc-twt-sched.o \
		nrc-trx.o \
		nrc-init.o \
		nrc-debug.o \
		hif.o \
		wim.o \
		nrc-fw.o \
		nrc-netlink.o \
		nrc-hif-cspi.o \
		mac80211-ext.o \
		nrc-stats.o \
		nrc-pm.o \
		nrc-dump.o \
		nrc-bd.o \
		nrc-s1g.o \
		nrc-trace.o \
		nrc-ps.o \

ccflags-y := \
	-I$(src) \
	-DDEBUG \
	-DCONFIG_NRC_HIF_CSPI \
	-DENABLE_DYNAMIC_PS \
	-Dregulatory_set_wiphy_regd_sync_rtnl=regulatory_set_wiphy_regd_sync

ldflags-y += -T$(M)/nrc.lds


ifeq ($(TESTMODE), y)
ccflags-y += \
		-DTEST_SELF_GENERATION
endif

#ccflags-y += -Wall -Werror -g
ccflags-y += -Wall -Werror

ccflags-y += -DCONFIG_NRC_TRACING

#ccflags-y += -DENABLE_HW_RESET
