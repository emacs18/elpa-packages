Use like any other minor mode.  You'll see tooltips with dates
instead of Unix epoch times.  This mode turns on font-lock and
leaves it on forever.  You may or may not like that.

TODO: instead of letting font-lock-mode manage the `display'
property, manage it ourselves so when multiple modes specify
`display' it won't get wiped out when this mode doesn't need it
anymore.