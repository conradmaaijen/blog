Parameters in bash script

	> ./test.sh one two "three four"

Output:

	$1 = one
	$2 = two
	$3 = three four

	# Size of the input array
	$# = 3

Example script:

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

## Flags

Another way of passing input to a script is using flags.

	sh test.sh -f 'John Smith' -a 25 -u john

We’ll modify the earlier script to use flags instead of relying on positional parameters. The getopts function reads the flags in the input, and OPTARG refers to the corresponding values:

    `#!/bin/bash

    while getopts u:a:f: flag
    do
        case "${flag}" in
            u) username=${OPTARG};;
            a) age=${OPTARG};;
            f) fullname=${OPTARG};;
        esac
    done

    echo "Username: $username";
    echo "Age: $age";
    echo "Full Name: $fullname";

Let’s run this script with the same input as before, only this time, we’ll add flags to the input:

    sh test.sh -f 'John Smith' -a 25 -u john

The output is the same as before, though we have shifted the positions of the username and full name arguments:

    Username : john
    Age: 25
    Full Name: John Smith
    Tags: bash
