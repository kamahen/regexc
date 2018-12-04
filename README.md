# regexc

## Introduction

regexc is a regular expression compiler. It takes a regular expression as input and creates a binary,
that matches that regular expression, as output.

My goal for this project was to explore using prolog in a practical setting. That means understanding
things like developer workflow, project layout, and argument parsing. Although the use of the this 
project is a bit contrived, I hope that it can serve as an accessable example of for what the source
of a practical prolog application might look like.

## For Developers

You will need to install [SWI Prolog](http://www.swi-prolog.org). I recomend using your package 
manager of choice. I'm on macOS so I used [brew](https://brew.sh).

```
brew install swi-prolog
```

To run the documenation server you should be in the `src` directory.

```
cd src
swipl -f documentation_server.pl
```

While working on the source code, I recomend starting a SWI-Prolog session with that consults the load module.
Whenever you want to consult your changes, run [make/0](http://www.swi-prolog.org/pldoc/doc_for?object=make/0).

```
$ swipl -f src/load.pl
<blah blah>
?-

...

?- make.
% <blah blah>
true.
```

If you are adding a new module, please add it to `src/load.pl`.

## Design Decisions

### Argument Parsing
	
SWI Prolog provides an [optparse](http://www.swi-prolog.org/pldoc/man?section=optparse) module that is
modeled after python's own opt parse. These modules provides the minimum of what we would expect from 
an argument parsing library in any language: one specification can be used to both generate a help 
message and check the list of inputs to the tool.

### Testing

SWI Prolog includes a unit test package, [plunit](http://www.swi-prolog.org/pldoc/doc_for?object=section(%27packages/plunit.html%27).

For now, the best option is consulting the load file and running
```
?- show_coverage(run_tests).
```

## Future Work

* I have not found a good solution for source formatting. There are some promising avenues however.

	- [package-indent](https://github.com/SWI-Prolog/packages-indent/blob/master/indent.pl) is written by
Jan Wielemaker himself. Initially, I found that it did not produce the expected results (removed
lines for example). However I was likely holding it wrong, did not have well made code.

	- [vcs-prolog](https://github.com/arthwang/vsc-prolog) is a VS Code plugin that provides, among
other things, prolog source formatting. It is much newer than package-indent, and was also a supervised
by Jan Wielmaker.

* I had trouble with the optparse module. The trouble was not unique to that module, however. The
issue I faced was the the specification is a very specific kind of structure. Any goals that 
expected that structure would simply fail if it did not meet match the expectations. In this case
I think it would be wise to have some goal that can type-check or parse the application structure
and give detailed feedback on why it does not meet expections. Adding such a goal to SWI Prolog might
be worth opening an issue / making a pull request.

	```
	opt_check_spec(+OptsSpec, -Errors)
	```

## Sources

I found this project to be a useful example of many prolog techniques.
[Alan Compiler by thanosqr](https://github.com/thanosqr/Alan-Prolog-Compiler)

I found this SO question useful when investigating how to handle input.
[String Stream in Prolog?](https://stackoverflow.com/questions/23593156/string-stream-in-prolog)
