### DNS via ```bind```
#### package
- bind-libs
- bind-utils
- bind

#### named.conf (/etc)
```
listen-on port 52 { any; };
allow-query { any ;};


zone "gsafety-co.com" IN {
    type master;
    file "gsafety-co.com.zone";
    allow-update { none; };
};

zone "180.10.17.172.in-addr.arpa" IN {  # 反转IP
    type master;
    file "172.17.10.180.zone";
    allow-update { none; };
};
```

#### gsafety-co.com.zone (/var/named) (/var/named/)
```
$TTL 1M
@   IN  SOA www.gsafety-co.com. root.gsafety-co.com. (
            1   ; serial id
            1M  ; refresh delay
            1M  ; retry delay
            1M  ; expiry
            1M  ; negative cache TTL
)
; name servers  NS
            IN  NS  www

; name servers  A
www         IN  A   172.17.10.180
```

#### 172.17.10.180.zone
```
$TTL 3H
@   IN  SOA gsafety-co.com.  root.gsafety-co.com. (
            1   ; serial id
            1M  ; refresh delay
            1M  ; retry delay
            1M  ; expiry
            1M  ; negative cache TTL
)
; name servers  NS
                NS  @

; name servers  A
                A   127.0.0.1

; PTR
180.10.17.172   IN  PTR www.gsafety-co.com.
```

#### 服务名称 named
