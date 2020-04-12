<!--
 * @Author: Devin Wang
 * @Date: 2020-04-11 08:49:37
 * @LastEditors: Devin Wang
 * @LastEditTime: 2020-04-12 18:23:37
>
 -->
**写在前面**
KeyChain 属于 Security 框架，主要用于存储少量的数据。

**参考文章**
1. https://blog.csdn.net/qq_30357519/article/details/85051107
2. https://developer.apple.com/documentation/security?language=objc
3. https://developer.apple.com/documentation/security/keychain_services?language=objc
4. https://developer.apple.com/documentation/security/keychain_services/keychain_items/using_the_keychain_to_manage_user_secrets?language=objc
5. https://www.jianshu.com/p/5825fbccef18
6. https://blog.csdn.net/weixin_33910137/article/details/91374812

**使用场景**
1. 存储密码
2. 存储私钥
3. 存储证书

**第三方库**
   1. [SAMKeychain](https://github.com/soffes/SAMKeychain)
   2. [UICKeyChainStore](https://github.com/kishikawakatsumi/UICKeyChainStore)

**问答环节**
 >问题1：返回 errSecInteractionNotAllowed -25308

>答案：kSecAttrAccessible 字段控制是否可以在锁屏的时候使用KeyChain，这个真的很意外！！！[Reference Accessible](https://developer.apple.com/documentation/security/keychain_services/keychain_items/restricting_keychain_item_accessibility?language=objc)

    [privateKey setObject:(__bridge id) kSecAttrAccessibleAfterFirstUnlock forKey:(__bridge id)kSecAttrAccessible];
    

**过程感悟**
正确理解返回错误的意义，去方法定义的地方看错误码和对应的设置项有没有什么关联，如问答环节的 "问题1" 