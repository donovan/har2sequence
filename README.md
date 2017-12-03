# har2sequence

Convert [HTTP Archive
format](https://dvcs.w3.org/hg/webperf/raw-file/tip/specs/HAR/Overview.html)
(HAR) to [websequencediagrams](https://www.websequencediagrams.com/) compatible
output. Supports automatic fetching sequence diagrams from websequencediagrams
via an API call.

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
interacting with this service the script presents the following useragent:
`har2sequence/0.1`.

# Installation

This script makes use of a number of perl modules. You can install these on a
Debian based system using the following command:

    $ sudo apt-get install libfile-slurp-perl libdata-dump-perl \
    libjson-pp-perl libtext-simpletable-perl libdata-dump-perl
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
        --host        use Host header instead of Server IP
        --style       websequencediagrams styles, use --list-styles for a listing
        --list-styles list valid styles for websequencediagrams

# Output formats

## TXT

This is the default output.

Outputs a sequence diagram defined as txt as used by tools like
[websequencediagrams](https://www.websequencediagrams.com/) and
[js-sequence-diagrams](https://bramp.github.io/js-sequence-diagrams/). This
format is not properly specified anywhere, As far as I know it was created by
websequencediagrams, the best definition I know of is
[here](https://www.websequencediagrams.com/examples.html).

## Table

Text table output.

## Dump

Dump perl data structure as output.

## PNG

Submit txt to websequencediagrams via API and save the returned png.

## SVG

Submit txt to websequencediagrams via API and save the returned svg.

## PDF

Submit txt to websequencediagrams via API and save the returned pdf.

# Examples

Parse a har file and output websequencediagrams txt format:

    $ ./har2sequence example.har

Retrieve a png sequence diagram that uses the napkin style from
websequencediagrams. Make use of hosts headers for server names.

    $ ./har2sequence --host --output png --style napkin example.har
    retrieved example.png from http://www.websequencediagrams.com/?img=example123

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
