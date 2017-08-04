# eclair モナコインテスト

[eclair](https://github.com/ACINQ/eclair)をmonaのmainnetで動くようにしたものです。

zeromq機能が有効化されたmonacoin coreが必要です。

moancoin core 0.14.2以降の公式バイナリでは有効になっています。

## 設定方法

monacoin.confの例：

    rpcuser=hoge
    rpcpassword=fuga
    rpcallowip=127.0.0.1
    rpcport=9402
    txindex=1
    server=1
    zmqpubrawblock=tcp://127.0.0.1:29000
    zmqpubrawtx=tcp://127.0.0.1:29000

eclair.conf をデータディレクトリ (どこにあるかはosなどによる)に置きます。

例：

    eclair {
      bitcoind {
        rpcuser = "hoge"
        rpcpassword = "fuga"
        rpcport = 9402
        zmq = "tcp://127.0.0.1:29000"
      }
    
      server {
        port = 9735
      }

      api {
        binding-ip = "127.0.0.1"
        port = 8087
      }

      # node一覧に表示される名称と色(HTML形式)
      node-alias = "eclair-mona"
      node-color = "B4A98E"
    }

## 参考になりそうな動画

[Testing Lightning on Litecoin with eclair - YouTube](https://www.youtube.com/watch?v=mxGiMu4V7ns&feature=youtu.be)

## テストノード

* 03aafadba1c7608a52b8defcb880e52c76d06eb36b6cb740ef94649b2a5277701e@54.201.194.99:9735

このノードにチャンネルを貼ると、10mMONA以上の資金をテストノード側に持つチャンネルが無い場合、自動的にチャンネルを貼り返してきます（が、まだちょっと不安定です）。pushしなくても、このノードを中継しての送金テストができます。

### テスト時の注意点

* 現在、一つのチャンネルに入れる最大資金は 0.16777216 mona に制限されています。また手数料の関係で、資金が少なすぎるチャンネルはうまく閉じられないケースがあります。5mMONA(0.005mona) 〜 160mMONA(0.16MONA) くらいが適切でしょう。

* 一度に送金できる金額は 0.04294967'296 monaに制限されています。また途中のノードの設定により、少なすぎる送金は受け付けないかもしれません。(デフォルト設定では、0.00001 mona以下)

* テストは失ってもいい金額の範囲で行ってください。monaを失っても開発者は一切の責任を負いません。

## askmonaスレ

[ライトニングネットワーク実験場 - Ask Mona](http://askmona.org/4955)

