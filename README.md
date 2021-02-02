# CUIT ICEC Wiki

## url

[CUIT ICEC Wiki - CUIT ICEC Wiki (gitee.io)](https://cuit_icec.gitee.io/icec_wiki/)

## 起步

运行环境：python 3.6+

```sh
# 配置运行环境，推荐使用 virtualenv
pip install -r requirements.txt -i https://pypi.tuna.tsinghua.edu.cn/simple
# 启动本地服务器，可在修改文章的同时实时查看渲染效果，服务器会自动重载
mkdocs serve
```

#### 可能出现的问题：

1.如果安装出现以下提示，需要将对应的script文件夹路径加入环境变量中

```
 WARNING: The script pygmentize.exe is installed in 'C:\Users\Administrator.VZMRW9ETL45BX39\AppData\Local\Packages\PythonSoftwareFoundation.Python.3.9_qbz5n2kfra8p0\LocalCache\local-packages\Python39\Scripts' which is not on PATH.
```



## 新增文章

将要添加至 Wiki 的 Markdown 文件保存至 `docs` 下的文件夹中，然后修改 `mkdocs.yml` 中的 `nav` 属性，将文章的标题及路径添加至 Wiki 目录，如：

```ymal
nav:
  - 简介:
    - 首页: index.md
    - 关于: about.md
  - 硬件:
    - 电路分析: hardware/circuit_analysis.md
  - 软件:
    - C 语言: software/c_language.md
```