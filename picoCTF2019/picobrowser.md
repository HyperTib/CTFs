# picobrowser
Category: Web Exploitation

Points  : 200

### Description
> This website can be rendered only by picobrowser, go and catch the flag! https://jupiter.challenges.picoctf.org/problem/50522/ (link) or http://jupiter.challenges.picoctf.org:50522

### Steps taken

Run the following to get the HTML file:
    curl https://jupiter.challenges.picoctf.org/problem/50522/
    
Nothing interesting found in the HTML.

When clicking on the Flag link we get the following error:

>You're not picobrowser! Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/87.0.4280.141 Safari/537.36

Copy the request in curl format and changed the User-Agent value to picobrowser:

    curl 'https://jupiter.challenges.picoctf.org/problem/50522/flag' \
      -H 'Connection: keep-alive' \
      -H 'Upgrade-Insecure-Requests: 1' \
      -H 'User-Agent: picobrowser' \
      -H 'Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.9' \
      -H 'Sec-Fetch-Site: same-origin' \
      -H 'Sec-Fetch-Mode: navigate' \
      -H 'Sec-Fetch-User: ?1' \
      -H 'Sec-Fetch-Dest: document' \
      -H 'Referer: https://jupiter.challenges.picoctf.org/problem/50522/' \
      -H 'Accept-Language: en-CA,en;q=0.9,en-GB;q=0.8,en-US;q=0.7,fr;q=0.6' \
      -H 'Cookie: _ga=GA1.2.2132573795.1610993605; _gid=GA1.2.197241733.1610993605' \
      --compressed
      
The HTML response we get will contain the flag.
