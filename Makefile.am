CXXFLAGS = -g -Wall -Werror
INCLUDES = @SIGC_CFLAGS@
LDADD = @SIGC_LIBS@

bin_PROGRAMS = rec play squelch encode capture plot log streamer splitter monitor demux emailer
# note that 'insertdb' is omitted because it's currently written to work with a very old version of libpq

htmldir = $(prefix)/html
html_DATA = rec.html squelch.html capture.html log.html streamer.html splitter.html demux.html emailer.html insertdb.html

man_MANS = rec.1 squelch.1 capture.1 log.1 streamer.1 splitter.1 demux.1 emailer.1 insertdb.1

EXTRA_DIST = $(man_MANS)

rec_SOURCES = rec.cpp

play_SOURCES = play.cpp

squelch_SOURCES = squelch.cpp

encode_SOURCES = encode.cpp

capture_SOURCES = capture.cpp eas_demod.cpp eas_decode.cpp

plot_SOURCES = plot.cpp

log_SOURCES = log.cpp

streamer_SOURCES = streamer.cpp

splitter_SOURCES = splitter.cpp

monitor_SOURCES = monitor.cpp eas_demod.cpp eas_decode.cpp

demux_SOURCES = demux.cpp

emailer_SOURCES = emailer.cpp eas_decode.cpp

#insertdb_SOURCES = insertdb.cpp eas_decode.cpp

eas_decode.cpp: fips.inc

fips.inc: county.dump fips2inc.pl
	perl fips2inc.pl county.dump >$@

.1.html:
	true rman -f html $< >$@
	nroff -man $< | man2html -topm 6 -compress -title '$< manual page' -cgiurl '$$title.html' | perl linkify.pl >$@
