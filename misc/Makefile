gen/autocomp.js: $(wildcard ../*) $(wildcard ../speeches/*) $(wildcard ../lists/*) ../scripts/gather_lists.sh
	../scripts/gather_lists.sh > gen/autocomp.js

gen/%.html: %.md head.html header.html
	cat head.html > $@
	head -n 1 $< | tr -d '#' >> $@
	echo '</title></head><body>' >> $@
	cat header.html >> $@
	pandoc -f markdown $< >> $@
	echo '</body></html>' >> $@

gen/Programs.html: ../scripts/create-program-list.sh $(wildcard ../lists/*.lst)
	cd .. && ./scripts/create-program-list.sh > misc/gen/Programs.html

ALLH=$(patsubst %.md, gen/%.html, $(wildcard *.md))
all: ${ALLH} gen/autocomp.js gen/Programs.html

