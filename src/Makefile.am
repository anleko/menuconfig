bin_PROGRAMS	= mconf conf
mconf_SOURCES	= mconf.c zconf.tab.c lxdialog/checklist.c lxdialog/inputbox.c lxdialog/menubox.c lxdialog/textbox.c lxdialog/util.c lxdialog/yesno.c
conf_SOURCES	= conf.c zconf.tab.c

zconf.tab.c : zconf.y zconf.lex.c
	$(YACC) -o$@ -t -l $<

zconf.lex.c : zconf.l
	$(LEX) -o$@ -L $<

mconf_CFLAGS = $(ncurses_CFLAGS)
mconf_LDFLAGS = -static
mconf_LDADD  = $(ncurses_LIBS)