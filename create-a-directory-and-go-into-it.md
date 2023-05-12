Create a directory and go into it.

Sometime the smallest bash scripts will help you stopping from doing the same thing over and over again.
E.g. typing `mkdir sample` and then `cd sample`.

Let's create a very small function that always takes you into the directory you just created.

---

	# Create a new directory and enter it

	function mkd() {
   		mkdir -p "$@" && cd "$@"
	}

Now you just have to type `mkd sample` and you are inside the sample directory.

Not the most shocking example, but you can use these simple functions to prevent repetitive commands.


Tags: bash-scripts
