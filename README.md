# har2sequence

Convert HTTP Archive format (HAR) to websequencediagrams compatible output.

# HAR files

The HTTP Archive format or HAR, is a JSON-formatted archive file format for
logging of a web browser's interaction with a site. The common extension for
these files is .har.

The specification for the HTTP Archive (HAR) format defines an archival format
for HTTP transactions that can be used by a web browser to export detailed
performance data about web pages it loads. The specification for this format is
produced by the Web Performance Working Group of the World Wide Web Consortium
(W3C). The specification is in draft form and is a work in progress.

# Sequence Diagrams

Sequence diagrams are a type of UML diagram that show the interaction between
entities where time passes from top to bottom. In this case we are using them
to show the interactions between a web browser and a one or more web servers.

# Web Sequence Diagrams

The png, svg and pdf outputs are generated via the websequencediagrams.com API.
This API returns invalid JSON with unquoted keys, in order to deal with this we
are using the allow_barekey method from the JSON::PP perl module. When
interacting with this service the script prsents the following useragent:
`har2sequence/0.1`.

# Installation

This script makes use of a number of perl modules. You can install these on a
Debian based system using the following command:

    $ sudo apt-get install libfile-slurp-perl libdata-dump-perl  libjson-pp-perl libtext-simpletable-perl libdata-dump-perl
    $ git clone https://github.com/donovan/har2sequence.git
    $ cd har2sequence

# Usage

Save a har file using an appropriate tool (eg chrome developer tools).

    $ ./har2seqence www.foo.com.har
    $ ./har2sequence --help
    Usage:
        har2sequence [options] <HAR file>

        Options:

        --help        detailed help message
        --output      output format, supports txt (default), table, dump, png, svg or pdf
        --outfile     override the output filename
        --style       websequencediagrams styles, use --list-styles for a listing
        --list-styles list valid styles for websequencediagrams

# Output formats

## TXT
## Table
## Dump
## PNG
## SVG
## PDF

# Examples

# Links

* https://dvcs.w3.org/hg/webperf/raw-file/tip/specs/HAR/Overview.html
* http://www.softwareishard.com/blog/har-adopters/
* https://en.wikipedia.org/wiki/.har
* https://www.igvita.com/2012/08/28/web-performance-power-tool-http-archive-har/
* http://www.softwareishard.com/blog/har-12-spec/
* https://bramp.github.io/js-sequence-diagrams/
* https://www.websequencediagrams.com/
* https://en.wikipedia.org/wiki/Sequence_diagram
* https://metacpan.org/pod/Archive::Har
* https://www.websequencediagrams.com/embedding.html
