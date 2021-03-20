
# 如何在 phpstrom 配置快速代码格式化



## 步骤一

使用 `composer global require fabpot/php-cs-fixer` 下载 `php-cs-fixer`



## 步骤二



使用 `which php-cs-fixer` 找到 `php-cs-fixer` 路径


## 步骤三



在 `phpstrom` 设置内找到 `external Tools`

![image-20210320234817073](1.png)



## 步骤四

添加格式化脚本

![image-20210320235612717](2.png)



## 步骤五



![image-20210320235920238](3.jpg)



参数说明：

name ： 扩展名称（可随意给）

 program: 填写   `php-cs-fixer` 路径

Arguments: `fix --config=$ProjectFileDir$/.php_cs "$FileDir$/$FileName$"`

Working directory: `$ProjectFileDir$`



## 步骤六

配置快速格式化快捷键

在 `Keymap` 内找到自己的扩展，并且设置快捷键，接下来就可以愉快的使用快捷键格式化当前的代码文件了

![image-20210321000425415](4.png)









## .php_cs 文件

> 项目格式化文件可参考以下文件，自行调整

```php
<?php
return PhpCsFixer\Config::create()
    ->setRiskyAllowed(true)
    ->setRules([
        '@PSR2' => true,
        '@Symfony' => true,
        '@DoctrineAnnotation' => true,
        '@PhpCsFixer' => true,
        'header_comment' => [
            'commentType' => 'PHPDoc',
            'header' => $header,
            'separate' => 'none',
            'location' => 'after_declare_strict',
        ],
        'array_syntax' => [
            'syntax' => 'short'
        ],
        'list_syntax' => [
            'syntax' => 'short'
        ],
        'concat_space' => [
            'spacing' => 'one'
        ],
        'blank_line_before_statement' => [
            'statements' => [
                'declare',
            ],
        ],
        'general_phpdoc_annotation_remove' => [
            'annotations' => [
                'author'
            ],
        ],
        'ordered_imports' => [
            'imports_order' => [
                'class', 'function', 'const',
            ],
            'sort_algorithm' => 'alpha',
        ],
        'single_line_comment_style' => [
            'comment_types' => [
            ],
        ],
        'yoda_style' => [
            'always_move_variable' => false,
            'equal' => false,
            'identical' => false,
        ],
        'phpdoc_align' => [
            'align' => 'left',
        ],
        'multiline_whitespace_before_semicolons' => [
            'strategy' => 'no_multi_line',
        ],
        'constant_case' => [
            'case' => 'lower',
        ],
        'class_attributes_separation' => true,
        'combine_consecutive_unsets' => true,
        'declare_strict_types' => true,
        'linebreak_after_opening_tag' => true,
        'lowercase_static_reference' => true,
        'no_useless_else' => true,
        'no_unused_imports' => true,
        'not_operator_with_successor_space' => true,
        'not_operator_with_space' => false,
        'ordered_class_elements' => true,
        'php_unit_strict' => false,
        'phpdoc_separation' => false,
        'single_quote' => true,
        'standardize_not_equals' => true,
        'multiline_comment_opening_closing' => true,
    ])
    ->setFinder(
        PhpCsFixer\Finder::create()
            ->exclude('public')
            ->exclude('runtime')
            ->exclude('vendor')
            ->in(__DIR__)
    )
    ->setUsingCache(false);

```

