# HastyHex : a faster hex dumper

HastyHex is a ***blazing fast*** hex dump utility with optional ANSI
color output. It performs about *one to two orders of magnitude* faster
than your typical implementation of `hexdump` or `od`. It's is written
in plain old ANSI C, so you can run it literally anywhere.

This is a fork that look to be right with your output...

## Usage

HastyHex produces color output by default and take care of output.
The `-p` option forces color to any output.

    usage: hastyhex [-fhlp] [-o FILE]
      -h       print this help message
      -l       force output line-buffered
      -f       force output fully-buffered
      -o FILE  output to file instead of standard output (windows only)
      -p       do force output color (through pipe and redirect)

The `less` pager has a `-R` argument that understands ANSI color escape
sequences, making it a great candidate for accepting output from
HastyHex.

    $ hastyhex -p data.bin | less -FRX

The `-f` option increases the output buffer size which typically
improves performance. Since MSVC doesn't support line-buffering, `-l`
will be equivalent to `-f` on Windows. The `-p` option let color persists
through pipe and redirection.
