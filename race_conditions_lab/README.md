# Race-Condition Vulnerability Lab

This lab is part of the [SEED Labs](http://www.cis.syr.edu/~wedu/seed/). 

Refer to the [lab webpage](http://www.cis.syr.edu/~wedu/seed/Labs_12.04/Software/Race_Condition/) for full details.

Needed Files: [Description](http://www.cis.syr.edu/~wedu/seed/Labs_12.04/Software/Race_Condition/Race_Condition.pdf), [`vulp.c`](http://www.cis.syr.edu/~wedu/seed/Labs_12.04/Software/Race_Condition/files/vulp.c), [`check.sh`](http://www.cis.syr.edu/~wedu/seed/Labs_12.04/Software/Race_Condition/files/check.sh)

# Tips

- Do not forget to compile with the correct permissions

		gcc vulp.c -o vulp && sudo chown root vulp && sudo chmod +s vulp

- Are you creating the correct symbolic link? Try 

		echo "hello" > /tmp/XYZ

and see if the expected file is being written.

- You may want to try first your script without trying to win the race. File `attack-v0.sh` sleeps for 3 seconds to give you a vulnerability window between the TOC and TOU. This one is easier to defeat.

- Notice that if the program `vuln` writes on `/tmp/XYZ` while it has no link to another file then there is no way to win the race. The file `/tmp/XYZ` will then be owned by `root` and you can no longer link it anywhere.
