HTTP/2 with HAProxy and Nginx
=============================

Install nghttp2 (an HTTP/2 client)

    sudo pacman -Sy nghttp2
    
Start the containers

    docker-compose up
    
Request `index.html`

    nghttp -vvv https://moellers.local
    
And you see it works!

    [  0.038] recv (stream_id=13) :method: GET
    [  0.038] recv (stream_id=13) :path: /style.css
    [  0.038] recv (stream_id=13) :scheme: https
    [  0.038] recv (stream_id=13) :authority: moellers.local
    [  0.038] recv (stream_id=13) accept-encoding: gzip, deflate
    [  0.038] recv (stream_id=13) user-agent: nghttp2/1.33.0
    [  0.038] recv PUSH_PROMISE frame <length=51, flags=0x04, stream_id=13>
              ; END_HEADERS
              (padlen=0, promised_stream_id=2)
    [  0.038] recv (stream_id=13) :status: 200
    [  0.038] recv (stream_id=13) server: nginx/1.15.4
    [  0.038] recv (stream_id=13) date: Tue, 02 Oct 2018 00:06:45 GMT
    [  0.038] recv (stream_id=13) content-type: text/html
    [  0.038] recv (stream_id=13) last-modified: Mon, 01 Oct 2018 23:31:56 GMT
    [  0.038] recv (stream_id=13) etag: W/"5bb2ae6c-1aa"
    [  0.038] recv (stream_id=13) x-scheme: http
    [  0.038] recv (stream_id=13) content-encoding: gzip
    [  0.038] recv HEADERS frame <length=117, flags=0x04, stream_id=13>
              ; END_HEADERS
              (padlen=0)
              ; First response header

**Note:** Because of a [bug in Nginx](https://trac.nginx.org/nginx/ticket/1549#ticket) the push does not currently work in the browser.
