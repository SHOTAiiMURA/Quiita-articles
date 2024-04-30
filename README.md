 # ネットワークの基本
回線速度：１秒間あたりに送ることができるデータ量
伝送効率、回転利用率：実際に送ることができるデータ量は減少する。
    例）回線速度が３ｍｂｐｓ，伝送効率が５０％　＝　理論上は1,5mbPS
LAN　vs　WAN
LANは、企業、家庭内で使われる狭い範囲で使用される。
WANは、広範囲で利用される。

有線　vs　無線
有線はイーサネット（ケーブル）
CSMA／CS式とは、通信を監視して、ネットが空いている場合、データを送信。たまに、コリジョンが起きる場合がある。

無線はケーブルがいらない。そのため、利便性が高い。デメリット：ハッキングされる可能性がある。

# プロトコルとOSI参照モデル
プロトコルとは、データを送受信するためのルール。例）友人に手紙を送る場合は、いつ届くか、どこに届くかわからないといけない。PCの場合も同様。
![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/3779552/195e1119-aea1-eb06-4115-9421461a2e51.png)
送信した時、階層が変わるごとにヘッダが付与される。受信する場合は、階層が変わるごとにヘッダが外される。
![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/3779552/963f9f91-da8a-1af6-d8b4-22e6c6ab045f.png)

## Macアドレス　vs　IP アドレス

Macアドレス
パソコンについている、ポート番号のようなイメージ。
コンピューターを識別するための番号
番号が体系的でない。

IPアドレス
パソコンについている、ポート番号のようなイメージ。
コンピューターを識別するための番号
番号が体系的である。ｰ>IPアドレスは範囲がせまく特定しやすい。

# TCP/IPネットワーク
現在はTCP／IPモデルが登場。昔はOSI参照モデルが使われていた。
![Screenshot 2024-04-30 at 18.16.28.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/3779552/63cea84e-3671-8ade-9a21-4a18a5d56c3a.png)
７層から４層に変更した。
## 用語：
### IP（Internet Protocol)
異なるネットワークをつなぐ方法を定義。機器にIPアドレスを割り当て、IPアドレスに対して、パケットでデータを送る。
### TCP（Transmission Control Protocol）
通信相手との接続が確認されてから通信を行うルール。メリットは信頼性の高いデータ転送を提供可能。
### UDP（User Datagram Protocol）
信頼性は落ちるが、高速通信が可能。リアルタイム性が必要な場合に用いられる。

## IPアドレスについて
これは住所のようなイメージ。２進数３２ビットのビット列を８桁ずつ１０進数に直して表現する。
例）
![Screenshot 2024-04-30 at 18.22.24.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/3779552/8bd8ff38-3091-4a3d-6510-bca264e53a57.png)
これらの番号は重複は許されない。

## IPｖ４　VS　IPｖ６
IPv4ではアドレスが足りなくなる恐れがあったため、IPｖ６を作った。実際は現状IPｖ４でこと足りている。
テストでは、IPアドレスに指定がない限り、IPアドレス＝IPV4と認識。

## グローバルIPとプライベートIP
グローバルIPとは、IPアドレスが重複しない番号。
プライベートIPとは企業や家庭で使われる。例：A社とB社でLANないで重複がなければ、同じIPアドレスを使ってよい。
しかし、プライベートからグローバルに接続できない。理由はグローバルと重複する可能性があるから。
    どう繋げるのか？ｰ>NATを利用して、プラベIPをグローバルIPに変換する。NATはよくルーターにある仕組み。
    NAPTを使って複数のプラベIPをグローバルに変換できる。
![Screenshot 2024-04-30 at 18.30.30.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/3779552/041230fd-3533-6317-dc58-b9aae660c7f9.png)

DHCP：大企業でIPアドレスの重複しない割当の設定が難しいため、それらを自動化してくれる。

## ドメインとDNSサーバー
ドメインはウェブにあるhttps://www.google.com/

![Screenshot 2024-04-30 at 18.33.31.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/3779552/f2855c64-0596-77e6-1f38-4aec4a1b8e74.png)
例えば、Facebookを開きたい時、ユーザーはドメインを指定して送るが、DNSサーバではそのドメインに対応してるIPアドレスを返す。

# IPアドレスとサブネットマスク
IPアドレスはネットワーク部分とホスト部で構成される。
    ネットワーク部分：どのネットワークを使用しているか。
    ホスト部：ネットワークないでどのコンピューターを使用してるか指定する。
どこがネットワーク部分でホスト部分？
クラスAは大規模で使用される。
![Screenshot 2024-04-30 at 19.43.04.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/3779552/50304b17-3cf3-3186-b9fc-6ba0c314a999.png)
ｎ個のビットでは２ｎ個の表現が可能。
クラスBは中規模のネットワークで使われる。
![Screenshot 2024-04-30 at 19.45.20.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/3779552/b906a46a-88b2-45df-82bb-f820a387cf5d.png)
クラスCは小規模で使わられる
![Screenshot 2024-04-30 at 19.45.40.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/3779552/115b03e2-8c0e-02df-1659-b1803bf1213c.png)
＊＊＊テストでは出題頻度は低い＊＊＊
![Screenshot 2024-04-30 at 19.47.14.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/3779552/f69a5c85-66e4-3ddc-265d-4645c06511ab.png)

サブネットマスク
IPアドレスのネットワーク部に自由に設定可能。
![Screenshot 2024-04-30 at 19.50.14.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/3779552/b38058f0-c471-90aa-9126-39eb8842ebe4.png)
２進数８ビットに直してみる。
![Screenshot 2024-04-30 at 19.51.19.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/3779552/e4224547-bcde-7163-5587-d72d903985ac.png)
一番左の箱に１２８入るので、１９２−１２８＝６４、そして６４の箱に１が入る。６４−６４＝０なので、左から３番目に入るすべての値は０になる。
IPアドレスとサブネットマスクを同様に８列になおしてみる。
![Screenshot 2024-04-30 at 19.53.40.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/3779552/38348486-8e87-de6b-977c-43b90f3a14bd.png)
先頭２６ビットがネットワーク部、そして残りの６ビットがホスト部になる。
サブネットマスクを使用して、柔軟にネットワークを設定できる。
### サブネットマスクの記載方法
![Screenshot 2024-04-30 at 19.56.33.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/3779552/e97ff42d-5420-92a9-a006-4a01a7878d0d.png)
前半２６ビット、後半６ビットを表す。
#　その他の重要単語


引用元：https://www.youtube.com/@kihonzyouhou
