# Probabilistic Inference Primer

This is a growing document on everything you need to know about:

1. Probabilistic Graphical Models
2. Factor Graphs as an instance of such a model
3. MCMC Sampling Methods
4. How to run Metropolis Hastings on a Graphical Model
5. Why this is the same as optimization, and when it's better that Convex Optimization
6. 


## Installing LaTeX on Mac

If you already have the entire 2.1GB MacTeX repository, then you should be all set!

But if not, here's how to get the stripped-down version running:

1. Install BasicTeX from here: http://www.tug.org/mactex/morepackages.html

2. Install the Tex Live Utility to manage packages from here: https://code.google.com/p/mactlmgr/

3. Install the Helvetica font:
        sudo tlmgr install helvetic

4. Install the Courier font:
        sudo tlmgr install courier

5. Install the preprint package to get Balanced Columns:
        sudo tlmgr install preprint

6. Install the boxedpage

Now you can run Make to build the paper!

## Setting up the Build System in Sublime Text to call our Makefile

Sublime Text can automatically call our makefile if we set it up correctly.
http://docs.sublimetext.info/en/latest/reference/build_systems.html

We copy the Make build system configuration to LaTex, and change it to associate with LaTeX files:

	cd ~/Library/Application\ Support/Sublime\ Text\ 2/Packages/
	cp Makefile/Make.sublime-build LaTeX/Make.sublime-build
	sed -e 's/source.python/text.tex.latex/g' LaTeX/Make.sublime-build > LaTeX/LaTeX.sublime-build
	rm LaTeX/Make.sublime-build

If you're in LaTeX mode, you can now hit Command-B to run the makefile.

You can also add a variant to this build system that will open the pdf for us.
Modify LaTeX.sublime-build's variants array as follows:

	"variants":
	[
		{
			"name": "Clean",
			"cmd": ["make", "clean"]
		},
		{
			"name": "Run",
			"cmd": ["make", "run"]
		}
	]