# Yet abother Genius blocker

This is yet another Genius blocker.  I have combined elements from 
[Todd Kennedy’s Genius blocker](https://github.com/toddself/genius-blocker)
and
[Marla Brizel’s Genius blocker](https://github.com/marlabrizel/genius-blocker/)
to make my own easy-to-install (as long as you can control the HTML
files) Genius blocker.

## What is Genius?

Genius, for people who do no know, is the latest incarnation of the
often tried and never successful “Let’s allow random Internet trolls
and crackpots to put abusive graffiti on everyone’s webpage” browser
plugin.  It has been tried several times before: Third Voice from
the original 1990s dot-com era was probably the first commercial attempt;
there was also Diigo, Fleck, ShiftSpace, Stickis, Trailfire, and Google
SideWiki.  

Google’s now-dead SideWiki was an attempt by Google to put their own
content on every single page on the Internet. SideWiki was a browser
extension that added, to the left of every web page, a section where
anyone on the Internet could comment on the web page or anything else;
the comments were visible to anyone else on the internet who visited
that web page and had SideWiki installed.

Google introduced it in the fall of 2009. It, thankfully, did not last
very long. In under two years, Google already announced its termination;
it was removed (including having all comments deleted) before the end
of 2011.

They never even implemented a way for webmasters to opt out of it,
despite repeated requests for them to do so.

SideWiki was a haven for spammers, trolls, crackpots and pretty much
no one else. Here is some of the documented abuse SideWiki was forcing
webmasters to put up with:

[http://marketersboard.com/google-sidewiki-controversy/](https://archive.is/7BN3Z)

Also, here is Jeff Jarvis’ well articulated criticism of SideWiki:

http://buzzmachine.com/2009/09/23/google-sidewiki-danger/ 

Genius is pretty much the same thing, and it’s also causing
controversey:

https://ellacydawson.wordpress.com/2016/03/25/how-news-genius-silences-writers/

A congresswoman even chipped in to complain about the service:

http://recode.net/2016/03/29/genius-responds-to-congresswoman-katherine-clarks-letter-on-preventing-abuse/

## What this script does

This script blocks Genius from being able to add annotations to a given
web page.  Not only does it block “genius.it” URLs, it also blocks Genius’s
bookmarklet and Chrome plugin.

## How to install it.

Put the file genius-blocker.js in the same directory as the html
files which you want to not allow to be annotated by Genius.

Put this at the *BOTTOM* of a given .html file, just before the closing
`</body>`
tag:

```html
<script src="genius-blocker.js"></script>
```

It must be at the bottom of the HTML file.  Here is how a full HTML web
page may look:

```html
<html><head><title>Example Genius blocked page</title></head><body>
This is an example page which Genius.it is blocked from annotating.
<script src="genius-blocker.js"></script></body></html>
```

Here is a script which uses Bash (actually, just bog vanilla POSIX 
compatible Bourne shell) and Perl to add a reference to the Genius 
Blocker to each .html file in a given directory:

```bash
for a in *html ; do 
    cat $a | \
perl -pe 's|(</body>)|<script src="genius-blocker.js"></script>$1|i' > foo
    mv foo $a
done
```

*Warning* This script will alter all the .html files and could corrupt
files. Use with caution.

Again, put genius-blocker.js in the same directory as the HTML files. 
The blocker should also work with PHP scripts and what not, using the
same principle. 

It’s also possible to have an absolute path to genius-blocker.js; it
does not need to be in the same directory (I only suggest this because
doing so makes it a bit easier to describe how to install).
