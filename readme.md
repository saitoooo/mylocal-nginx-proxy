# MyLocal Nginx Proxy

開発用にSSLのWebが欲しくなる時があるので、これDockerComposeで立ち上げて置き、VirtualHostでSSL(SNI)接続出来ればと思って作っています。

# 証明書について

* local.crt
* local.key

として用意してあります。その為に ** hoge.local ** や ** hage.local ** といったホストであればそのままこの証明書が使えます。
もちろんオレオレ証明書なのはご理解ください。

# Volumeについて

```yaml
    volumes:
      # - /run/user/501/docker.sock:/tmp/docker.sock:ro
      - /var/run/docker.sock:/tmp/docker.sock:ro      
```

としていますが、これはlima上でDockerで使う際には/run/user/501/docker.sockとする必要があったためです。
環境に応じて変更してください

# 使い方は

/etc/hosts もしくは相当機能に、localドメインでのホスト名を作成してください。
その後、別のDockerでVIRTUAL_HOST環境変数を設定したWebサーバを立ち上げて頂ければ接続できると思います。
（jwilder/nginx-proxyの標準的な使い方ですね）


