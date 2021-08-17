# Notice about operating of PGP Keys hosted by loxygenK

## Word definitions in this document

- **KID**: Keyid
- **FP**: Fingerprint
- **Key**: PGP Key

## Summary

The keys and the key pairs I currently operating will be operated as follows:

| KID of the master key of the key pair | Operation Policy                                             |
| ------------------------------------- | ------------------------------------------------------------ |
| **`4698AEC661CCD81E`**                | This key is used mainly.                                     |
| **`DA5BE9A08388C939`**                | **The sub key was expired, but its expiration date has been postponed to 01/04/2023 (UTC).**<br />**The master key's expiration date is set to 01/04/2023 (UTC) too, and they will be updated as the same as the key whose KID is `61CCD81E`**. |
| `FEB0F89E6E1EB2D9`                    | **This key will be revoked due to expiration in 2021/09/25 (JST, UTC+9).** |
| `94FBB0880BC97D4E`                    | This key is already revoked, however I'm not going to postpone expiration date. |

## Content

### Changing primary key

By setting up Yubikey to use new key ( KID: `4698AEC661CCD81E` ), the risk of leaking the private key has been reduced. Due to this, I've decided to change the key pairs mainly used. Also, I operated several key pairs without any reason, and I felt problems in terms of cost and safety, so I decided to use only one key pairs.

I had used following key pairs:

- Master key
  KID: `DA5BE9A08388C939`
  FP: `A244 6E2B F1A7 AC90 28F1  71A3 DA5B E9A0 8388 C939`
  1. Sub key (Signing and Authentication)
     KID: `5C101C888CCB1194`
  2. Sub key (Encryption/Decryption)
     KID: `9CE3B37FB3509E8A`

- Master key
  KID: `94FBB0880BC97D4E`
  FP: `AEF0 5495 AC12 23CB 3904  C4C9 94FB B088 0BC9 7D4E`
  1. Sub key ( Signing and Authentication )
     KID: `0BEBEA47F6DE1EE3`
  2. Sub key ( Encryption/Decryption )
     KID: `D7CE63F383C4B204`

- Master key
  KID: `FEB0F89E6E1EB2D9`
  FP: `56C5 EC0D 2245 3CE5 D6C7  FFA4 FEB0 F89E 6E1E B2D9`

**I will use the following key pairs mainly:**

- Master key
  KID: `4698AEC661CCD81E`
  FP: `1899 551D D3D1 B9DB 355A  EF24 4698 AEC6 61CC D81E` )
  1. Sub key ( Signing )
     KID: `3573FF548427FF69`
  2. Sub key ( Authentication )
     KID: `69CACB625254BDD1`
  3. Sub key (Encryption/Decryption)
     KID: `871A5B6C051C3CA9`

### Plan for revoking keys

The keys I've used until now have problems in the terms of safety due to the operating method. Furthermore, because of the change I declared in the previous section, the following key will be not used as primary keys anymore.

**The following key will be revoked in 25/09/2021 ( JST, UTC+9 ) due to expiration.**

- Master key
  KID: `FEB0F89E6E1EB2D9`
  FP: `56C5 EC0D 2245 3CE5 D6C7  FFA4 FEB0 F89E 6E1E B2D9`

### Adjusting expiration date of the key

**The sub key in the following key pair was already expired**, however **I postponed the expiration date to 01/04/2023 ( UTC ).** Also, **I postponed the expiration date of the master key to 01/04/2023 ( UTC ) too.**

- Master key
  KID: `DA5BE9A08388C939`
  FP: `A244 6E2B F1A7 AC90 28F1  71A3 DA5B E9A0 8388 C939`

  1. Sub key ( Signing and Authentication )
     KID: `5C101C888CCB1194`

  2. Sub key ( Encryption/Decryption )
     KID: `9CE3B37FB3509E8A`

This expiration dates will be updates as the same as the key whose KID is `61CCD81E`, however the key may be revoked with notice.

### The key which is already expired

The following key pair is not used for a long time, and I have no plan to use one, so **I'm not going to postpone following key's expiration date.**

- Master key
  KID: `94FBB0880BC97D4E`
  FP: `AEF0 5495 AC12 23CB 3904  C4C9 94FB B088 0BC9 7D4E`
1. Sub key ( Signing and Authentication )
     KID: `0BEBEA47F6DE1EE3`
  
2. Sub key ( Encryption/Decryption )
     KID: `D7CE63F383C4B204`

## The signature of this document

The signature of this document is uploaded at https://github.com/loxygenK/pgpkey-notices/tree/main/2020-8-17_operation_notice:

- (The root of the repository)
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

## Others

### Importing the key

The key whose KID is `61CCD18E` is registered at `keys.openpgp.org`. You can import the key using following command:

```sh
gpg --keyserver=keys.openpgp.org --recv-keys '1899551DD3D1B9DB355AEF244698AEC661CCD81E'
```

#### Validating the signature of key

The master key of the key whose KID is `61CCD81E` is signed by the key whose KID is `8388C939` ( and self-signing by the key whose KID is `61CCD81E` ). You can validate the signature if you have the key whose ID is `8388C939`:

```sh
gpg --check-sigs '1899551DD3D1B9DB355AEF244698AEC661CCD81E'
```

If you do not have the key whose KID is `8388C939`, and want to make sure the key is imported correctly, you can check the fingerprint against the key whose KID is `61CCD81E` using the following command:

```sh
gpg --fingerprint '1899551DD3D1B9DB355AEF244698AEC661CCD81E'
```

#### Request regarding signing key

If you acknowledge the validity of the key whose KID is `61CCD81E`, I really appreciate if you sign the key! You can sign by executing following command: 

```sh
gpg --sign-key '1899551DD3D1B9DB355AEF244698AEC661CCD81E'
```

After you signed the key, I would be very grateful if you send the signature using the following method:

- Keybase: [`loxygenK`](https://keybase.io/loxygenK)
- Twitter: [`@loxygen_k`](https://twitter.com/loxygen_k)
- E-Mail: me [A character separating local-part and domain] loxygen.dev



Sorry for inconvenience, and thank you for your understanding.

2021, loxygenK ( a.k.a. flisan )