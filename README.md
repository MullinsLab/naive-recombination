# NAME

recombine-naively - Naively recombine input sequences at specified breakpoints

# SYNOPSIS

    recombine-naively --breakpoint=N [--breakpoint=N] [--group-by-file] [file.fasta ...]
    recombine-naively --help

# DESCRIPTION

Produces naive recombinant sequences (hard breaks, no mutation) from all
possible combinations of input sequences.

Input and output is in the FASTA format.

If no input files are provided, stdin is read.  Output is always to stdout.

Output sequences are named in the following manner:

    foo|@113|bar|@242|baz

where `foo`, `bar`, and `baz` are the input sequence names and `113` and
`242` are the breakpoint locations between the adjacent sequences.

# OPTIONS

- **--breakpoint=N**
- **-b N**

    Specify a breakpoint should occur _after_ position N.  Positions are 1-based.

    This option may be repeated to add multiple breakpoints.  N may also be a
    comma-separated list of positions.

    The number of breakpoints may not exceed the number of sequences and breakpoint
    positions must fall within the length of the shortest sequence.

- **--group-by-file**

    With this option, multiple files are treated as groups of similar sequences, or
    subtypes.  Sequences are recombined with sequences from other files but not
    with sequences from the same file.

    Without this option, multiple files are treated the same as a single file: all
    sequences are recombined with each other.

- **--help**

    Show this help.

# INSTALLATION

Currently the only supported way is using [cpanm](https://metacpan.org/pod/cpanm):

    cpanm --installdeps .

This will install the dependencies for everyone on the system and then you can
run this program.  You can also install dependencies in a `local/` directory
just for you:

    cpanm --installdeps -L local .

If you don't have [cpanm](https://metacpan.org/pod/cpanm) already, you can still install the dependencies in
one go:

    curl -fsSL https://cpanmin.us | perl - --installdeps -L local .

Alternatively, you can install the dependencies in `cpanfile` manually with
the standard [cpan](https://metacpan.org/pod/cpan) command.  This is equivalent to installing system-wide
with cpanm.

# AUTHOR

Thomas Sibley <trsibley@uw.edu>

# COPYRIGHT & LICENSE

Copyright (c) 2014-2015 Mullins Lab, University of Washington.

This software is licensed under the GNU General Public License, version 2.
