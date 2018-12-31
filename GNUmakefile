
all : revert-date-changes
	git diff

revert-date-changes:
	git diff -G"^ *.dt.Latest./dt.*" | patch -p1 -R
