# Twig 介绍

## 为什么需要View模板？

直接在HTML页面中嵌入代码的做法，虽然直接快捷，但不利于前后端分工合作，也不易维护，程序逻辑和视图（包括视图的渲染逻辑）耦合在一块，也不便于拓展和重用，相对于拼接字符串，可读性也更高。
相比之下，Twig这样的模板语言，将逻辑和视图完全分离，同时其语法支持HTML片段的组合复用，对错误的处理也更优雅，语法上亲前端，可以大大提高团队开发效率。

## Twig 简介

Twig的语言风格：  
```
{% extends "base.html" %}
{% block navigation %}
    <ul id="navigation">
    {% for item in navigation %}
        <li>
            <a href="{{ item.href }}">
                {% if item.level == 2 %}&nbsp;&nbsp;{% endif %}
                {{ item.caption|upper }}
            </a>
        </li>
    {% endfor %}
    </ul>
{% endblock navigation %}
```

* [如何引用Twig](http://twig.sensiolabs.org/doc/intro.html)
* [Twig基本语法](http://twig.sensiolabs.org/doc/templates.html)
* [Tags](http://twig.sensiolabs.org/doc/tags/index.html)
* [Filters](http://twig.sensiolabs.org/doc/filters/index.html)
* [Functions](http://twig.sensiolabs.org/doc/functions/index.html)
* [Tests](http://twig.sensiolabs.org/doc/tests/index.html)


Twig的详尽介绍可以参考：[Twig 官方文档](http://twig.sensiolabs.org/documentation)



## 拓展阅读

* [Twig官网](http://twig.sensiolabs.org/)