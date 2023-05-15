Parameters in bash script

	> ./test.sh one two "three four"

Output:

	$1 = one
	$2 = two
	$3 = three four

	# Size of the input array
	$# = 3

Example script:

#!/bin/bash

    echo "Using \"\$*\":"
    for a in "$*"; do
        echo $a;
    done

    echo -e "\nUsing \$*:"
    for a in $*; do
        echo $a;
    done

    echo -e "\nUsing \"\$@\":"
    for a in "$@"; do
        echo $a;
    done

    echo -e "\nUsing \$@:"
    for a in $@; do
        echo $a;
    done

The explanation and the results for the four cases are below.

In the first case, the parameters are regarded as one long quoted string:

    Using "$*":
    one two three four

Case 2 (unquoted) - the string is broken into words by the for loop:

    Using $*:
    one
    two
    three
    four

Case 3 - it treats each element of $@ as a quoted string:

    Using "$@":
    one
    two
    three four

Last case - it treats each element as an unquoted string, so the last one is again split by what amounts to for three four:

    Using $@:
    one
    two
    three
    four




Tags: bash
