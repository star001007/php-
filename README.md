# 声明
本文为 [`PHP: The Right Way`](http://www.phptherightway.com/)的中文翻译。我们致力于创建PHP最优秀的实践指南，我会尽力保持同步更新。

# 欢迎
长久以来，网上大量陈旧、泛滥的资料使得我们的PHP新手误入歧途，传播着丑陋的实践和不安全的代码。`PHP之道[PHP：The Right Way]`就是为此而诞生，我们致力于提供迄今为止开发的最佳实践及开发准则。

这里没有唯一的标准。我们的目的就是给提前给新手提供一些指南，让开发多年的PHP们对于他们多年的选择做一个重新的思考。本文也不会告诉你具体使用哪儿个工具，而是给你多个选择，同时解释他们的区别和具体应用场景。

这个文档会一直保持更新，因为会有更多、更好的信息和资料出现。

### 翻译
已经翻译为好多语言，当然也有我们的汉语。
>* [官方英文](http://www.phptherightway.com/)
>* [简体中文](http://wulijun.github.io/php-the-right-way/)
>* [繁体中文](http://laravel-taiwan.github.io/php-the-right-way/)

### 期待您的贡献
来帮助我们，给新手提供最好的资源。关注我们的[githup官方账户](https://github.com/codeguy/php-the-right-way/tree/gh-pages)

### 告诉您周围的小伙伴
使用这些Banner图片，传播`PHP之道`，让新手发现它。注：[图片详情地址](http://www.phptherightway.com/banners.html)

# 开始
### 使用最新的PHP版本（5.6）
如果你开始用了PHP，从5.6开始吧。过去几年里，PHP增加了大量的特性，尽管5.2到5.6的版本不多，但是改进却很多。
> 备注： PHP版本的升级包含bug的修正、功能的完善、性能的提升、安全性能的提高。所以，我们强烈建议大家尽量升级到最新的版本，让我们的PHP走的更远，从升级版本开始。

### 使用内置的web服务器
PHP5.4开始，你可以不需要安装配置一个成熟的web服务器，比如Apache/Nginx。你可以在你的项目的跟目录使用如下令：
```
>php -S localhost:8000
```
>更多关于内置、命令行的web服务器，[点击这里](http://php.net/manual/en/features.commandline.webserver.php)

### Mac安装
>备注：苹果的系统OS X操作系统是基于Unix的，如果你使用Linux系统，同样使用

OS X开始预装PHP，不过他们的版本会落后点，最新的版本是5.5.9。
我们当然建议是5.6，下面是多种安装方式：

#### 通过Homebrew安装
>备注：仅适用于苹果系统

[Homebrew](http://brew.sh/)是苹果系统OS X的强大的包管理工具，可以帮助你很容易的安装PHP和其他的扩展。[Homebrew PHP](https://github.com/Homebrew/homebrew-php#installation)是一个很好的仓库来帮助你。

这样，你可以使用命令`brew install`来安装PHP5.3,PHP5.4,PHP5.5,PHP5.6，并且通过修改`PATH`环境变量，来很容易的进行切换。

#### 通过phpbrew安装
>备注：适用于所有linux系统和Mac系统，墙裂建议

[phpbrew](https://github.com/phpbrew/phpbrew)是一个安装和管理PHP多个版本的工具。如果多个应用需要不同的版本，那么它很有帮助。

#### 从源代码编译
如果您需要安装时配置更多的选项，可以自己编译它。苹果机的朋友得确保安装了`Xcode`或者`Command Line Tools for Xcode`。

#### 使用集成环境
上面的方法只是安装单独的PHP，并没有提供Apache、Nginx或者Sql服务器，集成环境如 [MAMP](http://www.mamp.info/en/downloads/) 和 [XAMPP](https://www.apachefriends.org/index.html)。它会集成安装了其他的软件，当然了简易安装的同时会有灵活性丧失的代价。

### Windows安装
>备注：新手建议使用集成环境`XAMPP`就行，经验丰富时，可以在unix环境下手工编译。

windows安装有多种方式，[下载安装](http://windows.php.net/)或者和通过`.msi`安装器。不过从PHP5.3.0开始，不再支持安装器。

如果你只是在本地环境下的学习，你可以使用PHP5.4以上的内置服务器，你不需要配置。如果你想使用集成环境包含了内置服务器和mysql等，那么使用集成环境如：[Web Platform Installer](http://www.microsoft.com/web/downloads/platform.aspx)、[Zend Server CE](http://www.zend.com/en/products/server-ce/), [XAMPP](https://www.apachefriends.org/index.html), [EasyPHP](http://www.easyphp.org/) 和 [WAMP](http://www.wampserver.com/en/)。注意这会在生存环境下会有所不同，若你的部署环境不是windows，而是unix操作系统时。


# 代码风格指南

PHP社区有大量的包、框架和组件，我们在应用开发中，很多时候会使用其中几个，那么统一的代码风格将对我们开发者来说很便利。

[框架开发组](http://www.php-fig.org/)倡议并提出了一些列的编码风格的提议。其中有PSR-0, PSR-1, PSR-2 和 PSR-4。这些建议已经被很多框架所采用，如： Laravel, Phalcon, Symfony2, Drupal, Zend, CakePHP, phpBB, AWS SDK, FuelPHP, Lithium等等。

理想情况是，大家都使用统一的编码风格，如PSR，或者 PEAE 和 Zend的规范，这样我们在相互学习和使用时将毫无障碍，非常便捷。下面是我们推荐的一些规范：
>* PSR-0，[英文版](https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-0.md)，[中文版](https://github.com/PizzaLiu/PHP-FIG/blob/master/PSR-0-cn.md)
>* PSR-1，[英文版](https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-1-basic-coding-standard.md)，[中文版](https://github.com/PizzaLiu/PHP-FIG/blob/master/PSR-1-basic-coding-standard-cn.md)
>* PSR-2，[英文版](https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-2-coding-style-guide.md)，[中文版](https://github.com/PizzaLiu/PHP-FIG/blob/master/PSR-2-coding-style-guide-cn.md)
>* PSR-4，[英文版](https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-4-autoloader.md)，[中文版](https://github.com/PizzaLiu/PHP-FIG/blob/master/PSR-4-autoloader-cn.md)
>* PEAR，[英文版](http://pear.php.net/manual/en/standards.php)
>* Zend
>* Symfony，[英文版](http://symfony.com/doc/current/contributing/code/standards.html)

你可以使用`[PHP CodeSniffer](http://pear.php.net/package/PHP_CodeSniffer/)`来检测上述的规范，Sublime Text2也有专门的插件来检测。

你可以使用两个工具来自动校准你的代码风格。一个是`[PHP Coding Standards Fixer](http://cs.sensiolabs.org/)`，稳定可靠，被symfony和magento所采用，但是比较慢。另一个是`[php.tools](https://github.com/dericofilho/php.tools)`，sumlime-phpfmt编辑器的插件。

英语当然是最好的语法定义、代码使用的语言。注释可以根据你的团队来使用熟悉的语言。

# 语法高亮

### 编程范式

#### 面向对象编程

#### 函数式编程

#### 元编程

# 命名空间

# PHP标准类库

# 命令行接口

# Xdebug

# 依赖管理

### Composer和包列表

#### 如何安装Composer

##### windows上安装composer 

#### 如果手工安装Composer

#### 如何定义和安装依赖

#### 更新依赖

#### 更新通知

#### 检查依赖的安全问题

#### 使用Composer处理全局依赖

### PEAR

#### 如何安装PEAR

#### 如果通过pear安装包

#### 使用composer处理pear依赖

# 代码实践

### 基础

### 日期和时间

### 设计模式

### 使用UTF-8

# 依赖注入

### 基本概念

### 复杂问题

#### 控制反转

#### 依赖注入原理

### 容器

### 扩展阅读


# 数据库

### mysql扩展

### PDO扩展

### 与数据库交互

### 抽象层

# 模板








