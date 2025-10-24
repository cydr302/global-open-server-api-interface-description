#### Request mode:

- POST

#### Request header:

|Parameter name|Required|Type|Illustration|
|:----    |:---|:----- |-----   |
|Content-Type |Yes  |string |Request type： application/json   |
|sign |Yes  |string | Request content signature    |


#### Signature rules:
- Generation rule of sign field in HTTP request header:
```
Openid is the encrypted content,The first 13 bytes of the secret and the last three bits of the time stamp (MS) are spliced into the encryption key (16 bits in total),The encryption method is AES.
```

|Parameter name|Type|Illustration|
|:-----  |:-----|-----                           |
|openId |String   |The communication ID assigned by the open platform can be viewed in the merchant's background.  |
|secret |String   |The communication key distributed by the open platform can be viewed or reset in the merchant's background.If lost or leaked, please reset the key in the merchant's background in time. |

- Encryption method demo(Java):

```java

import javax.crypto.Cipher;
import javax.crypto.spec.SecretKeySpec;
import java.nio.charset.StandardCharsets;
import java.security.Key;
import java.util.Base64;

public class Sign {

    public static String encode(String text, String key) {
        try {
            Key keySpec = new SecretKeySpec(key.getBytes(), "AES");
            Cipher cipher = Cipher.getInstance("AES/ECB/PKCS5Padding");
            cipher.init(Cipher.ENCRYPT_MODE, keySpec);
            return java.util.Base64.getEncoder().encodeToString(cipher.doFinal(text.getBytes(StandardCharsets.UTF_8)));
        } catch (Exception e) {
            e.printStackTrace();
        }
        return null;
    }

    public static void main(String[] args) {
        String openId = "aaaaaaaaaaaaaaaa";
        String secret = "bbbbbbbbbbbbbbbb";
        long time = System.currentTimeMillis();

        System.out.println("time:" + time);

        String encode = encode(openId, secret.substring(0, 13) + time % 1000);

        System.out.println("encode:" + encode);
    }
}

```
- Encryption test：

If openid is aaaaaaaaaaaaaaaa，secret is bbbbbbbbbbbbbbbb，time stamp is 1613633983928，
and the splicing encryption key is bbbbbbbbbbbbb928
the sign after encryption is:
```
036ytW2zWyI0V6JqEhCDrrH9YiW31PkQLodR694kwTs=
```