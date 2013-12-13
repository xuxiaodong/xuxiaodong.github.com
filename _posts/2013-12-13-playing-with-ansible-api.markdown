---
layout: post
title: 玩玩 Ansible API
date: 2013-12-13 14:00
post-link: https://github.com/xuxiaodong/ansible-utils/blob/master/ansible-groups
---

如果了解一点 Python，我们还可以从 API 的角度来使用 Ansible。
这是我喜欢使用 Ansible 的另一个原因。

虽然 Ansible 提供的 `--list-hosts` 选项可以看到 inventory 中
的主机，但却无法看到具体的组别。因此，我写了一段小程序来列出
这些组名：

    from ansible.inventory import Inventory

    def get_groups():
        i = Inventory()
        groups = i.list_groups()
        return '\n'.join(groups)

    if __name__ == '__main__':
        print(get_groups())

如果保存为 ansible-groups，执行

    ./ansible-groups

就会输出类似下面的结果：

    all
    test
    ungrouped
