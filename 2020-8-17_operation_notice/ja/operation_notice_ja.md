# loxygenK が保有する鍵の運用について

## 単語の定義

- **KID**: Keyid
  キー ID．
- **FP**: Fingerprint
  フィンガープリント．
- **鍵**
  PGP 鍵．

## 概要

現在私が運用しているキーペア及び鍵について，以下の通り運用します:

| キーペアのマスターキーの KID | 運用方針                                                     |
| ---------------------------- | ------------------------------------------------------------ |
| **`4698AEC661CCD81E`**       | 主にこのキーペアを使用します．                               |
| **`DA5BE9A08388C939`**       | **サブキーが失効していましたが，失効日時を 2023/04/01 ( UTC ) に延期しました．**<br />**マスターキーの失効日時も 2023/04/01 ( UTC ) に設定しましたが，`61CCD81E` と同様に更新します．** |
| `FEB0F89E6E1EB2D9`           | **2021/09/25 (JST, UTC+9) に期限切れで失効します．**         |
| `94FBB0880BC97D4E`           | 既に失効していますが，失効日時の延期は行いません．           |

## 内容

### 主に使用するキーペアの変更

YubiKey を新しい鍵でセットアップしたことにより，秘密鍵の漏洩リスクが減少したことを受け，主に使用する鍵を変更することにしました．また，無意味に複数のキーペアを運用していて，コスト面や安全面に問題を感じたため，使用するキーペアは 1 つに統一することにしました．

これまでは以下のキーペアを使用していました:

- マスターキー
  KID: `DA5BE9A08388C939`
  FP: `A244 6E2B F1A7 AC90 28F1  71A3 DA5B E9A0 8388 C939`
  1. サブキー (署名兼認証用)
     KID: `5C101C888CCB1194`
  2. サブキー (暗号化/復号用)
     KID: `9CE3B37FB3509E8A`

- マスターキー
  KID: `94FBB0880BC97D4E`
  FP: `AEF0 5495 AC12 23CB 3904  C4C9 94FB B088 0BC9 7D4E`
  1. サブキー ( 署名兼認証用 )
     KID: `0BEBEA47F6DE1EE3`
  2. サブキー ( 暗号化/復号用 )
     KID: `D7CE63F383C4B204`

- マスターキー
  KID: `FEB0F89E6E1EB2D9`
  FP: `56C5 EC0D 2245 3CE5 D6C7  FFA4 FEB0 F89E 6E1E B2D9`

**これからは以下のキーペアを主に使用します**:

- マスタ/ーキー
  KID: `4698AEC661CCD81E`
  FP: `1899 551D D3D1 B9DB 355A  EF24 4698 AEC6 61CC D81E` )
  1. サブキー (署名用)
     KID: `3573FF548427FF69`
  2. サブキー (認証用)
     KID: `69CACB625254BDD1`
  3. サブキー (暗号化/復号用)
     KID: `871A5B6C051C3CA9`

### 鍵の失効予定

これまで使用していた鍵は，運用方法上に安全面の問題がありました．加えて，前項で宣言した変更により以下に上げる鍵が主に使われる鍵として使われるケースはなくなりました．

**以下の鍵は，2021/09/25 ( JST, UTC+9 ) に期限切れによって失効します．**

- マスターキー
  KID: `FEB0F89E6E1EB2D9`
  FP: `56C5 EC0D 2245 3CE5 D6C7  FFA4 FEB0 F89E 6E1E B2D9`

### 鍵の失効日時の調整について

以下のキーペアは，**サブキーが失効していましたが，失効日時を 2023/04/01 (UTC) に延長しました**．また，**マスターキーの失効日時も併せて 2023/04/01 ( UTC ) に延長しました**．

- マスターキー
  KID: `DA5BE9A08388C939`
  FP: `A244 6E2B F1A7 AC90 28F1  71A3 DA5B E9A0 8388 C939`

  1. サブキー (署名兼認証用)
     KID: `5C101C888CCB1194`

  2. サブキー (暗号化/復号用)
     KID: `9CE3B37FB3509E8A`

この失効日時は，KID `61CCD81E` の鍵と同じく更新する予定ですが，その前に予告の上で鍵の失効を行う可能性があります．

### 既に失効している鍵について

以下のキーペアはしばらく使用されておらず，使用する場合もないので**失効日時の延長は行いません．**

- マスターキー
  KID: `94FBB0880BC97D4E`
  FP: `AEF0 5495 AC12 23CB 3904  C4C9 94FB B088 0BC9 7D4E`
1. サブキー ( 署名兼認証用 )
     KID: `0BEBEA47F6DE1EE3`
  
2. サブキー ( 暗号化/復号用 )
     KID: `D7CE63F383C4B204`

## 内容の署名について

https://github.com/loxygenK/pgpkey-notices/tree/main/2020-8-17_operation_notice にこの文章の署名がアップロードしてあります:

- (リポジトリルート)
  - `2020-8-17_operation_notice`
    - `ja`
      - `operation_notice_ja.md`
      - `operation_notice_ja_signed_newkey_61CCD81E.asc`
      - `operation_notice_ja_signed_oldkey_rev_6E1EB2D9.asc`
      - `operation_notice_ja_signed_oldkey_8388C939.asc`
    - `en`
      - `operation_notice_en.md`
      - `operation_notice_en_signed_newkey_61CCD81E.asc`
      - `operation_notice_en_signed_oldkey_rev_6E1EB2D9.asc`
      - `operation_notice_en_signed_oldkey_8388C939.asc`
  - ...

## その他

### 鍵のインポートについて

KID `61CCD81E` の鍵は，`keys.openpgp.org` サーバに登録してあります．以下のコマンドでインポートできます:

```sh
gpg --keyserver=keys.openpgp.org --recv-keys '1899551DD3D1B9DB355AEF244698AEC661CCD81E'
```

#### 鍵の署名の検証

KID `61CCD81E` のマスターキーは KID `8388C939` の鍵 (及び KID `61CCD81E` の鍵による自己署名) によって署名されています．以下のコマンドで署名を検証できます:

```sh
gpg --check-sigs '1899551DD3D1B9DB355AEF244698AEC661CCD81E'
```

KID `8388C939` の鍵を持っていないが鍵が正常にインポートされているかを確認したい場合，以下のコマンドを使用してフィンガープリントが正しいかを確認できます:

```sh
gpg --fingerprint '1899551DD3D1B9DB355AEF244698AEC661CCD81E'
```

#### 署名のお願い

KID `61CCD81E` の鍵の正当性を認めてくださった場合，鍵を署名していただけると大変幸いです! 以下のコマンドで署名を行えます:

```sh
gpg --sign-key '1899551DD3D1B9DB355AEF244698AEC661CCD81E'
```

署名後，以下のいずれかの方法で私に署名を送信していただけると幸いです :pray:

- Keybase: [`loxygenK`](https://keybase.io/loxygenK)
- Twitter: [`@loxygen_k`](https://twitter.com/loxygen_k)
- E-Mail: me [local-part と domain の間の区切りの記号] loxygen.dev



お手数をおかけしますが，どうかよろしくおねがいします．

2021, loxygenK ( a.k.a. flisan )