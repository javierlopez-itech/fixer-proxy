# Propose solution

Use Varnish to cache the response from the backend server (origin).

# Problems

Varnish open source doesn't support backends on HTTPS (you have to upgrade to the premium version). The solution to this is to add an nginx reverse proxy
to the backend we want to proxy Varnish. So, they traffic goes like this

Client -- HTTPs --> Varnish -- HTTP --> Nginx -- HTTPs --> Origin

Since fixer.io already sends the right HTTP headers to handle HTTP caching (https://fixer.io/documentation) Varnish will take care of us automagically for caching.
 
