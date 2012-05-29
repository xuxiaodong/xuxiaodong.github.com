---
layout: post
title: 修复 Debian 6 系统区域错误
date: 2012-05-29 23:30
post-link:
---

在 Debian 6 执行 aptitude upgrade 将系统升级后，出现了以下区域错误：

    perl: warning: Setting locale failed.
    perl: warning: Please check that your locale settings:
            LANGUAGE = "en_US:en_GB:en",
            LC_ALL = (unset),
            LANG = "en"
        are supported and installed on your system.
    perl: warning: Falling back to the standard locale ("C").
    locale: Cannot set LC_CTYPE to default locale: No such file or directory
    locale: Cannot set LC_MESSAGES to default locale: No such file or directory
    locale: Cannot set LC_ALL to default locale: No such file or directory

解决方法为：

    # aptitude remove locales
    # aptitude install locales
    # dpkg-reconfigure locales
