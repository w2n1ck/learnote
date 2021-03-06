# 演示

> 查询最近暴力破解服务器密码的IP归属地

```shell
cat /var/log/secure | awk '/Failed/ {print $(NF-3)}' > ip_list.txt
```

然后查询

```shell
python ip_query.py -i ip_list.txt -o out.csv
```

就是利用淘宝IP地址查询API挨个把IP地址归属地查询一遍，结果放在`csv`文件中，`Excel`打开长这样

| ip             | count | country | isp  | area | region | city | county |
| -------------- | ----- | ------- | ---- | ---- | ------ | ---- | ------ |
| 114.112.69.50  | 11    | 中国      |      | 华北   | 北京市    | 北京市  |        |
| 1.25.202.50    | 5     | 中国      | 联通   | 华北   | 内蒙古自治区 | 包头市  |        |
| 66.161.209.154 | 5     | 美国      |      |      |        |      |        |
| 50.97.246.147  | 5     | 美国      |      |      |        |      |        |
| 38.69.193.39   | 5     | 美国      |      |      |        |      |        |
| 37.55.227.103  | 5     | 乌克兰     |      |      |        |      |        |
| 223.5.3.200    | 5     | 中国      | 阿里云  | 华东   | 浙江省    | 杭州市  |        |
| 218.248.42.131 | 5     | 印度      |      |      |        |      |        |
| 211.232.30.253 | 5     | 韩国      |      |      |        |      |        |
| 210.44.159.49  | 5     | 中国      | 教育网  | 华东   | 山东省    | 济南市  |        |
| 203.122.59.88  | 5     | 印度      |      |      |        |      |        |
| 202.97.194.167 | 5     | 中国      | 联通   | 东北   | 黑龙江省   | 哈尔滨市 |        |
| 202.103.36.43  | 5     | 中国      | 电信   | 华中   | 湖北省    | 武汉市  |        |
| 188.116.55.211 | 5     | 波兰      |      |      |        |      |        |
| 145.253.72.3   | 5     | 德国      |      |      |        |      |        |
| 134.255.243.11 | 5     | 德国      |      |      |        |      |        |
| 133.242.17.113 | 5     | 日本      |      |      |        |      |        |
| 122.72.120.109 | 5     | 中国      | 铁通   | 华东   | 上海市    | 上海市  |        |
| 118.244.14.49  | 5     | 中国      |      | 华北   | 北京市    | 北京市  |        |
| 66.248.201.2   | 5     | 美国      |      |      |        |      |        |

PS: 帮助信息

```shell
$ python ip_query.py -h
Query IP from taobao ip API
via <http://ip.taobao.com>
Usage:
    ip_query.py [-i=in] [-o=out] [-v]
    ip_query.py -h | --help | --version
Options:
    -h --help   show this help message and exit
    --version   show version and exit
    -i in       file that has ip each line [default: ips.txt]
    -o out      output file name(with 'csv' format) [default: out.csv]
    -v          explain what is being done
```

