# regexc

# Intro

regexc is a regular expression compiler. It takes a regular expression as input and creates a binary
that matches that regular expression.

My goal for this project was to explore using prolog in a practical setting. That means understanding
things like developer workflow, project layout, and solving mundane problems like argument parsing.
Althought the use of the this project is a bit contrived, I hope that it can serve as an accessable
example of what a practical prolog application might look like.

# For Developers

To run the documenation server you should be in the `src` directory.

```
cd src
swipl -f documentation_server.pl
```

While working on the source code, I recomend starting a SWI-Prolog session with that consults all
the files int the `src` directory. Whenever you want to consult your changes, run
[make/0](http://www.swi-prolog.org/pldoc/doc_for?object=make/0).

```
$ swipl -f src/*
Welcome to SWI-Prolog (threaded, 64 bits, version 7.6.4)
SWI-Prolog comes with ABSOLUTELY NO WARRANTY. This is free software.
Please run ?- license. for legal details.

For online help and background, visit http://www.swi-prolog.org
For built-in help, use ?- help(Topic). or ?- apropos(Word).

?-

...

?- make.
% <blah blah>
true.
```

If you are adding a new module, please add it to `src/load.pl`.

## Future Work

* I have not found a good solution for source formatting. There are some promising avenues however.

	- [package-indent](https://github.com/SWI-Prolog/packages-indent/blob/master/indent.pl) is written by
Jan Wielemaker himself. Initially, I found that it did not produce the expected results (removed
lines for example). However I was likely holding it wrong, did not have well made code.

	- [vcs-prolog](https://github.com/arthwang/vsc-prolog) is a VS Code plugin that provides, among
other things, prolog source formatting. It is much newer than package-indent, and was also a supervised
by Jan Wielmaker.

* I have not found a good testing pattern. I really want to be able to run `make test` and see something like
`n/n test are successful`!

## Sources

I found this project to be a useful example of many prolog techniques.
[Alan Compiler by thanosqr](https://github.com/thanosqr/Alan-Prolog-Compiler)

I found this SO question useful when investigating how to handle input.
[String Stream in Prolog?](https://stackoverflow.com/questions/23593156/string-stream-in-prolog)