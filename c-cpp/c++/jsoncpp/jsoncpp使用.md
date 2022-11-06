# jsoncpp的使用

## 安装jsoncpp库

### 1. mac 环境下

直接使用命令安装

```shell
brew install jsoncpp
```

### 2. Ubuntu 坏境下

```shell
sudo apt-get install libjsoncpp-dev
```

库的[头文件](https://so.csdn.net/so/search?q=头文件&spm=1001.2101.3001.7020)安装在/usr/include/jsoncpp中, 库API文档默认在/usr/share/doc/libjsoncpp-dev/jsoncpp-api-html/目录下

---

## json库的使用

### Jsoncpp 常用变量介绍

在Jsoncpp中，有几个常用的变量特别重要，首先介绍一下。

#### Json::Value

Json::Value 用来表示Json中的任何一种value抽象数据类型，具体来说，Json中的value可以是一下数据类型：

*   有符号整数 signed integer [range: Value::minInt - Value::maxInt]
*   无符号整数 unsigned integer (range: 0 - Value::maxUInt)
*   双精度浮点数 double
*   字符串 UTF-8 string
*   布尔型 boolean
*   空 ‘null’
*   一个Value的有序列表 an ordered list of Value
*   collection of name/value pairs (javascript object)

可以通过[][]的方法来取值。
```c++
//Examples:
Json::Value null_value; // null
Json::Value arr_value(Json::arrayValue); // []
Json::Value obj_value(Json::objectValue); // {}
```

#### Json::Reader

Json::Reader可以通过对Json源目标进行解析，得到一个解析好了的Json::Value，通常字符串或者文件输入流可以作为源目标。

假设现在有一个example.json文件

``` json
{
    "encoding" : "UTF-8",
    "plug-ins" : [
        "python",
        "c++",
        "ruby"
        ],
    "indent" : { "length" : 3, "use_space": true }
}
```

#### 使用Json::Reader对Json文件进行解析：

``` c++
bool parse (const std::string &document, Value &root, bool collectComments=true)
bool parse (std::istream &is, Value &root, bool collectComments=true)
```

```c++
Json::Value root;
Json::Reader reader;
std::ifstream ifs("example.json");//open file example.json

if(!reader.parse(ifs, root)){
   // fail to parse
}
else{
   // success
   std::cout<<root["encoding"].asString()<<endl;
   std::cout<<root["indent"]["length"].asInt()<<endl;
}
```

#### 使用Json::Reader对字符串进行解析

```c++
bool Json::Reader::parse ( const char * beginDoc,
        const char * endDoc,
        Value & root,
        bool collectComments = true 
    )   
```

```c++
  Json::Value root;
  Json::Reader reader;
  const char* s = "{\"uploadid\": \"UP000000\",\"code\": 100,\"msg\": \"\",\"files\": \"\"}"; 
  if(!reader.parse(s, root)){
    // "parse fail";
  }
  else{
      std::cout << root["uploadid"].asString();//print "UP000000"
  }
```

#### 获取所有的key，以及key对应的value

```c++
// 将读取的配置文件中的json内容解析
Json::Value root;       // 解析结果
Json::Reader reader;
if (reader.parse(conf_connect.c_str(), root)) {
  // 获取所有的key，以及key对应的value
  Json::Value::Members members;
  members = root.getMemberNames();    // 获取所有的 key 值

  // 遍历json，得到所有的key以及对应的value
  Json::Value::Members::iterator iter = members.begin();
  for (iter; iter != members.end(); iter++) {
    // 获取键对应的值
    m_conf[*iter] = root[*iter].asString();
  }
}
```

