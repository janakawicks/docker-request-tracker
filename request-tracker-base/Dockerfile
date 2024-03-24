FROM alpine:3.19

RUN apk add --no-cache --virtual .build-deps alpine-sdk curl perl-dev

RUN curl https://download.bestpractical.com/pub/rt/release/rt-5.0.5.tar.gz > /tmp/rt-5.0.5.tar.gz && cd /opt/ && tar xzvf /tmp/rt-5.0.5.tar.gz && rm /tmp/rt-5.0.5.tar.gz

RUN apk add --no-cache perl perl-app-cpanminus spawn-fcgi graphviz gpg gpg-agent

RUN apk add --no-cache perl-apache-session perl-business-hours perl-fcgi perl-cgi perl-cgi-emulate-psgi perl-cgi-psgi perl-css-minifier-xs perl-css-squish perl-class-accessor perl-clone perl-convert-color perl-crypt-eksblowfish perl-dbi perl-dbix-searchbuilder perl-data-guid perl-data-ical perl-data-page perl-datetime perl-datetime-format-natural perl-datetime-locale perl-date-extract perl-date-manip perl-devel-globaldestruction  perl-email-address perl-email-address-list  perl-encode-hanextra perl-html-formattext-withlinks-andtables perl-html-mason-psgihandler perl-html-scrubber perl-html-quoted perl-html-rewriteattributes perl-json perl-javascript-minifier perl-javascript-minifier-xs perl-lwp-protocol-https perl-locale-maketext-fuzzy perl-locale-maketext-lexicon perl-mime-types perl-module-versions-report perl-module-refresh perl-moose perl-moosex perl-mozilla-ca perl-net-cidr perl-net-ip perl-parallel-forkmanager perl-plack  perl-regexp-common perl-regexp-common-net-cidr perl-role-basic perl-scope-upper perl-symbol-global-name perl-term-readkey perl-text-password-pronounceable perl-text-quoted perl-text-template perl-text-wikiformat perl-text-wrapper perl-time-parsedate perl-tree-simple perl-xml-rss perl-dbd-mysql perl-crypt-x509 perl-file-which perl-string-shellquote perl-log-dispatch perl-mime-tools perl-regexp-ipv6 perl-gd perl-gdgraph perl-gdtextutil perl-net-ldap perl-dbd-pg

RUN cpanm --notest Encode::Detect::Detector HTML::FormatExternal HTML::Gumbo Module::Path MooseX::NonMoose MooseX::Role::Parameterized Path::Dispatcher Plack::Handler::Starlet Text::WordDiff Web::Machine GraphViz2 GnuPG::Interface PerlIO::eol

RUN cd /opt/rt-5.0.5 && ./configure --enable-gd --enable-graphviz --enable-externalauth --enable-smime --enable-gpg && make install

RUN apk del .build-deps
