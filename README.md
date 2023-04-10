# carbonapi-web

This is a fork of graphite-project/graphite-web removing all the Python
code, and just retaining the JavaScrip browser frontend.

The aim for this fork is to be used with on a static/non-interpreted
stack, which interfaces well with either graphite-web running elsewhere
(or in Docker instance) or using carbonapi with carbonzipper and
go-carbon stack.

Reasoning for doing this are twofold:
1. Python deps for graphite-web are aging, and not keeping up with the
   Python release system, making it harder to securely run the graphite
   stack this way.  In fact, on some distros, the required deps are even
   no longer available due to these concerns.
2. The go-carbon stack outperforms the Python-based originals especially
   on very large scale setups, in such case, the Python stack is not
   used, and not necessary to be installed either.


## Installation, Configuration and Usage

It is recommented to setup carbonapi (the graphite-project or bookingcom
version) and use carbonapi-web against that using a vhost that glues
together the two.  For example setup an nginx server that proxies the
following urls to carbonapi, and handles the rest from carbonapi-web
sources:
- /render/
- /metrics/
- /info/
- /functions/
- /tags/

## License

Graphite-Web is licensed under version 2.0 of the Apache License. See the [LICENSE](https://github.com/graphite-project/graphite-web/blob/master/LICENSE) file for details.  Carbonapi-web is thus licensed the same way.
