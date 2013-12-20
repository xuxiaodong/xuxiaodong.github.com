---
layout: post
title: 修复 pycrypto AttributeError
date: 2013-12-20 10:05
post-link:
---

在将 Ansible 升级到 1.4.2 时，其依赖模块 pycrpyto 也进行了
更新，执行 `ansible` 报如下错误：

    Traceback (most recent call last):
    File "/usr/bin/ansible", line 24, in <module>
        from ansible.runner import Runner
    File "/usr/lib/python2.6/site-packages/ansible/runner/__init__.py", line 53, in <module>
        from Crypto.Random import atfork
    File "/usr/lib64/python2.6/site-packages/Crypto/Random/__init__.py", line 29, in <module>
        from Crypto.Random import _UserFriendlyRNG
    File "/usr/lib64/python2.6/site-packages/Crypto/Random/_UserFriendlyRNG.py", line 38, in <module>
        from Crypto.Random.Fortuna import FortunaAccumulator
    File "/usr/lib64/python2.6/site-packages/Crypto/Random/Fortuna/FortunaAccumulator.py", line 39, in <module>
        import FortunaGenerator
    File "/usr/lib64/python2.6/site-packages/Crypto/Random/Fortuna/FortunaGenerator.py", line 34, in <module>
        from Crypto.Util.number import ceil_shift, exact_log2, exact_div
    File "/usr/lib64/python2.6/site-packages/Crypto/Util/number.py", line 56, in <module>
        if _fastmath is not None and not _fastmath.HAVE_DECL_MPZ_POWM_SEC:
    AttributeError: 'module' object has no attribute 'HAVE_DECL_MPZ_POWM_SEC'

打开 `/usr/lib64/python2.6/site-packages/Crypto/Util/number.py` 文件，可以
看到 56 行上的注释说明，要求 libgmp 为 v5 以上版本。而系统现有版本为
4.1.4，把 56 和 57 行暂时注释掉，Ansible 执行正常。

不过，此方法只是临时加以解决，更好的方式是去将 libgmp
升级到符合要求的版本。
