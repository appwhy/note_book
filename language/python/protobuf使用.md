# protobuf使用

## 转json/dict

protobuf对象转json/dict对象时，使用的是`google/protobuf/json_format.py`模块中的相关函数

* 转json：`MessageToJson`， `Parse`。 前者底层调用的是`json.dumps`函数， 可以用过这里将ascii码转成中文（ensure_ascii参数）
* 转dict：`MessageToDict`， `ParseDict`

## `__str__`与`__repr__`

这两个函数是通过wrapper整合到protobuf对象中的（`google/protobuf/internal/python_message.py` 文件中实现）. 实际上是调用的函数`MessageToString`（`google/protobuf/text_format.py`）, 可以通过参数as_utf8是字符串展示utf8，而不是ascii编码



