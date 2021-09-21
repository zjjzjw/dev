![20210918154942_7963c40f2cd7f4db1c91549ecc4c0fd6.png](https://zjj-1307432767.cos.ap-shanghai.myqcloud.com/20210918154942_7963c40f2cd7f4db1c91549ecc4c0fd6.png?q-sign-algorithm=sha1&q-ak=AKIDvgBQO5VeWZMs74l8G7gyzjCPL1RbU5PU&q-sign-time=1631951382;1663487382&q-key-time=1631951382;1663487382&q-header-list=&q-url-param-list=&q-signature=522c781228e501a4a6dcc94985f8e26522f092ab)


1. 前言
1.1. 一般信息[重要必读]
此编码风格指南主要基于 Google Python Style Guide [中译版]，结合百度python使用习惯和实际开发情况制定。

这份文档存在的意义是让大家写出统一风格的代码，让百度的模块可维护性和可读性更好；

文档内容可能会与您的喜好冲突， 请尽量用包容的心态来接受; 不合理之处， 请反馈给py-styleguide@baidu.com

1.2. 如何使用本编程规范
1.2.1. 本规范的层次结构
本规范可分为三大部分，分别对Python语法、风格、编程实践作出规定与建议。

每一部分有若干专题，每一专题下有若干条目。

条目是规范的基本组成部分，每一条目由规定、定义、解释、示例、参考等项组成。

1.2.2. 条目的级别和编号
本规范的条目分两个级别:

[强制]：要求所有程序必须遵守，不得违反
[建议]：建议遵守，除非确有特殊情况
1.3. The Zen of Python
建议每位python开发人员细读”python之禅”，理解规范背后的思想

"""
The Zen of Python

 Beautiful is better than ugly.
 Explicit is better than implicit.
 Simple is better than complex.
 Complex is better than complicated.
 Flat is better than nested.
 Sparse is better than dense.
 Readability counts.
 Special cases aren't special enough to break the rules.
 Although practicality beats purity.
 Errors should never pass silently.
 Unless explicitly silenced.
 In the face of ambiguity, refuse the temptation to guess.
 There should be one-- and preferably only one --obvious way to do it.
 Although that way may not be obvious at first unless you're Dutch.
 Now is better than never.
 Although never is often better than |right| now.
 If the implementation is hard to explain, it's a bad idea.
 If the implementation is easy to explain, it may be a good idea.
 Namespaces are one honking great idea -- let's do more of those!

-- by Tim Peters
"""
2. 语言规范
2.1. import
·[建议] 禁止使用from xxx import yyy语法直接导入类或函数(即yyy只能是module或package，不能是类或函数)。

解释

避免冲突。调用关系简单明了，x.obj表示obj对象定义在模块x中。

示例


![20210918155150_9dfcc75383a4efec8d9cbcf6c7862d0b.png](https://zjj-1307432767.cos.ap-shanghai.myqcloud.com/20210918155150_9dfcc75383a4efec8d9cbcf6c7862d0b.png?q-sign-algorithm=sha1&q-ak=AKIDvgBQO5VeWZMs74l8G7gyzjCPL1RbU5PU&q-sign-time=1631951510;1663487510&q-key-time=1631951510;1663487510&q-header-list=&q-url-param-list=&q-signature=bfaf96ad39d15a0375d33efce00701a089e2b9ec)



![20210918155215_57afda297109ceeeff8a1826c841a4d2.png](https://zjj-1307432767.cos.ap-shanghai.myqcloud.com/20210918155215_57afda297109ceeeff8a1826c841a4d2.png?q-sign-algorithm=sha1&q-ak=AKIDvgBQO5VeWZMs74l8G7gyzjCPL1RbU5PU&q-sign-time=1631951535;1663487535&q-key-time=1631951535;1663487535&q-header-list=&q-url-param-list=&q-signature=1603b0efd06d93b0d25f8b1af78294aa93a4e1db)



![20210918155252_fca9e9e298d75be06c01d021a4c90c73.png](https://zjj-1307432767.cos.ap-shanghai.myqcloud.com/20210918155252_fca9e9e298d75be06c01d021a4c90c73.png?q-sign-algorithm=sha1&q-ak=AKIDvgBQO5VeWZMs74l8G7gyzjCPL1RbU5PU&q-sign-time=1631951571;1663487571&q-key-time=1631951571;1663487571&q-header-list=&q-url-param-list=&q-signature=4786c26079b45a815aaafb9fc9d306aae83b3e3e)


![20210918155315_8bc8a23c842e8a5c4e49d4015dd9d028.png](https://zjj-1307432767.cos.ap-shanghai.myqcloud.com/20210918155315_8bc8a23c842e8a5c4e49d4015dd9d028.png?q-sign-algorithm=sha1&q-ak=AKIDvgBQO5VeWZMs74l8G7gyzjCPL1RbU5PU&q-sign-time=1631951595;1663487595&q-key-time=1631951595;1663487595&q-header-list=&q-url-param-list=&q-signature=ba6aad4c83f8691c3a35fa582f155938cddcab5d)


![20210918155403_4346511317b64ee3d5786f6ea2ba41c9.png](https://zjj-1307432767.cos.ap-shanghai.myqcloud.com/20210918155403_4346511317b64ee3d5786f6ea2ba41c9.png?q-sign-algorithm=sha1&q-ak=AKIDvgBQO5VeWZMs74l8G7gyzjCPL1RbU5PU&q-sign-time=1631951643;1663487643&q-key-time=1631951643;1663487643&q-header-list=&q-url-param-list=&q-signature=81fe5152f897857b826075ba8c35e56b5fbd46d5)

![20210918155428_a80beb715812a8d74fb2a74f89835088.png](https://zjj-1307432767.cos.ap-shanghai.myqcloud.com/20210918155428_a80beb715812a8d74fb2a74f89835088.png?q-sign-algorithm=sha1&q-ak=AKIDvgBQO5VeWZMs74l8G7gyzjCPL1RbU5PU&q-sign-time=1631951668;1663487668&q-key-time=1631951668;1663487668&q-header-list=&q-url-param-list=&q-signature=181d5aefccf872789550178a1584426d029999be)

![20210918161817_96687319fc071fa4e704bc3e4f48d680.png](https://zjj-1307432767.cos.ap-shanghai.myqcloud.com/20210918161817_96687319fc071fa4e704bc3e4f48d680.png?q-sign-algorithm=sha1&q-ak=AKIDvgBQO5VeWZMs74l8G7gyzjCPL1RbU5PU&q-sign-time=1631953097;1663489097&q-key-time=1631953097;1663489097&q-header-list=&q-url-param-list=&q-signature=e82d57c647b4aced3c3ab245aa84170928ea5643)


![20210918161835_46abaced31f37d9dd5f6f15bc194a36d.png](https://zjj-1307432767.cos.ap-shanghai.myqcloud.com/20210918161835_46abaced31f37d9dd5f6f15bc194a36d.png?q-sign-algorithm=sha1&q-ak=AKIDvgBQO5VeWZMs74l8G7gyzjCPL1RbU5PU&q-sign-time=1631953114;1663489114&q-key-time=1631953114;1663489114&q-header-list=&q-url-param-list=&q-signature=c2b84cc8fa390fa8cede61b4f06e1197597c1ce0)

![20210918161851_ddb263af49d9f4612e31999dd662f426.png](https://zjj-1307432767.cos.ap-shanghai.myqcloud.com/20210918161851_ddb263af49d9f4612e31999dd662f426.png?q-sign-algorithm=sha1&q-ak=AKIDvgBQO5VeWZMs74l8G7gyzjCPL1RbU5PU&q-sign-time=1631953131;1663489131&q-key-time=1631953131;1663489131&q-header-list=&q-url-param-list=&q-signature=63d15f938cc18ecc8d4a36bbfeca879c1dfb259d)

![20210918162044_42b32751ecaa2de2bacb8b390d8f9c2f.png](https://zjj-1307432767.cos.ap-shanghai.myqcloud.com/20210918162044_42b32751ecaa2de2bacb8b390d8f9c2f.png?q-sign-algorithm=sha1&q-ak=AKIDvgBQO5VeWZMs74l8G7gyzjCPL1RbU5PU&q-sign-time=1631953244;1663489244&q-key-time=1631953244;1663489244&q-header-list=&q-url-param-list=&q-signature=4b99cef40d33f60994a163ecee831153d8a45e07)

![20210918162112_df30f32c0427a816fffbf1f8c566e8ef.png](https://zjj-1307432767.cos.ap-shanghai.myqcloud.com/20210918162112_df30f32c0427a816fffbf1f8c566e8ef.png?q-sign-algorithm=sha1&q-ak=AKIDvgBQO5VeWZMs74l8G7gyzjCPL1RbU5PU&q-sign-time=1631953271;1663489271&q-key-time=1631953271;1663489271&q-header-list=&q-url-param-list=&q-signature=76f9f9f5162beaba6592921d795598d8c518028b)


![20210918162140_938516bf28b68ceb25de02731c5d043e.png](https://zjj-1307432767.cos.ap-shanghai.myqcloud.com/20210918162140_938516bf28b68ceb25de02731c5d043e.png?q-sign-algorithm=sha1&q-ak=AKIDvgBQO5VeWZMs74l8G7gyzjCPL1RbU5PU&q-sign-time=1631953300;1663489300&q-key-time=1631953300;1663489300&q-header-list=&q-url-param-list=&q-signature=64cb0c4e0c9b69fc9a2dc755e31be8874a2094af)

![20210918162208_2946fe97dd19037d0a20884db8eeda64.png](https://zjj-1307432767.cos.ap-shanghai.myqcloud.com/20210918162208_2946fe97dd19037d0a20884db8eeda64.png?q-sign-algorithm=sha1&q-ak=AKIDvgBQO5VeWZMs74l8G7gyzjCPL1RbU5PU&q-sign-time=1631953327;1663489327&q-key-time=1631953327;1663489327&q-header-list=&q-url-param-list=&q-signature=4c11a67a6245b54d6f519fd9217ec7d37f9bb5d7)


![20210918162228_b54c023edef6ffda4e134bcc1aed0a32.png](https://zjj-1307432767.cos.ap-shanghai.myqcloud.com/20210918162228_b54c023edef6ffda4e134bcc1aed0a32.png?q-sign-algorithm=sha1&q-ak=AKIDvgBQO5VeWZMs74l8G7gyzjCPL1RbU5PU&q-sign-time=1631953348;1663489348&q-key-time=1631953348;1663489348&q-header-list=&q-url-param-list=&q-signature=6c3ea6d47c683873232a87e83fc5d6fd1c3a873a)


![20210918162307_a028341c851b652eb457d283f9a5b697.png](https://zjj-1307432767.cos.ap-shanghai.myqcloud.com/20210918162307_a028341c851b652eb457d283f9a5b697.png?q-sign-algorithm=sha1&q-ak=AKIDvgBQO5VeWZMs74l8G7gyzjCPL1RbU5PU&q-sign-time=1631953387;1663489387&q-key-time=1631953387;1663489387&q-header-list=&q-url-param-list=&q-signature=6e4a3eed043b0541cad4411ce87a57c7051ab66d)


![20210918162403_de0b3ffe6d7eeb19bea26ad43a6b3324.png](https://zjj-1307432767.cos.ap-shanghai.myqcloud.com/20210918162403_de0b3ffe6d7eeb19bea26ad43a6b3324.png?q-sign-algorithm=sha1&q-ak=AKIDvgBQO5VeWZMs74l8G7gyzjCPL1RbU5PU&q-sign-time=1631953443;1663489443&q-key-time=1631953443;1663489443&q-header-list=&q-url-param-list=&q-signature=9a6e696d1f903bc64f7afeace01a328abf0273a6)

![20210918162427_503bf6c018259553e135a0eb27ba6c4f.png](https://zjj-1307432767.cos.ap-shanghai.myqcloud.com/20210918162427_503bf6c018259553e135a0eb27ba6c4f.png?q-sign-algorithm=sha1&q-ak=AKIDvgBQO5VeWZMs74l8G7gyzjCPL1RbU5PU&q-sign-time=1631953467;1663489467&q-key-time=1631953467;1663489467&q-header-list=&q-url-param-list=&q-signature=033175ce8a05eb3222602594d2c07a33ab800fc9)



![20210918162459_aa60203f536991da8e4b502fcd1ebf3a.png](https://zjj-1307432767.cos.ap-shanghai.myqcloud.com/20210918162459_aa60203f536991da8e4b502fcd1ebf3a.png?q-sign-algorithm=sha1&q-ak=AKIDvgBQO5VeWZMs74l8G7gyzjCPL1RbU5PU&q-sign-time=1631953499;1663489499&q-key-time=1631953499;1663489499&q-header-list=&q-url-param-list=&q-signature=0d5934164cfe0607e6d3e5c5596f38a2e0e7ce7e)


![20210918162543_5be2dbdf57b88e389cdbaee5d7d84787.png](https://zjj-1307432767.cos.ap-shanghai.myqcloud.com/20210918162543_5be2dbdf57b88e389cdbaee5d7d84787.png?q-sign-algorithm=sha1&q-ak=AKIDvgBQO5VeWZMs74l8G7gyzjCPL1RbU5PU&q-sign-time=1631953543;1663489543&q-key-time=1631953543;1663489543&q-header-list=&q-url-param-list=&q-signature=4b01fea4cd9228cd3d49e6d4fdda868d3277df49)


![20210918162558_2a387ed6096bc7badf8f7ad672f85861.png](https://zjj-1307432767.cos.ap-shanghai.myqcloud.com/20210918162558_2a387ed6096bc7badf8f7ad672f85861.png?q-sign-algorithm=sha1&q-ak=AKIDvgBQO5VeWZMs74l8G7gyzjCPL1RbU5PU&q-sign-time=1631953558;1663489558&q-key-time=1631953558;1663489558&q-header-list=&q-url-param-list=&q-signature=fe22ef21c9a930a4e3e6a40c5d8a22c64a2d06e6)


![20210918162632_db9f87bdd343b239bac511d9dd757e9d.png](https://zjj-1307432767.cos.ap-shanghai.myqcloud.com/20210918162632_db9f87bdd343b239bac511d9dd757e9d.png?q-sign-algorithm=sha1&q-ak=AKIDvgBQO5VeWZMs74l8G7gyzjCPL1RbU5PU&q-sign-time=1631953592;1663489592&q-key-time=1631953592;1663489592&q-header-list=&q-url-param-list=&q-signature=a86903f631b2aa76cd98f6807b51df3c6526d46d)


![20210918162704_f3d7e26949bacc49f17bea37b1423a0b.png](https://zjj-1307432767.cos.ap-shanghai.myqcloud.com/20210918162704_f3d7e26949bacc49f17bea37b1423a0b.png?q-sign-algorithm=sha1&q-ak=AKIDvgBQO5VeWZMs74l8G7gyzjCPL1RbU5PU&q-sign-time=1631953624;1663489624&q-key-time=1631953624;1663489624&q-header-list=&q-url-param-list=&q-signature=4f6d263bdea176637edc8774a002af13eadf8a60)

![20210918162729_85366f48bcdc868399a93d693dbf7c0c.png](https://zjj-1307432767.cos.ap-shanghai.myqcloud.com/20210918162729_85366f48bcdc868399a93d693dbf7c0c.png?q-sign-algorithm=sha1&q-ak=AKIDvgBQO5VeWZMs74l8G7gyzjCPL1RbU5PU&q-sign-time=1631953649;1663489649&q-key-time=1631953649;1663489649&q-header-list=&q-url-param-list=&q-signature=86d4add9efb5502ad21e10eac4a5bcdc8398eb61)

![20210918162822_de676b84ab0876a910eb76f2b9366374.png](https://zjj-1307432767.cos.ap-shanghai.myqcloud.com/20210918162822_de676b84ab0876a910eb76f2b9366374.png?q-sign-algorithm=sha1&q-ak=AKIDvgBQO5VeWZMs74l8G7gyzjCPL1RbU5PU&q-sign-time=1631953702;1663489702&q-key-time=1631953702;1663489702&q-header-list=&q-url-param-list=&q-signature=72bb09148c33ad3602837349785395210677f29f)


![20210918162902_e262f858a0738531d4fda4e338ee33d9.png](https://zjj-1307432767.cos.ap-shanghai.myqcloud.com/20210918162902_e262f858a0738531d4fda4e338ee33d9.png?q-sign-algorithm=sha1&q-ak=AKIDvgBQO5VeWZMs74l8G7gyzjCPL1RbU5PU&q-sign-time=1631953742;1663489742&q-key-time=1631953742;1663489742&q-header-list=&q-url-param-list=&q-signature=938e1a0927b94c66b595a71645f112b966aec38e)


![20210918162929_d057a084f4e0432967edd9f773b46b65.png](https://zjj-1307432767.cos.ap-shanghai.myqcloud.com/20210918162929_d057a084f4e0432967edd9f773b46b65.png?q-sign-algorithm=sha1&q-ak=AKIDvgBQO5VeWZMs74l8G7gyzjCPL1RbU5PU&q-sign-time=1631953769;1663489769&q-key-time=1631953769;1663489769&q-header-list=&q-url-param-list=&q-signature=75d98604f5eae2635b1cc4d39ebc9e4f10759ae0)

![20210918162954_dfe53c80aa3a2f0c4553492d753dfc2c.png](https://zjj-1307432767.cos.ap-shanghai.myqcloud.com/20210918162954_dfe53c80aa3a2f0c4553492d753dfc2c.png?q-sign-algorithm=sha1&q-ak=AKIDvgBQO5VeWZMs74l8G7gyzjCPL1RbU5PU&q-sign-time=1631953794;1663489794&q-key-time=1631953794;1663489794&q-header-list=&q-url-param-list=&q-signature=dd050dad98f28d23ce258b131a7b0210264d1c08)



![20210918165818_598bc4a2d019dc346fbc9a63b26fb29b.png](https://zjj-1307432767.cos.ap-shanghai.myqcloud.com/20210918165818_598bc4a2d019dc346fbc9a63b26fb29b.png?q-sign-algorithm=sha1&q-ak=AKIDvgBQO5VeWZMs74l8G7gyzjCPL1RbU5PU&q-sign-time=1631955498;1663491498&q-key-time=1631955498;1663491498&q-header-list=&q-url-param-list=&q-signature=e7ac3c3c10681ea6d0bca497bad0103b864f093b)

![20210918165845_823815226ef365bd73fc6894593286f8.png](https://zjj-1307432767.cos.ap-shanghai.myqcloud.com/20210918165845_823815226ef365bd73fc6894593286f8.png?q-sign-algorithm=sha1&q-ak=AKIDvgBQO5VeWZMs74l8G7gyzjCPL1RbU5PU&q-sign-time=1631955525;1663491525&q-key-time=1631955525;1663491525&q-header-list=&q-url-param-list=&q-signature=9298e4e56ed8265cf8a099da5b27d61b796e7109)



![20210918170719_66ea9b5b898dd675b839b5c86ced38f9.png](https://zjj-1307432767.cos.ap-shanghai.myqcloud.com/20210918170719_66ea9b5b898dd675b839b5c86ced38f9.png?q-sign-algorithm=sha1&q-ak=AKIDvgBQO5VeWZMs74l8G7gyzjCPL1RbU5PU&q-sign-time=1631956039;1663492039&q-key-time=1631956039;1663492039&q-header-list=&q-url-param-list=&q-signature=fa043fb4fe2be7d92608763fa37aad1db57aece8)

![20210918170739_1aa40176b6af9ca7f7aeac39ed1bacf0.png](https://zjj-1307432767.cos.ap-shanghai.myqcloud.com/20210918170739_1aa40176b6af9ca7f7aeac39ed1bacf0.png?q-sign-algorithm=sha1&q-ak=AKIDvgBQO5VeWZMs74l8G7gyzjCPL1RbU5PU&q-sign-time=1631956059;1663492059&q-key-time=1631956059;1663492059&q-header-list=&q-url-param-list=&q-signature=36863b78c47a90402421492ac2d09c594bdce876)

![20210918170757_dc6ac06b098bc719f646ef37fc0ffe45.png](https://zjj-1307432767.cos.ap-shanghai.myqcloud.com/20210918170757_dc6ac06b098bc719f646ef37fc0ffe45.png?q-sign-algorithm=sha1&q-ak=AKIDvgBQO5VeWZMs74l8G7gyzjCPL1RbU5PU&q-sign-time=1631956077;1663492077&q-key-time=1631956077;1663492077&q-header-list=&q-url-param-list=&q-signature=cdc29e27a04cdbc648d8b581404ec15a63b1daca)

![20210918170815_38fa667e2a1668f5ce9c6de27ff100e0.png](https://zjj-1307432767.cos.ap-shanghai.myqcloud.com/20210918170815_38fa667e2a1668f5ce9c6de27ff100e0.png?q-sign-algorithm=sha1&q-ak=AKIDvgBQO5VeWZMs74l8G7gyzjCPL1RbU5PU&q-sign-time=1631956095;1663492095&q-key-time=1631956095;1663492095&q-header-list=&q-url-param-list=&q-signature=70f42021922e4e09a5cd42de6be2e03105eb2d6d)

![20210918170842_0a49098ea37b3531aaada63d12a24913.png](https://zjj-1307432767.cos.ap-shanghai.myqcloud.com/20210918170842_0a49098ea37b3531aaada63d12a24913.png?q-sign-algorithm=sha1&q-ak=AKIDvgBQO5VeWZMs74l8G7gyzjCPL1RbU5PU&q-sign-time=1631956122;1663492122&q-key-time=1631956122;1663492122&q-header-list=&q-url-param-list=&q-signature=533db3b37c67a72c607f59ecdc8ededad347aac4)

![20210918170912_c2f721df21793ef41de507d90d299f48.png](https://zjj-1307432767.cos.ap-shanghai.myqcloud.com/20210918170912_c2f721df21793ef41de507d90d299f48.png?q-sign-algorithm=sha1&q-ak=AKIDvgBQO5VeWZMs74l8G7gyzjCPL1RbU5PU&q-sign-time=1631956152;1663492152&q-key-time=1631956152;1663492152&q-header-list=&q-url-param-list=&q-signature=6e5bcabf632d92b591344ac2e426ff1c04d198e2)


https://docs.python.org/2.7/library/logging.html






