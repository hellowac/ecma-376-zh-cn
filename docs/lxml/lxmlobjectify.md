# lxml.objectify

- 原文: <https://lxml.de/objectify.html>
- lxml.objectify API: <https://lxml.de/apidoc/lxml.objectify.html>
- xml schema - wiki:
    - xsd(xml schema definition): <https://zh.wikipedia.org/wiki/XML_Schema>
    - xsd schema language: <https://zh.wikipedia.org/wiki/XML_Schema语言>
- xml schema - w3school: <https://www.w3school.com.cn/schema/index.asp>
- xmlschema - github: <https://github.com/sissaschool/xmlschema>

=== "中文"

    **作者**
    
    : Stefan Behnel
    : Holger Joukl

    lxml 通过自定义 Element 实现支持类似于 [**Amara**](http://uche.ogbuji.net/tech/4suite/amara/) 绑定库或 [**gnosis.xml.objectify**](http://uche.ogbuji.net/tech/4suite/amara/) 的替代 API。 主要思想是将 XML 的使用隐藏在普通 Python 对象后面，有时称为数据绑定。 它允许您像处理普通的 Python 对象层次结构一样使用 XML。

    访问 XML 元素的子元素会部署对象属性访问。 如果有多个同名的子元素，可以使用切片和索引。 Python 数据类型会自动从 XML 内容中提取，并可供普通 Python 操作员使用。
    
    要设置和使用 objectify，您需要 `lxml.etree` 模块和 `lxml.objectify`：

    ```pycon
    >>> from lxml import etree
    >>> from lxml import objectify
    ```

=== "英文"

    **Authors**
    
    : Stefan Behnel
    : Holger Joukl


    lxml supports an alternative API similar to the [**Amara**](http://uche.ogbuji.net/tech/4suite/amara/) bindery or [**gnosis.xml.objectify**](http://gnosis.cx/download/) through a custom Element implementation. The main idea is to hide the usage of XML behind normal Python objects, sometimes referred to as data-binding. It allows you to use XML as if you were dealing with a normal Python object hierarchy.

    Accessing the children of an XML element deploys object attribute access. If there are multiple children with the same name, slicing and indexing can be used. Python data types are extracted from XML content automatically and made available to the normal Python operators.
    
    To set up and use objectify, you need both the lxml.etree module and lxml.objectify:

    ```pycon
    >>> from lxml import etree
    >>> from lxml import objectify
    ```

## lxml.objectify API接口

=== "中文"

    在 `lxml.objectify` 中，元素树提供了一个 API，它尽可能地模拟普通 Python 对象树的行为。

=== "英文"

    **The lxml.objectify API**

    In lxml.objectify, element trees provide an API that models the behaviour of normal Python object trees as closely as possible.

### 通过对象属性访问元素

=== "中文"

    objectify API 背后的主要思想是将 XML 元素访问隐藏在通常的对象属性访问模式后面。 向元素询问属性将返回具有相应标签名称的子元素序列：

    ```pycon
    >>> root = objectify.Element("root")
    >>> b = objectify.SubElement(root, "b")
    >>> print(root.b[0].tag)
    b
    >>> root.index(root.b[0])
    0
    >>> b = objectify.SubElement(root, "b")
    >>> print(root.b[0].tag)
    b
    >>> print(root.b[1].tag)
    b
    >>> root.index(root.b[1])
    1
    ```

    为了方便起见，您可以省略索引`0`来访问第一个子项：

    ```pycon
    >>> print(root.b.tag)
    b
    >>> root.index(root.b)
    0
    >>> del root.b
    ```

    迭代和切片也遵循请求的标签：

    ```pycon
    >>> x1 = objectify.SubElement(root, "x")
    >>> x2 = objectify.SubElement(root, "x")
    >>> x3 = objectify.SubElement(root, "x")
    
    >>> [ el.tag for el in root.x ]
    ['x', 'x', 'x']
    
    >>> [ el.tag for el in root.x[1:3] ]
    ['x', 'x']
    
    >>> [ el.tag for el in root.x[-1:] ]
    ['x']
    
    >>> del root.x[1:2]
    >>> [ el.tag for el in root.x ]
    ['x', 'x']
    ```

    如果您想迭代所有子项或需要为标记提供特定的命名空间，请使用 `iterchildren()` 方法。 与其他迭代方法一样，它支持可选的标签关键字参数：

    ```pycon
    >>> [ el.tag for el in root.iterchildren() ]
    ['b', 'x', 'x']
    
    >>> [ el.tag for el in root.iterchildren(tag='b') ]
    ['b']
    
    >>> [ el.tag for el in root.b ]
    ['b']
    ```

    XML 属性的访问方式与普通 `ElementTree API` 中一样:

    ```pycon
    >>> c = objectify.SubElement(root, "c", myattr="someval")
    >>> print(root.c.get("myattr"))
    someval
    
    >>> root.c.set("c", "oh-oh")
    >>> print(root.c.get("c"))
    oh-oh
    ```

    除了用于将元素附加到树的普通 `ElementTree API` 之外，还可以通过将子树分配给对象属性来添加子树。 在这种情况下，子树会自动深度复制，并更新其根的标记名称以匹配属性名称：

    ```pycon
    >>> el = objectify.Element("yet_another_child")
    >>> root.new_child = el
    >>> print(root.new_child.tag)
    new_child
    >>> print(el.tag)
    yet_another_child
    
    >>> root.y = [ objectify.Element("y"), objectify.Element("y") ]
    >>> [ el.tag for el in root.y ]
    ['y', 'y']
    ```

    后者是对整个切片进行操作的缩写形式：

    ```pycon
    >>> root.y[:] = [ objectify.Element("y") ]
    >>> [ el.tag for el in root.y ]
    ['y']
    ```

    你也可以用这种方式替代子元素:

    ```pycon
    >>> child1 = objectify.SubElement(root, "child")
    >>> child2 = objectify.SubElement(root, "child")
    >>> child3 = objectify.SubElement(root, "child")
    
    >>> el = objectify.Element("new_child")
    >>> subel = objectify.SubElement(el, "sub")
    
    >>> root.child = el
    >>> print(root.child.sub.tag)
    sub
    
    >>> root.child[2] = el
    >>> print(root.child[2].sub.tag)
    sub
    ```

    请{++ 注意 ++}，更改元素的标签名称时必须特别小心：

    ```pycon
    >>> print(root.b.tag)
    b
    >>> root.b.tag = "notB"
    >>> root.b
    Traceback (most recent call last):
      ...
    AttributeError: no such child: b
    >>> print(root.notB.tag)
    notB
    ```

=== "英文"

    **Element access through object attributes**

    The main idea behind the objectify API is to hide XML element access behind the usual object attribute access pattern. Asking an element for an attribute will return the sequence of children with corresponding tag names:

    ```pycon
    >>> root = objectify.Element("root")
    >>> b = objectify.SubElement(root, "b")
    >>> print(root.b[0].tag)
    b
    >>> root.index(root.b[0])
    0
    >>> b = objectify.SubElement(root, "b")
    >>> print(root.b[0].tag)
    b
    >>> print(root.b[1].tag)
    b
    >>> root.index(root.b[1])
    1
    ```

    For convenience, you can omit the index '0' to access the first child:

    ```pycon
    >>> print(root.b.tag)
    b
    >>> root.index(root.b)
    0
    >>> del root.b
    ```

    Iteration and slicing also obey the requested tag:

    ```pycon
    >>> x1 = objectify.SubElement(root, "x")
    >>> x2 = objectify.SubElement(root, "x")
    >>> x3 = objectify.SubElement(root, "x")
    
    >>> [ el.tag for el in root.x ]
    ['x', 'x', 'x']
    
    >>> [ el.tag for el in root.x[1:3] ]
    ['x', 'x']
    
    >>> [ el.tag for el in root.x[-1:] ]
    ['x']
    
    >>> del root.x[1:2]
    >>> [ el.tag for el in root.x ]
    ['x', 'x']
    ```

    If you want to iterate over all children or need to provide a specific namespace for the tag, use the iterchildren() method. Like the other methods for iteration, it supports an optional tag keyword argument:

    ```pycon
    >>> [ el.tag for el in root.iterchildren() ]
    ['b', 'x', 'x']
    
    >>> [ el.tag for el in root.iterchildren(tag='b') ]
    ['b']
    
    >>> [ el.tag for el in root.b ]
    ['b']
    ```

    XML attributes are accessed as in the normal ElementTree API:

    ```pycon
    >>> c = objectify.SubElement(root, "c", myattr="someval")
    >>> print(root.c.get("myattr"))
    someval
    
    >>> root.c.set("c", "oh-oh")
    >>> print(root.c.get("c"))
    oh-oh
    ```

    In addition to the normal ElementTree API for appending elements to trees, subtrees can also be added by assigning them to object attributes. In this case, the subtree is automatically deep copied and the tag name of its root is updated to match the attribute name:

    ```pycon
    >>> el = objectify.Element("yet_another_child")
    >>> root.new_child = el
    >>> print(root.new_child.tag)
    new_child
    >>> print(el.tag)
    yet_another_child
    
    >>> root.y = [ objectify.Element("y"), objectify.Element("y") ]
    >>> [ el.tag for el in root.y ]
    ['y', 'y']
    ```

    The latter is a short form for operations on the full slice:

    ```pycon
    >>> root.y[:] = [ objectify.Element("y") ]
    >>> [ el.tag for el in root.y ]
    ['y']
    ```

    You can also replace children that way:

    ```pycon
    >>> child1 = objectify.SubElement(root, "child")
    >>> child2 = objectify.SubElement(root, "child")
    >>> child3 = objectify.SubElement(root, "child")
    
    >>> el = objectify.Element("new_child")
    >>> subel = objectify.SubElement(el, "sub")
    
    >>> root.child = el
    >>> print(root.child.sub.tag)
    sub
    
    >>> root.child[2] = el
    >>> print(root.child[2].sub.tag)
    sub
    ```

    Note that special care must be taken when changing the tag name of an element:

    ```pycon
    >>> print(root.b.tag)
    b
    >>> root.b.tag = "notB"
    >>> root.b
    Traceback (most recent call last):
      ...
    AttributeError: no such child: b
    >>> print(root.notB.tag)
    notB
    ```

### 创建对象树

=== "中文"

    与 `lxml.etree` 一样，您可以通过解析 XML 文档或从头开始构建一棵对象化树来创建对象化树。 要解析文档，只需使用模块的 [parse()](https://lxml.de/apidoc/lxml.etree.html#lxml.etree._ElementTree.parse) 或 [fromstring()](https://lxml.de/apidoc/lxml.etree.html#lxml.etree.fromstring) 函数：

    ```pycon
    >>> fileobject = StringIO('<test/>')
    
    >>> tree = objectify.parse(fileobject)
    >>> print(isinstance(tree.getroot(), objectify.ObjectifiedElement))
    True
    
    >>> root = objectify.fromstring('<test/>')
    >>> print(isinstance(root, objectify.ObjectifiedElement))
    True
    ```

    为了在内存中构建新树，objectify 复制了 `lxml.etree` 中的标准工厂函数 [Element()](https://lxml.de/apidoc/lxml.etree.html#lxml.etree.Element)：

    ```pycon
    >>> obj_el = objectify.Element("new")
    >>> print(isinstance(obj_el, objectify.ObjectifiedElement))
    True
    ```

    创建这样的元素后，您可以使用 `lxml.etree` 的常用 API 将子元素添加到树中：

    ```pycon
    >>> child = objectify.SubElement(obj_el, "newchild", attr="value")
    ```

    新的子元素将自动从其树继承对象化行为。 但是，您通过 `lxml.etree` 的 `Element()` 工厂（而不是 objectify）创建的所有独立元素本身将不支持 objectify API：

    ```pycon
    >>> subel = objectify.SubElement(obj_el, "sub")
    >>> print(isinstance(subel, objectify.ObjectifiedElement))
    True
    
    >>> independent_el = etree.Element("new")
    >>> print(isinstance(independent_el, objectify.ObjectifiedElement))
    False
    ```

=== "英文"

    **Creating objectify trees**

    As with lxml.etree, you can either create an objectify tree by parsing an XML document or by building one from scratch. To parse a document, just use the parse() or fromstring() functions of the module:

    ```pycon
    >>> fileobject = StringIO('<test/>')
    
    >>> tree = objectify.parse(fileobject)
    >>> print(isinstance(tree.getroot(), objectify.ObjectifiedElement))
    True
    
    >>> root = objectify.fromstring('<test/>')
    >>> print(isinstance(root, objectify.ObjectifiedElement))
    True
    ```

    To build a new tree in memory, objectify replicates the standard factory function Element() from lxml.etree:

    ```pycon
    >>> obj_el = objectify.Element("new")
    >>> print(isinstance(obj_el, objectify.ObjectifiedElement))
    True
    ```

    After creating such an Element, you can use the usual API of lxml.etree to add SubElements to the tree:

    ```pycon
    >>> child = objectify.SubElement(obj_el, "newchild", attr="value")
    ```

    New subelements will automatically inherit the objectify behaviour from their tree. However, all independent elements that you create through the Element() factory of lxml.etree (instead of objectify) will not support the objectify API by themselves:

    ```pycon
    >>> subel = objectify.SubElement(obj_el, "sub")
    >>> print(isinstance(subel, objectify.ObjectifiedElement))
    True
    
    >>> independent_el = etree.Element("new")
    >>> print(isinstance(independent_el, objectify.ObjectifiedElement))
    False
    ```

### 使用 E-factory 生成节点树

=== "中文"

    为了进一步简化树的生成，您可以使用 E-factory：

    ```pycon
    >>> E = objectify.E
    >>> root = E.root(
    ...   E.a(5),
    ...   E.b(6.21),
    ...   E.c(True),
    ...   E.d("how", tell="me")
    ... )
    
    >>> print(etree.tostring(root, pretty_print=True))
    <root xmlns:py="http://codespeak.net/lxml/objectify/pytype">
      <a py:pytype="int">5</a>
      <b py:pytype="float">6.21</b>
      <c py:pytype="bool">true</c>
      <d py:pytype="str" tell="me">how</d>
    </root>
    ```

    这允许您在标签中编写特定语言:

    ```pycon
    >>> ROOT = objectify.E.root
    >>> TITLE = objectify.E.title
    >>> HOWMANY = getattr(objectify.E, "how-many")
    
    >>> root = ROOT(
    ...   TITLE("The title"),
    ...   HOWMANY(5)
    ... )
    
    >>> print(etree.tostring(root, pretty_print=True))
    <root xmlns:py="http://codespeak.net/lxml/objectify/pytype">
      <title py:pytype="str">The title</title>
      <how-many py:pytype="int">5</how-many>
    </root>
    ```

    objectify.E 是 [objectify.ElementMaker](https://lxml.de/apidoc/lxml.objectify.html#lxml.objectify.ElementMaker) 的实例。 默认情况下，它创建没有命名空间的 pytype 注释元素。 您可以通过将 `False` 传递给构造函数的 `annotate` 关键字参数来关闭 `pytype` 注释。 您还可以传递默认名称空间和 `nsmap`：

    ```pycon
    >>> myE = objectify.ElementMaker(annotate=False,
    ...           namespace="http://my/ns", nsmap={None : "http://my/ns"})
    
    >>> root = myE.root( myE.someint(2) )
    
    >>> print(etree.tostring(root, pretty_print=True))
    <root xmlns="http://my/ns">
      <someint>2</someint>
    </root>
    ```

=== "英文"

    **Tree generation with the E-factory**

    To simplify the generation of trees even further, you can use the E-factory:

    ```pycon
    >>> E = objectify.E
    >>> root = E.root(
    ...   E.a(5),
    ...   E.b(6.21),
    ...   E.c(True),
    ...   E.d("how", tell="me")
    ... )
    
    >>> print(etree.tostring(root, pretty_print=True))
    <root xmlns:py="http://codespeak.net/lxml/objectify/pytype">
      <a py:pytype="int">5</a>
      <b py:pytype="float">6.21</b>
      <c py:pytype="bool">true</c>
      <d py:pytype="str" tell="me">how</d>
    </root>
    ```

    This allows you to write up a specific language in tags:

    ```pycon
    >>> ROOT = objectify.E.root
    >>> TITLE = objectify.E.title
    >>> HOWMANY = getattr(objectify.E, "how-many")
    
    >>> root = ROOT(
    ...   TITLE("The title"),
    ...   HOWMANY(5)
    ... )
    
    >>> print(etree.tostring(root, pretty_print=True))
    <root xmlns:py="http://codespeak.net/lxml/objectify/pytype">
      <title py:pytype="str">The title</title>
      <how-many py:pytype="int">5</how-many>
    </root>
    ```

    objectify.E is an instance of objectify.ElementMaker. By default, it creates pytype annotated Elements without a namespace. You can switch off the pytype annotation by passing False to the annotate keyword argument of the constructor. You can also pass a default namespace and an nsmap:

    ```pycon
    >>> myE = objectify.ElementMaker(annotate=False,
    ...           namespace="http://my/ns", nsmap={None : "http://my/ns"})
    
    >>> root = myE.root( myE.someint(2) )
    
    >>> print(etree.tostring(root, pretty_print=True))
    <root xmlns="http://my/ns">
      <someint>2</someint>
    </root>
    ```

### 命名空间处理

=== "中文"

    在标签查找期间，名称空间主要在幕后处理。 如果访问 Element 的子元素而不指定命名空间，则查找将使用父元素的命名空间：

    ```pycon
    >>> root = objectify.Element("{http://ns/}root")
    >>> b = objectify.SubElement(root, "{http://ns/}b")
    >>> c = objectify.SubElement(root, "{http://other/}c")
    
    >>> print(root.b.tag)
    {http://ns/}b
    ```

    请注意，lxml.etree 的 [SubElement()](https://lxml.de/apidoc/lxml.etree.html#lxml.etree.SubElement) 工厂在创建新子元素时不会继承任何名称空间。 元素创建必须明确命名空间，并通过如上所述的 E-factory 进行简化。
    
    然而，查找元素时则隐式继承命名空间：

    ```pycon
    >>> print(root.b.tag)
    {http://ns/}b
    
    >>> print(root.c)
    Traceback (most recent call last):
        ...
    AttributeError: no such child: {http://ns/}c
    ```

    要访问与其父级不同的命名空间中的元素，可以使用 `getattr()`：

    ```pycon
    >>> c = getattr(root, "{http://other/}c")
    >>> print(c.tag)
    {http://other/}c
    ```
    
    为了方便起见，还有一种快速访问项目的方法：

    ```pycon
    >>> c = root["{http://other/}c"]
    >>> print(c.tag)
    {http://other/}c
    ```

    必须使用相同的方法来访问标签名称不是有效 Python 标识符的子项：

    ```pycon
    >>> el = objectify.SubElement(root, "{http://ns/}tag-name")
    >>> print(root["tag-name"].tag)
    {http://ns/}tag-name
    
    >>> new_el = objectify.Element("{http://ns/}new-element")
    >>> el = objectify.SubElement(new_el, "{http://ns/}child")
    >>> el = objectify.SubElement(new_el, "{http://ns/}child")
    >>> el = objectify.SubElement(new_el, "{http://ns/}child")
    
    >>> root["tag-name"] = [ new_el, new_el ]
    >>> print(len(root["tag-name"]))
    2
    >>> print(root["tag-name"].tag)
    {http://ns/}tag-name
    
    >>> print(len(root["tag-name"].child))
    3
    >>> print(root["tag-name"].child.tag)
    {http://ns/}child
    >>> print(root["tag-name"][1].child.tag)
    {http://ns/}child
    ```

    或者对于 `lxml.objectify` 中具有特殊含义的名称：

    ```pycon
    >>> root = objectify.XML("<root><text>TEXT</text></root>")

    >>> print(root.text.text)
    Traceback (most recent call last):
      ...
    AttributeError: 'NoneType' object has no attribute 'text'
    
    >>> print(root["text"].text)
    TEXT
    ```

=== "英文"

    **Namespace handling**

    During tag lookups, namespaces are handled mostly behind the scenes. If you access a child of an Element without specifying a namespace, the lookup will use the namespace of the parent:

    ```pycon
    >>> root = objectify.Element("{http://ns/}root")
    >>> b = objectify.SubElement(root, "{http://ns/}b")
    >>> c = objectify.SubElement(root, "{http://other/}c")
    
    >>> print(root.b.tag)
    {http://ns/}b
    ```

    Note that the SubElement() factory of lxml.etree does not inherit any namespaces when creating a new subelement. Element creation must be explicit about the namespace, and is simplified through the E-factory as described above.
    
    Lookups, however, inherit namespaces implicitly:

    ```pycon
    >>> print(root.b.tag)
    {http://ns/}b
    
    >>> print(root.c)
    Traceback (most recent call last):
        ...
    AttributeError: no such child: {http://ns/}c
    ```

    To access an element in a different namespace than its parent, you can use getattr():

    ```pycon
    >>> c = getattr(root, "{http://other/}c")
    >>> print(c.tag)
    {http://other/}c
    ```
    
    For convenience, there is also a quick way through item access:

    ```pycon
    >>> c = root["{http://other/}c"]
    >>> print(c.tag)
    {http://other/}c
    ```

    The same approach must be used to access children with tag names that are not valid Python identifiers:

    ```pycon
    >>> el = objectify.SubElement(root, "{http://ns/}tag-name")
    >>> print(root["tag-name"].tag)
    {http://ns/}tag-name
    
    >>> new_el = objectify.Element("{http://ns/}new-element")
    >>> el = objectify.SubElement(new_el, "{http://ns/}child")
    >>> el = objectify.SubElement(new_el, "{http://ns/}child")
    >>> el = objectify.SubElement(new_el, "{http://ns/}child")
    
    >>> root["tag-name"] = [ new_el, new_el ]
    >>> print(len(root["tag-name"]))
    2
    >>> print(root["tag-name"].tag)
    {http://ns/}tag-name
    
    >>> print(len(root["tag-name"].child))
    3
    >>> print(root["tag-name"].child.tag)
    {http://ns/}child
    >>> print(root["tag-name"][1].child.tag)
    {http://ns/}child
    ```

    or for names that have a special meaning in lxml.objectify:

    ```pycon
    >>> root = objectify.XML("<root><text>TEXT</text></root>")

    >>> print(root.text.text)
    Traceback (most recent call last):
      ...
    AttributeError: 'NoneType' object has no attribute 'text'
    
    >>> print(root["text"].text)
    TEXT
    ```

## 断言Schema

=== "中文"

    当处理来自不同源的 XML 文档时，您通常会要求它们遵循通用的模式。 在 **lxml.objectify** 中，这直接转化为强制执行特定的对象树，即确保预期的对象属性存在并具有预期的类型。 这可以通过解析时的 XML 模式验证轻松实现。 另请参阅有关此主题的[验证文档](https://lxml.de/validation.html){target="_blank"}。

    首先，我们需要一个了解我们的schema的解析器，所以假设我们从类似文件的对象（或文件或文件名）解析schema：

    ```pycon
    >>> f = StringIO('''\
    ...   <xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema">
    ...     <xsd:element name="a" type="AType"/>
    ...     <xsd:complexType name="AType">
    ...       <xsd:sequence>
    ...         <xsd:element name="b" type="xsd:string" />
    ...       </xsd:sequence>
    ...     </xsd:complexType>
    ...   </xsd:schema>
    ... ''')
    >>> schema = etree.XMLSchema(file=f)
    ```

    创建验证解析器时，我们必须确保它返回对象化树。 最好使用 [makeparser()](https://lxml.de/apidoc/lxml.objectify.html#lxml.objectify.makeparser) 函数来完成：

    ```pycon
    >>> parser = objectify.makeparser(schema = schema)
    ```

    现在我们可以用它来解析有效的文档:

    ```pycon
    >>> xml = "<a><b>test</b></a>"
    >>> a = objectify.fromstring(xml, parser)
    
    >>> print(a.b)
    test
    ```

    或者无效的文件:

    ``` pycon
    >>> xml = b"<a><b>test</b><c/></a>"
    >>> a = objectify.fromstring(xml, parser)  # doctest: +ELLIPSIS
    Traceback (most recent call last):
    lxml.etree.XMLSyntaxError: Element 'c': This element is not expected...
    ```

    请注意，这同样适用于解析时 DTD 验证，只是 DTD 在设计上不支持任何数据类型。

=== "英文"

    **Asserting a Schema**

    When dealing with XML documents from different sources, you will often require them to follow a common schema. In lxml.objectify, this directly translates to enforcing a specific object tree, i.e. expected object attributes are ensured to be there and to have the expected type. This can easily be achieved through XML Schema validation at parse time. Also see the [documentation on validation](https://lxml.de/validation.html) on this topic.

    First of all, we need a parser that knows our schema, so let's say we parse the schema from a file-like object (or file or filename):

    ```pycon
    >>> f = StringIO('''\
    ...   <xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema">
    ...     <xsd:element name="a" type="AType"/>
    ...     <xsd:complexType name="AType">
    ...       <xsd:sequence>
    ...         <xsd:element name="b" type="xsd:string" />
    ...       </xsd:sequence>
    ...     </xsd:complexType>
    ...   </xsd:schema>
    ... ''')
    >>> schema = etree.XMLSchema(file=f)
    ```

    When creating the validating parser, we must make sure it returns objectify trees. This is best done with the makeparser() function:

    ```pycon
    >>> parser = objectify.makeparser(schema = schema)
    ```

    Now we can use it to parse a valid document:

    ```pycon
    >>> xml = "<a><b>test</b></a>"
    >>> a = objectify.fromstring(xml, parser)
    
    >>> print(a.b)
    test
    ```

    Or an invalid document:

    ```pycon
    >>> xml = b"<a><b>test</b><c/></a>"
    >>> a = objectify.fromstring(xml, parser)  # doctest: +ELLIPSIS
    Traceback (most recent call last):
    lxml.etree.XMLSyntaxError: Element 'c': This element is not expected...
    ```

    Note that the same works for parse-time DTD validation, except that DTDs do not support any data types by design.

## ObjectPath

=== "中文"

    为了方便和快速，`objectify` 支持自己的路径语言，由 `ObjectPath` 类表示：

    ```pycon
    >>> root = objectify.Element("{http://ns/}root")
    >>> b1 = objectify.SubElement(root, "{http://ns/}b")
    >>> c  = objectify.SubElement(b1,   "{http://ns/}c")
    >>> b2 = objectify.SubElement(root, "{http://ns/}b")
    >>> d  = objectify.SubElement(root, "{http://other/}d")
    
    >>> path = objectify.ObjectPath("root.b.c")
    >>> print(path)
    root.b.c
    >>> path.hasattr(root)
    True
    >>> print(path.find(root).tag)
    {http://ns/}c
    
    >>> find = objectify.ObjectPath("root.b.c")
    >>> print(find(root).tag)
    {http://ns/}c
    
    >>> find = objectify.ObjectPath("root.{http://other/}d")
    >>> print(find(root).tag)
    {http://other/}d
    
    >>> find = objectify.ObjectPath("root.{not}there")
    >>> print(find(root).tag)
    Traceback (most recent call last):
      ...
    AttributeError: no such child: {not}there
    
    >>> find = objectify.ObjectPath("{not}there")
    >>> print(find(root).tag)
    Traceback (most recent call last):
      ...
    ValueError: root element does not match: need {not}there, got {http://ns/}root
    
    >>> find = objectify.ObjectPath("root.b[1]")
    >>> print(find(root).tag)
    {http://ns/}b
    
    >>> find = objectify.ObjectPath("root.{http://ns/}b[1]")
    >>> print(find(root).tag)
    {http://ns/}b
    ```

    除了字符串之外，ObjectPath 还接受路径段列表：

    ```pycon
    >>> find = objectify.ObjectPath(['root', 'b', 'c'])
    >>> print(find(root).tag)
    {http://ns/}c
    
    >>> find = objectify.ObjectPath(['root', '{http://ns/}b[1]'])
    >>> print(find(root).tag)
    {http://ns/}b
    ```

    您还可以使用以**“.”**开头的相对路径忽略实际的根元素并仅继承其名称空间：

    ```pycon
    >>> find = objectify.ObjectPath(".b[1]")
    >>> print(find(root).tag)
    {http://ns/}b
    
    >>> find = objectify.ObjectPath(['', 'b[1]'])
    >>> print(find(root).tag)
    {http://ns/}b
    
    >>> find = objectify.ObjectPath(".unknown[1]")
    >>> print(find(root).tag)
    Traceback (most recent call last):
      ...
    AttributeError: no such child: {http://ns/}unknown
    
    >>> find = objectify.ObjectPath(".{http://other/}unknown[1]")
    >>> print(find(root).tag)
    Traceback (most recent call last):
      ...
    AttributeError: no such child: {http://other/}unknown
    ```

    为了方便起见，单个点代表空的 ObjectPath（标识）：

    ```pycon
    >>> find = objectify.ObjectPath(".")
    >>> print(find(root).tag)
    {http://ns/}root
    ```

    ObjectPath 对象可用于操作树：

    ```pycon
    >>> root = objectify.Element("{http://ns/}root")

    >>> path = objectify.ObjectPath(".some.child.{http://other/}unknown")
    >>> path.hasattr(root)
    False
    >>> path.find(root)
    Traceback (most recent call last):
      ...
    AttributeError: no such child: {http://ns/}some
    
    >>> path.setattr(root, "my value") # creates children as necessary
    >>> path.hasattr(root)
    True
    >>> print(path.find(root).text)
    my value
    >>> print(root.some.child["{http://other/}unknown"].text)
    my value
    
    >>> print(len( path.find(root) ))
    1
    >>> path.addattr(root, "my new value")
    >>> print(len( path.find(root) ))
    2
    >>> [ el.text for el in path.find(root) ]
    ['my value', 'my new value']
    ```

    与属性分配一样，setattr() 接受列表：

    ```pycon
    >>> path.setattr(root, ["v1", "v2", "v3"])
    >>> [ el.text for el in path.find(root) ]
    ['v1', 'v2', 'v3']
    ```

    但请注意，仅当子项存在时，此上下文中才支持索引。 对不存在的子项建立索引不会扩展或创建此类子项的列表，但会引发异常：

    ```pycon
    >>> path = objectify.ObjectPath(".{non}existing[1]")
    >>> path.setattr(root, "my value")
    Traceback (most recent call last):
      ...
    TypeError: creating indexed path attributes is not supported
    ```

    值得注意的是，ObjectPath 不依赖于 `objectify` 模块或 `ObjectifiedElement` 实现。 它还可以与普通 `lxml.etree` API 中的元素结合使用。

=== "英文"

    **ObjectPath**

    For both convenience and speed, objectify supports its own path language, represented by the ObjectPath class:

    ```pycon
    >>> root = objectify.Element("{http://ns/}root")
    >>> b1 = objectify.SubElement(root, "{http://ns/}b")
    >>> c  = objectify.SubElement(b1,   "{http://ns/}c")
    >>> b2 = objectify.SubElement(root, "{http://ns/}b")
    >>> d  = objectify.SubElement(root, "{http://other/}d")
    
    >>> path = objectify.ObjectPath("root.b.c")
    >>> print(path)
    root.b.c
    >>> path.hasattr(root)
    True
    >>> print(path.find(root).tag)
    {http://ns/}c
    
    >>> find = objectify.ObjectPath("root.b.c")
    >>> print(find(root).tag)
    {http://ns/}c
    
    >>> find = objectify.ObjectPath("root.{http://other/}d")
    >>> print(find(root).tag)
    {http://other/}d
    
    >>> find = objectify.ObjectPath("root.{not}there")
    >>> print(find(root).tag)
    Traceback (most recent call last):
      ...
    AttributeError: no such child: {not}there
    
    >>> find = objectify.ObjectPath("{not}there")
    >>> print(find(root).tag)
    Traceback (most recent call last):
      ...
    ValueError: root element does not match: need {not}there, got {http://ns/}root
    
    >>> find = objectify.ObjectPath("root.b[1]")
    >>> print(find(root).tag)
    {http://ns/}b
    
    >>> find = objectify.ObjectPath("root.{http://ns/}b[1]")
    >>> print(find(root).tag)
    {http://ns/}b
    ```

    Apart from strings, ObjectPath also accepts lists of path segments:

    ```pycon
    >>> find = objectify.ObjectPath(['root', 'b', 'c'])
    >>> print(find(root).tag)
    {http://ns/}c
    
    >>> find = objectify.ObjectPath(['root', '{http://ns/}b[1]'])
    >>> print(find(root).tag)
    {http://ns/}b
    ```

    You can also use relative paths starting with a '.' to ignore the actual root element and only inherit its namespace:

    ```pycon
    >>> find = objectify.ObjectPath(".b[1]")
    >>> print(find(root).tag)
    {http://ns/}b
    
    >>> find = objectify.ObjectPath(['', 'b[1]'])
    >>> print(find(root).tag)
    {http://ns/}b
    
    >>> find = objectify.ObjectPath(".unknown[1]")
    >>> print(find(root).tag)
    Traceback (most recent call last):
      ...
    AttributeError: no such child: {http://ns/}unknown
    
    >>> find = objectify.ObjectPath(".{http://other/}unknown[1]")
    >>> print(find(root).tag)
    Traceback (most recent call last):
      ...
    AttributeError: no such child: {http://other/}unknown
    ```

    For convenience, a single dot represents the empty ObjectPath (identity):

    ```pycon
    >>> find = objectify.ObjectPath(".")
    >>> print(find(root).tag)
    {http://ns/}root
    ```

    ObjectPath objects can be used to manipulate trees:

    ```pycon
    >>> root = objectify.Element("{http://ns/}root")

    >>> path = objectify.ObjectPath(".some.child.{http://other/}unknown")
    >>> path.hasattr(root)
    False
    >>> path.find(root)
    Traceback (most recent call last):
      ...
    AttributeError: no such child: {http://ns/}some
    
    >>> path.setattr(root, "my value") # creates children as necessary
    >>> path.hasattr(root)
    True
    >>> print(path.find(root).text)
    my value
    >>> print(root.some.child["{http://other/}unknown"].text)
    my value
    
    >>> print(len( path.find(root) ))
    1
    >>> path.addattr(root, "my new value")
    >>> print(len( path.find(root) ))
    2
    >>> [ el.text for el in path.find(root) ]
    ['my value', 'my new value']
    ```

    As with attribute assignment, setattr() accepts lists:

    ```pycon
    >>> path.setattr(root, ["v1", "v2", "v3"])
    >>> [ el.text for el in path.find(root) ]
    ['v1', 'v2', 'v3']
    ```

    Note, however, that indexing is only supported in this context if the children exist. Indexing of non existing children will not extend or create a list of such children but raise an exception:

    ```pycon
    >>> path = objectify.ObjectPath(".{non}existing[1]")
    >>> path.setattr(root, "my value")
    Traceback (most recent call last):
      ...
    TypeError: creating indexed path attributes is not supported
    ```

    It is worth noting that ObjectPath does not depend on the objectify module or the ObjectifiedElement implementation. It can also be used in combination with Elements from the normal lxml.etree API.

## Python数据类型

=== "中文"

    objectify 模块了解 Python 数据类型，并尽力让元素内容表现得像它们。 例如，它们支持普通的数学运算符：

    ```pycon
    >>> root = objectify.fromstring(
    ...             "<root><a>5</a><b>11</b><c>true</c><d>hoi</d></root>")
    >>> root.a + root.b
    16
    >>> root.a += root.b
    >>> print(root.a)
    16
    
    >>> root.a = 2
    >>> print(root.a + 2)
    4
    >>> print(1 + root.a)
    3
    
    >>> print(root.c)
    True
    >>> root.c = False
    >>> if not root.c:
    ...     print("false!")
    false!
    
    >>> print(root.d + " test !")
    hoi test !
    >>> root.d = "%s - %s"
    >>> print(root.d % (1234, 12345))
    1234 - 12345
    ```

    但是，数据元素继续提供 **objectify API**。 这意味着诸如 `len()`、切片和索引（例如字符串）之类的序列操作不能表现为 Python 类型。 与所有其他树元素一样，它们显示了 **objectify** 元素的正常切片行为：

    ```pycon
    >>> root = objectify.fromstring("<root><a>test</a><b>toast</b></root>")
    >>> print(root.a + ' me') # behaves like a string, right?
    test me
    >>> len(root.a) # but there's only one 'a' element!
    1
    >>> [ a.tag for a in root.a ]
    ['a']
    >>> print(root.a[0].tag)
    a
    
    >>> print(root.a)
    test
    >>> [ str(a) for a in root.a[:1] ]
    ['test']
    ```

    如果需要对数据类型运行序列操作，则必须向 API 询问真实的 Python 值。 字符串值始终可以通过普通的 `ElementTree` 的 `.text` 属性获得。 此外，所有数据类都提供 `.pyval` 属性，该属性以纯 Python 类型返回值：

    ```pycon
    >>> root = objectify.fromstring("<root><a>test</a><b>5</b></root>")
    >>> root.a.text
    'test'
    >>> root.a.pyval
    'test'
    
    >>> root.b.text
    '5'
    >>> root.b.pyval
    5
    ```

    但请注意，这两个属性在 **objectify** 中都是只读的。 如果要更改值，只需将它们直接分配给属性即可：

    ```pycon
    >>> root.a.text  = "25"
    Traceback (most recent call last):
      ...
    TypeError: attribute 'text' of 'StringElement' objects is not writable
    
    >>> root.a.pyval = 25
    Traceback (most recent call last):
      ...
    TypeError: attribute 'pyval' of 'StringElement' objects is not writable
    
    >>> root.a = 25
    >>> print(root.a)
    25
    >>> print(root.a.pyval)
    25
    ```

    换句话说，**objectify** 数据元素的行为就像不可变的 Python 类型。 您可以替换它们，但不能修改它们。

=== "英文"

    **Python data types**

    The objectify module knows about Python data types and tries its best to let element content behave like them. For example, they support the normal math operators:

    ```pycon
    >>> root = objectify.fromstring(
    ...             "<root><a>5</a><b>11</b><c>true</c><d>hoi</d></root>")
    >>> root.a + root.b
    16
    >>> root.a += root.b
    >>> print(root.a)
    16
    
    >>> root.a = 2
    >>> print(root.a + 2)
    4
    >>> print(1 + root.a)
    3
    
    >>> print(root.c)
    True
    >>> root.c = False
    >>> if not root.c:
    ...     print("false!")
    false!
    
    >>> print(root.d + " test !")
    hoi test !
    >>> root.d = "%s - %s"
    >>> print(root.d % (1234, 12345))
    1234 - 12345
    ```

    However, data elements continue to provide the objectify API. This means that sequence operations such as len(), slicing and indexing (e.g. of strings) cannot behave as the Python types. Like all other tree elements, they show the normal slicing behaviour of objectify elements:

    ```pycon
    >>> root = objectify.fromstring("<root><a>test</a><b>toast</b></root>")
    >>> print(root.a + ' me') # behaves like a string, right?
    test me
    >>> len(root.a) # but there's only one 'a' element!
    1
    >>> [ a.tag for a in root.a ]
    ['a']
    >>> print(root.a[0].tag)
    a
    
    >>> print(root.a)
    test
    >>> [ str(a) for a in root.a[:1] ]
    ['test']
    ```

    If you need to run sequence operations on data types, you must ask the API for the real Python value. The string value is always available through the normal ElementTree .text attribute. Additionally, all data classes provide a .pyval attribute that returns the value as plain Python type:

    ```pycon
    >>> root = objectify.fromstring("<root><a>test</a><b>5</b></root>")
    >>> root.a.text
    'test'
    >>> root.a.pyval
    'test'
    
    >>> root.b.text
    '5'
    >>> root.b.pyval
    5
    ```

    Note, however, that both attributes are read-only in objectify. If you want to change values, just assign them directly to the attribute:

    ```pycon
    >>> root.a.text  = "25"
    Traceback (most recent call last):
      ...
    TypeError: attribute 'text' of 'StringElement' objects is not writable
    
    >>> root.a.pyval = 25
    Traceback (most recent call last):
      ...
    TypeError: attribute 'pyval' of 'StringElement' objects is not writable
    
    >>> root.a = 25
    >>> print(root.a)
    25
    >>> print(root.a.pyval)
    25
    ```

    In other words, objectify data elements behave like immutable Python types. You can replace them, but not modify them.

### 递归数并表示

=== "中文"

    要查看当前使用的数据类型，您可以调用模块级 `dump()` 函数，该函数返回元素的递归字符串表示形式：

    ```pycon
    >>> root = objectify.fromstring("""
    ... <root xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
    ...   <a attr1="foo" attr2="bar">1</a>
    ...   <a>1.2</a>
    ...   <b>1</b>
    ...   <b>true</b>
    ...   <c>what?</c>
    ...   <d xsi:nil="true"/>
    ... </root>
    ... """)
    
    >>> print(objectify.dump(root))
    root = None [ObjectifiedElement]
        a = 1 [IntElement]
          * attr1 = 'foo'
          * attr2 = 'bar'
        a = 1.2 [FloatElement]
        b = 1 [IntElement]
        b = True [BoolElement]
        c = 'what?' [StringElement]
        d = None [NoneElement]
          * xsi:nil = 'true'
    ```

    您可以在同一个子节点的不同类型之间自由切换：

    ```pycon
    >>> root = objectify.fromstring("<root><a>5</a></root>")
    >>> print(objectify.dump(root))
    root = None [ObjectifiedElement]
        a = 5 [IntElement]
    
    >>> root.a = 'nice string!'
    >>> print(objectify.dump(root))
    root = None [ObjectifiedElement]
        a = 'nice string!' [StringElement]
          * py:pytype = 'str'
    
    >>> root.a = True
    >>> print(objectify.dump(root))
    root = None [ObjectifiedElement]
        a = True [BoolElement]
          * py:pytype = 'bool'
    
    >>> root.a = [1, 2, 3]
    >>> print(objectify.dump(root))
    root = None [ObjectifiedElement]
        a = 1 [IntElement]
          * py:pytype = 'int'
        a = 2 [IntElement]
          * py:pytype = 'int'
        a = 3 [IntElement]
          * py:pytype = 'int'
    
    >>> root.a = (1, 2, 3)
    >>> print(objectify.dump(root))
    root = None [ObjectifiedElement]
        a = 1 [IntElement]
          * py:pytype = 'int'
        a = 2 [IntElement]
          * py:pytype = 'int'
        a = 3 [IntElement]
          * py:pytype = 'int'
    ```

=== "英文"

    **Recursive tree dump**

    To see the data types that are currently used, you can call the module level dump() function that returns a recursive string representation for elements:

    ```pycon
    >>> root = objectify.fromstring("""
    ... <root xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
    ...   <a attr1="foo" attr2="bar">1</a>
    ...   <a>1.2</a>
    ...   <b>1</b>
    ...   <b>true</b>
    ...   <c>what?</c>
    ...   <d xsi:nil="true"/>
    ... </root>
    ... """)
    
    >>> print(objectify.dump(root))
    root = None [ObjectifiedElement]
        a = 1 [IntElement]
          * attr1 = 'foo'
          * attr2 = 'bar'
        a = 1.2 [FloatElement]
        b = 1 [IntElement]
        b = True [BoolElement]
        c = 'what?' [StringElement]
        d = None [NoneElement]
          * xsi:nil = 'true'
    ```

    You can freely switch between different types for the same child:

    ```pycon
    >>> root = objectify.fromstring("<root><a>5</a></root>")
    >>> print(objectify.dump(root))
    root = None [ObjectifiedElement]
        a = 5 [IntElement]
    
    >>> root.a = 'nice string!'
    >>> print(objectify.dump(root))
    root = None [ObjectifiedElement]
        a = 'nice string!' [StringElement]
          * py:pytype = 'str'
    
    >>> root.a = True
    >>> print(objectify.dump(root))
    root = None [ObjectifiedElement]
        a = True [BoolElement]
          * py:pytype = 'bool'
    
    >>> root.a = [1, 2, 3]
    >>> print(objectify.dump(root))
    root = None [ObjectifiedElement]
        a = 1 [IntElement]
          * py:pytype = 'int'
        a = 2 [IntElement]
          * py:pytype = 'int'
        a = 3 [IntElement]
          * py:pytype = 'int'
    
    >>> root.a = (1, 2, 3)
    >>> print(objectify.dump(root))
    root = None [ObjectifiedElement]
        a = 1 [IntElement]
          * py:pytype = 'int'
        a = 2 [IntElement]
          * py:pytype = 'int'
        a = 3 [IntElement]
          * py:pytype = 'int'
    ```

### 元素的递归字符串表示

=== "中文"

    通常，元素使用 **lxml.etree** 提供的 `str()` 标准字符串表示形式。 您可以为对象化元素启用漂亮的打印表示，如下所示：

    ```pycon
    >>> objectify.enable_recursive_str()

    >>> root = objectify.fromstring("""
    ... <root xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
    ...   <a attr1="foo" attr2="bar">1</a>
    ...   <a>1.2</a>
    ...   <b>1</b>
    ...   <b>true</b>
    ...   <c>what?</c>
    ...   <d xsi:nil="true"/>
    ... </root>
    ... """)
    
    >>> print(str(root))
    root = None [ObjectifiedElement]
        a = 1 [IntElement]
          * attr1 = 'foo'
          * attr2 = 'bar'
        a = 1.2 [FloatElement]
        b = 1 [IntElement]
        b = True [BoolElement]
        c = 'what?' [StringElement]
        d = None [NoneElement]
          * xsi:nil = 'true'
    ```

    可以用相同的方式关闭此行为：

    ```pycon
    >>> objectify.enable_recursive_str(False)
    ```

=== "英文"

    **Recursive string representation of elements**

    Normally, elements use the standard string representation for str() that is provided by lxml.etree. You can enable a pretty-print representation for objectify elements like this:

    ```pycon
    >>> objectify.enable_recursive_str()

    >>> root = objectify.fromstring("""
    ... <root xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
    ...   <a attr1="foo" attr2="bar">1</a>
    ...   <a>1.2</a>
    ...   <b>1</b>
    ...   <b>true</b>
    ...   <c>what?</c>
    ...   <d xsi:nil="true"/>
    ... </root>
    ... """)
    
    >>> print(str(root))
    root = None [ObjectifiedElement]
        a = 1 [IntElement]
          * attr1 = 'foo'
          * attr2 = 'bar'
        a = 1.2 [FloatElement]
        b = 1 [IntElement]
        b = True [BoolElement]
        c = 'what?' [StringElement]
        d = None [NoneElement]
          * xsi:nil = 'true'
    ```

    This behaviour can be switched off in the same way:

    ```pycon
    >>> objectify.enable_recursive_str(False)
    ```

## 如何匹配数据类型

=== "中文"

    Objectify 使用两种不同类型的元素。 结构元素（或树元素）表示对象树结构。 数据元素表示叶节点处的数据容器。 您可以使用[objectify.Element()](https://lxml.de/apidoc/lxml.objectify.html#lxml.objectify.Element)工厂显式创建树元素，并使用 [objectify.DataElement()](https://lxml.de/apidoc/lxml.objectify.html#lxml.objectify.DataElement) 工厂显式创建数据元素。
    
    创建 Element 对象时，**lxml.objectify** 必须确定要为它们使用哪个实现类。 这对于树元素来说相对容易，而对于数据元素则不太容易。 算法如下：

    1. 如果元素有子元素，则使用默认的树类。
    2. 如果元素定义为 `xsi:nil`，请使用 **[NoneElement](https://lxml.de/apidoc/lxml.objectify.html#lxml.objectify.NoneElement)** 类。
    3. 如果给出了“Python 类型注解”属性，请使用它来确定元素类，请参见下文。
    4. 如果给出了 XML Schema xsi:type 提示，请使用它来确定元素类，请参见下文。
    5. 尝试通过反复试验从文本内容类型确定元素类。
    6. 如果元素是根节点，则使用默认树类。
    7. 否则，对空数据类使用默认类。

    您可以在设置时更改树元素和空数据元素的默认类。 [ObjectifyElementClassLookup()](https://lxml.de/apidoc/lxml.objectify.html#lxml.objectify.ObjectifyElementClassLookup) 调用接受两个关键字参数 `tree_class` 和 `empty_data_class`，它们确定在这些情况下使用的 [Element](https://lxml.de/apidoc/lxml.objectify.html#lxml.objectify.Element) 类。 默认情况下，`tree_class` 是一个名为[ObjectifiedElement](https://lxml.de/apidoc/lxml.objectify.html#lxml.objectify.ObjectifiedElement) 的类，`empty_data_class` 是一个 [StringElement](https://lxml.de/apidoc/lxml.objectify.html#lxml.objectify.StringElement) 。

=== "英文"

    **How data types are matched**

    Objectify uses two different types of Elements. Structural Elements (or tree Elements) represent the object tree structure. Data Elements represent the data containers at the leafs. You can explicitly create tree Elements with the `objectify.Element()` factory and data Elements with the `objectify.DataElement()` factory.
    
    When Element objects are created, lxml.objectify must determine which implementation class to use for them. This is relatively easy for tree Elements and less so for data Elements. The algorithm is as follows:

    1. If an element has children, use the default tree class.
    2. If an element is defined as xsi:nil, use the NoneElement class.
    3. If a "Python type hint" attribute is given, use this to determine the element class, see below.
    4. If an XML Schema xsi:type hint is given, use this to determine the element class, see below.
    5. Try to determine the element class from the text content type by trial and error.
    6. If the element is a root node then use the default tree class.
    7. Otherwise, use the default class for empty data classes.
    
    You can change the default classes for tree Elements and empty data Elements at setup time. The `ObjectifyElementClassLookup()` call accepts two keyword arguments, `tree_class` and `empty_data_class`, that determine the Element classes used in these cases. By default, tree_class is a class called `ObjectifiedElement` and `empty_data_class` is a StringElement.

### 类型注解

=== "中文"

    "类型注解" 机制部署定义为 `lxml.objectify.PYTYPE_ATTRIBUTE` 的 XML 属性。 它可能包含以下任何字符串值：`int`、`long`、`float`、`str`、`unicode`、`NoneType`：

    ```pycon
    >>> print(objectify.PYTYPE_ATTRIBUTE)
    {http://codespeak.net/lxml/objectify/pytype}pytype
    >>> ns, name = objectify.PYTYPE_ATTRIBUTE[1:].split('}')

    >>> root = objectify.fromstring("""\
    ... <root xmlns:py='%s'>
    ...   <a py:pytype='str'>5</a>
    ...   <b py:pytype='int'>5</b>
    ...   <c py:pytype='NoneType' />
    ... </root>
    ... """ % ns)

    >>> print(root.a + 10)
    510
    >>> print(root.b + 10)
    15
    >>> print(root.c)
    None
    ```

    请注意，您可以通过 [set_pytype_attribute_tag(tag)](https://lxml.de/apidoc/lxml.objectify.html#lxml.objectify.set_pytype_attribute_tag) 模块函数更改用于此属性的名称和命名空间，以防您的应用程序需要。 还有一个实用函数 [annotate()](https://lxml.de/apidoc/lxml.objectify.html#lxml.objectify.annotate) 可以为树的元素递归生成此属性：

    ```pycon
    >>> root = objectify.fromstring("<root><a>test</a><b>5</b></root>")
    >>> print(objectify.dump(root))
    root = None [ObjectifiedElement]
        a = 'test' [StringElement]
        b = 5 [IntElement]
    
    >>> objectify.annotate(root)
    
    >>> print(objectify.dump(root))
    root = None [ObjectifiedElement]
        a = 'test' [StringElement]
          * py:pytype = 'str'
        b = 5 [IntElement]
          * py:pytype = 'int'
    ```

=== "英文"

    **Type annotations**

    The "type hint" mechanism deploys an XML attribute defined as `lxml.objectify.PYTYPE_ATTRIBUTE`. It may contain any of the following string values: int, long, float, str, unicode, NoneType:

    ```pycon
    >>> print(objectify.PYTYPE_ATTRIBUTE)
    {http://codespeak.net/lxml/objectify/pytype}pytype
    >>> ns, name = objectify.PYTYPE_ATTRIBUTE[1:].split('}')
    
    >>> root = objectify.fromstring("""\
    ... <root xmlns:py='%s'>
    ...   <a py:pytype='str'>5</a>
    ...   <b py:pytype='int'>5</b>
    ...   <c py:pytype='NoneType' />
    ... </root>
    ... """ % ns)
    
    >>> print(root.a + 10)
    510
    >>> print(root.b + 10)
    15
    >>> print(root.c)
    None
    ```

    Note that you can change the name and namespace used for this attribute through the set_pytype_attribute_tag(tag) module function, in case your application ever needs to. There is also a utility function annotate() that recursively generates this attribute for the elements of a tree:

    ```pycon
    >>> root = objectify.fromstring("<root><a>test</a><b>5</b></root>")
    >>> print(objectify.dump(root))
    root = None [ObjectifiedElement]
        a = 'test' [StringElement]
        b = 5 [IntElement]
    
    >>> objectify.annotate(root)
    
    >>> print(objectify.dump(root))
    root = None [ObjectifiedElement]
        a = 'test' [StringElement]
          * py:pytype = 'str'
        b = 5 [IntElement]
          * py:pytype = 'int'
    ```

### XML Schema的数据类型注释

=== "中文"

    指定数据类型信息的第二种方法使用 XML Schema类型作为元素注解。 **Objectify** 知道那些可以映射到普通 Python 类型的类型：

    ```pycon
    >>> root = objectify.fromstring('''\
    ...    <root xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    ...          xmlns:xsd="http://www.w3.org/2001/XMLSchema">
    ...      <d xsi:type="xsd:double">5</d>
    ...      <i xsi:type="xsd:int"   >5</i>
    ...      <s xsi:type="xsd:string">5</s>
    ...    </root>
    ...    ''')
    >>> print(objectify.dump(root))
    root = None [ObjectifiedElement]
        d = 5.0 [FloatElement]
          * xsi:type = 'xsd:double'
        i = 5 [IntElement]
          * xsi:type = 'xsd:int'
        s = '5' [StringElement]
          * xsi:type = 'xsd:string'
    ```

    同样，有一个实用函数 [xsiannotate()](https://lxml.de/apidoc/lxml.objectify.html#lxml.objectify.xsiannotate) 可以递归地为树的元素生成**“xsi:type”** 属性：

    ```pycon
    >>> root = objectify.fromstring('''\
    ...    <root><a>test</a><b>5</b><c>true</c></root>
    ...    ''')
    >>> print(objectify.dump(root))
    root = None [ObjectifiedElement]
        a = 'test' [StringElement]
        b = 5 [IntElement]
        c = True [BoolElement]
    
    >>> objectify.xsiannotate(root)
    
    >>> print(objectify.dump(root))
    root = None [ObjectifiedElement]
        a = 'test' [StringElement]
          * xsi:type = 'xsd:string'
        b = 5 [IntElement]
          * xsi:type = 'xsd:integer'
        c = True [BoolElement]
          * xsi:type = 'xsd:boolean'
    ```

    但请注意，[xsiannotate()](https://lxml.de/apidoc/lxml.objectify.html#lxml.objectify.xsiannotate) 将始终使用为任何给定 Python 类型定义的第一个 XML 架构数据类型，另请参阅[**定义附加数据类**](#定义附加数据类)(Defining additional data classes)。
    
    实用函数 [deannotate()](https://lxml.de/apidoc/lxml.objectify.html#lxml.objectify.deannotate){target="_balnk"} 可用于删除 {== py:pytype ==} 和/或 {== xsi:type ==} 信息：
    
    ```pycon
    >>> root = objectify.fromstring('''\
    ... <root xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    ...       xmlns:xsd="http://www.w3.org/2001/XMLSchema">
    ...   <d xsi:type="xsd:double">5</d>
    ...   <i xsi:type="xsd:int"   >5</i>
    ...   <s xsi:type="xsd:string">5</s>
    ... </root>''')
    >>> objectify.annotate(root)
    >>> print(objectify.dump(root))
    root = None [ObjectifiedElement]
        d = 5.0 [FloatElement]
          * py:pytype = 'float'
          * xsi:type = 'xsd:double'
        i = 5 [IntElement]
          * py:pytype = 'int'
          * xsi:type = 'xsd:int'
        s = '5' [StringElement]
          * py:pytype = 'str'
          * xsi:type = 'xsd:string'
    >>> objectify.deannotate(root)
    >>> print(objectify.dump(root))
    root = None [ObjectifiedElement]
        d = 5 [IntElement]
        i = 5 [IntElement]
        s = 5 [IntElement]
    ```

    您可以使用关键字参数 `pytype`（默认值：`True`）和 `xsi`（默认值：`True`）来控制应取消注释哪些类型属性。 [deannotate()](https://lxml.de/apidoc/lxml.objectify.html#lxml.objectify.deannotate){target="_balnk"} 还可以通过设置 `xsi_nil=True` （默认值：`False`）来删除 `xsi:nil` 属性：

    ```pycon
    >>> root = objectify.fromstring('''\
    ... <root xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    ...       xmlns:xsd="http://www.w3.org/2001/XMLSchema">
    ...   <d xsi:type="xsd:double">5</d>
    ...   <i xsi:type="xsd:int"   >5</i>
    ...   <s xsi:type="xsd:string">5</s>
    ...   <n xsi:nil="true"/>
    ... </root>''')
    >>> objectify.annotate(root)
    >>> print(objectify.dump(root))
    root = None [ObjectifiedElement]
        d = 5.0 [FloatElement]
          * py:pytype = 'float'
          * xsi:type = 'xsd:double'
        i = 5 [IntElement]
          * py:pytype = 'int'
          * xsi:type = 'xsd:int'
        s = '5' [StringElement]
          * py:pytype = 'str'
          * xsi:type = 'xsd:string'
        n = None [NoneElement]
          * py:pytype = 'NoneType'
          * xsi:nil = 'true'
    >>> objectify.deannotate(root, xsi_nil=True)
    >>> print(objectify.dump(root))
    root = None [ObjectifiedElement]
        d = 5 [IntElement]
        i = 5 [IntElement]
        s = 5 [IntElement]
        n = u'' [StringElement]
    ```

    请注意，默认情况下 [deannotate()](https://lxml.de/apidoc/lxml.objectify.html#lxml.objectify.deannotate){target="_balnk"} 不会删除 `pytype` 命名空间的命名空间声明。 要删除它们，并通常清理文档中的命名空间声明（通常在完成整个处理时），请传递选项 `cleanup_namespaces=True`。 此选项是 `lxml 2.3.2` 中的新增选项。 在旧版本中，请改用函数 [lxml.etree.cleanup_namespaces()](https://lxml.de/apidoc/lxml.etree.html#lxml.etree.cleanup_namespaces){target="_blank"}。

=== "英文"

    **XML Schema datatype annotation**

    A second way of specifying data type information uses XML Schema types as element annotations. Objectify knows those that can be mapped to normal Python types:

    ```pycon
    >>> root = objectify.fromstring('''\
    ...    <root xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    ...          xmlns:xsd="http://www.w3.org/2001/XMLSchema">
    ...      <d xsi:type="xsd:double">5</d>
    ...      <i xsi:type="xsd:int"   >5</i>
    ...      <s xsi:type="xsd:string">5</s>
    ...    </root>
    ...    ''')
    >>> print(objectify.dump(root))
    root = None [ObjectifiedElement]
        d = 5.0 [FloatElement]
          * xsi:type = 'xsd:double'
        i = 5 [IntElement]
          * xsi:type = 'xsd:int'
        s = '5' [StringElement]
          * xsi:type = 'xsd:string'
    ```

    Again, there is a utility function xsiannotate() that recursively generates the "xsi:type" attribute for the elements of a tree:

    ```pycon
    >>> root = objectify.fromstring('''\
    ...    <root><a>test</a><b>5</b><c>true</c></root>
    ...    ''')
    >>> print(objectify.dump(root))
    root = None [ObjectifiedElement]
        a = 'test' [StringElement]
        b = 5 [IntElement]
        c = True [BoolElement]
    
    >>> objectify.xsiannotate(root)
    
    >>> print(objectify.dump(root))
    root = None [ObjectifiedElement]
        a = 'test' [StringElement]
          * xsi:type = 'xsd:string'
        b = 5 [IntElement]
          * xsi:type = 'xsd:integer'
        c = True [BoolElement]
          * xsi:type = 'xsd:boolean'
    ```

    Note, however, that xsiannotate() will always use the first XML Schema datatype that is defined for any given Python type, see also **Defining additional data classes**.
    
    The utility function deannotate() can be used to get rid of 'py:pytype' and/or 'xsi:type' information:
    
    ```pycon
    >>> root = objectify.fromstring('''\
    ... <root xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    ...       xmlns:xsd="http://www.w3.org/2001/XMLSchema">
    ...   <d xsi:type="xsd:double">5</d>
    ...   <i xsi:type="xsd:int"   >5</i>
    ...   <s xsi:type="xsd:string">5</s>
    ... </root>''')
    >>> objectify.annotate(root)
    >>> print(objectify.dump(root))
    root = None [ObjectifiedElement]
        d = 5.0 [FloatElement]
          * py:pytype = 'float'
          * xsi:type = 'xsd:double'
        i = 5 [IntElement]
          * py:pytype = 'int'
          * xsi:type = 'xsd:int'
        s = '5' [StringElement]
          * py:pytype = 'str'
          * xsi:type = 'xsd:string'
    >>> objectify.deannotate(root)
    >>> print(objectify.dump(root))
    root = None [ObjectifiedElement]
        d = 5 [IntElement]
        i = 5 [IntElement]
        s = 5 [IntElement]
    ```

    You can control which type attributes should be de-annotated with the keyword arguments 'pytype' (default: True) and 'xsi' (default: True). deannotate() can also remove 'xsi:nil' attributes by setting 'xsi_nil=True' (default: False):

    ```pycon
    >>> root = objectify.fromstring('''\
    ... <root xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    ...       xmlns:xsd="http://www.w3.org/2001/XMLSchema">
    ...   <d xsi:type="xsd:double">5</d>
    ...   <i xsi:type="xsd:int"   >5</i>
    ...   <s xsi:type="xsd:string">5</s>
    ...   <n xsi:nil="true"/>
    ... </root>''')
    >>> objectify.annotate(root)
    >>> print(objectify.dump(root))
    root = None [ObjectifiedElement]
        d = 5.0 [FloatElement]
          * py:pytype = 'float'
          * xsi:type = 'xsd:double'
        i = 5 [IntElement]
          * py:pytype = 'int'
          * xsi:type = 'xsd:int'
        s = '5' [StringElement]
          * py:pytype = 'str'
          * xsi:type = 'xsd:string'
        n = None [NoneElement]
          * py:pytype = 'NoneType'
          * xsi:nil = 'true'
    >>> objectify.deannotate(root, xsi_nil=True)
    >>> print(objectify.dump(root))
    root = None [ObjectifiedElement]
        d = 5 [IntElement]
        i = 5 [IntElement]
        s = 5 [IntElement]
        n = u'' [StringElement]
    ```

    Note that deannotate() does not remove the namespace declarations of the pytype namespace by default. To remove them as well, and to generally clean up the namespace declarations in the document (usually when done with the whole processing), pass the option `cleanup_namespaces=True`. This option is new in lxml 2.3.2. In older versions, use the function `lxml.etree.cleanup_namespaces()` instead.

### DataElement 工厂

=== "中文"

    为了方便起见， [DataElement()](https://lxml.de/apidoc/lxml.objectify.html#lxml.objectify.DataElement){target="_blank"} 工厂一步创建一个具有 Python 值的元素。 您可以传递所需的 **Python 类型名称**或 **XSI 类型名称**：

    ```pycon
    >>> root = objectify.Element("root")
    >>> root.x = objectify.DataElement(5, _pytype="int")
    >>> print(objectify.dump(root))
    root = None [ObjectifiedElement]
        x = 5 [IntElement]
          * py:pytype = 'int'
    
    >>> root.x = objectify.DataElement(5, _pytype="str", myattr="someval")
    >>> print(objectify.dump(root))
    root = None [ObjectifiedElement]
        x = '5' [StringElement]
          * myattr = 'someval'
          * py:pytype = 'str'
    
    >>> root.x = objectify.DataElement(5, _xsi="integer")
    >>> print(objectify.dump(root))
    root = None [ObjectifiedElement]
        x = 5 [IntElement]
          * py:pytype = 'int'
          * xsi:type = 'xsd:integer'
    ```

    **XML Schema 类型** 驻留在 XML 模式命名空间中，因此 [DataElement()](https://lxml.de/apidoc/lxml.objectify.html#lxml.objectify.DataElement){target="_blank"} 尝试为您正确添加 `xsi:type` 属性值前缀：

    ```pycon
    >>> root = objectify.Element("root")
    >>> root.s = objectify.DataElement(5, _xsi="string")
    
    >>> objectify.deannotate(root, xsi=False)
    >>> print(etree.tostring(root, pretty_print=True))
    <root xmlns:py="http://codespeak.net/lxml/objectify/pytype" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
      <s xsi:type="xsd:string">5</s>
    </root>
    ```

    [DataElement()](https://lxml.de/apidoc/lxml.objectify.html#lxml.objectify.DataElement){target="_blank"} 使用默认的 `nsmap` 来设置这些前缀：

    ```pycon
    >>> el = objectify.DataElement('5', _xsi='string')
    >>> namespaces = list(el.nsmap.items())
    >>> namespaces.sort()
    >>> for prefix, namespace in namespaces:
    ...     print("%s - %s" % (prefix, namespace))
    py - http://codespeak.net/lxml/objectify/pytype
    xsd - http://www.w3.org/2001/XMLSchema
    xsi - http://www.w3.org/2001/XMLSchema-instance
    
    >>> print(el.get("{http://www.w3.org/2001/XMLSchema-instance}type"))
    xsd:string
    ```

    虽然您可以设置自定义命名空间前缀，但如果您选择这样做，则必须提供有效的命名空间信息：

    ```pycon
    >>> el = objectify.DataElement('5', _xsi='foo:string',
    ...          nsmap={'foo': 'http://www.w3.org/2001/XMLSchema'})
    >>> namespaces = list(el.nsmap.items())
    >>> namespaces.sort()
    >>> for prefix, namespace in namespaces:
    ...     print("%s - %s" % (prefix, namespace))
    foo - http://www.w3.org/2001/XMLSchema
    py - http://codespeak.net/lxml/objectify/pytype
    xsi - http://www.w3.org/2001/XMLSchema-instance
    
    >>> print(el.get("{http://www.w3.org/2001/XMLSchema-instance}type"))
    foo:string
    ```

    请注意 lxml 是如何为 XML Schema 实例命名空间选择默认前缀的。 我们可以重写它，如下例所示：

    ```pycon
    >>> el = objectify.DataElement('5', _xsi='foo:string',
    ...          nsmap={'foo': 'http://www.w3.org/2001/XMLSchema',
    ...                 'myxsi': 'http://www.w3.org/2001/XMLSchema-instance'})
    >>> namespaces = list(el.nsmap.items())
    >>> namespaces.sort()
    >>> for prefix, namespace in namespaces:
    ...     print("%s - %s" % (prefix, namespace))
    foo - http://www.w3.org/2001/XMLSchema
    myxsi - http://www.w3.org/2001/XMLSchema-instance
    py - http://codespeak.net/lxml/objectify/pytype
    
    >>> print(el.get("{http://www.w3.org/2001/XMLSchema-instance}type"))
    foo:string
    ```

    如果同一命名空间使用了不同的命名空间前缀，则必须小心。 命名空间信息被合并以避免在向树添加新子元素时出现重复定义，但此机制不适用于属性值的前缀：

    ```pycon
    >>> root = objectify.fromstring("""<root xmlns:schema="http://www.w3.org/2001/XMLSchema"/>""")
    >>> print(etree.tostring(root, pretty_print=True))
    <root xmlns:schema="http://www.w3.org/2001/XMLSchema"/>
    
    >>> s = objectify.DataElement("17", _xsi="string")
    >>> print(etree.tostring(s, pretty_print=True))
    <value xmlns:py="http://codespeak.net/lxml/objectify/pytype" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" py:pytype="str" xsi:type="xsd:string">17</value>
    
    >>> root.s = s
    >>> print(etree.tostring(root, pretty_print=True))
    <root xmlns:schema="http://www.w3.org/2001/XMLSchema">
      <s xmlns:py="http://codespeak.net/lxml/objectify/pytype" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" py:pytype="str" xsi:type="xsd:string">17</s>
    </root>
    ```

    如果您选择偏离标准前缀，则您有责任修复属性值的前缀。 对 `xsi:type` 属性执行此操作的一种便捷方法是使用 [xsiannotate()](https://lxml.de/apidoc/lxml.objectify.html#lxml.objectify.xsiannotate){target="_blank"} 工具：

    ```pycon
    >>> objectify.xsiannotate(root)
    >>> print(etree.tostring(root, pretty_print=True))
    <root xmlns:schema="http://www.w3.org/2001/XMLSchema">
      <s xmlns:py="http://codespeak.net/lxml/objectify/pytype" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" py:pytype="str" xsi:type="schema:string">17</s>
    </root>
    ```

    当然，在构建对象化树时，不鼓励对同一个命名空间使用不同的前缀。

=== "英文"

    **The DataElement factory**

    For convenience, the DataElement() factory creates an Element with a Python value in one step. You can pass the required Python type name or the XSI type name:

    ```pycon
    >>> root = objectify.Element("root")
    >>> root.x = objectify.DataElement(5, _pytype="int")
    >>> print(objectify.dump(root))
    root = None [ObjectifiedElement]
        x = 5 [IntElement]
          * py:pytype = 'int'
    
    >>> root.x = objectify.DataElement(5, _pytype="str", myattr="someval")
    >>> print(objectify.dump(root))
    root = None [ObjectifiedElement]
        x = '5' [StringElement]
          * myattr = 'someval'
          * py:pytype = 'str'
    
    >>> root.x = objectify.DataElement(5, _xsi="integer")
    >>> print(objectify.dump(root))
    root = None [ObjectifiedElement]
        x = 5 [IntElement]
          * py:pytype = 'int'
          * xsi:type = 'xsd:integer'
    ```

    XML Schema types reside in the XML schema namespace thus DataElement() tries to correctly prefix the xsi:type attribute value for you:

    ```pycon
    >>> root = objectify.Element("root")
    >>> root.s = objectify.DataElement(5, _xsi="string")
    
    >>> objectify.deannotate(root, xsi=False)
    >>> print(etree.tostring(root, pretty_print=True))
    <root xmlns:py="http://codespeak.net/lxml/objectify/pytype" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
      <s xsi:type="xsd:string">5</s>
    </root>
    ```

    `DataElement()` uses a default nsmap to set these prefixes:

    ```pycon
    >>> el = objectify.DataElement('5', _xsi='string')
    >>> namespaces = list(el.nsmap.items())
    >>> namespaces.sort()
    >>> for prefix, namespace in namespaces:
    ...     print("%s - %s" % (prefix, namespace))
    py - http://codespeak.net/lxml/objectify/pytype
    xsd - http://www.w3.org/2001/XMLSchema
    xsi - http://www.w3.org/2001/XMLSchema-instance
    
    >>> print(el.get("{http://www.w3.org/2001/XMLSchema-instance}type"))
    xsd:string
    ```

    While you can set custom namespace prefixes, it is necessary to provide valid namespace information if you choose to do so:

    ```pycon
    >>> el = objectify.DataElement('5', _xsi='foo:string',
    ...          nsmap={'foo': 'http://www.w3.org/2001/XMLSchema'})
    >>> namespaces = list(el.nsmap.items())
    >>> namespaces.sort()
    >>> for prefix, namespace in namespaces:
    ...     print("%s - %s" % (prefix, namespace))
    foo - http://www.w3.org/2001/XMLSchema
    py - http://codespeak.net/lxml/objectify/pytype
    xsi - http://www.w3.org/2001/XMLSchema-instance
    
    >>> print(el.get("{http://www.w3.org/2001/XMLSchema-instance}type"))
    foo:string
    ```

    Note how lxml chose a default prefix for the XML Schema Instance namespace. We can override it as in the following example:

    ```pycon
    >>> el = objectify.DataElement('5', _xsi='foo:string',
    ...          nsmap={'foo': 'http://www.w3.org/2001/XMLSchema',
    ...                 'myxsi': 'http://www.w3.org/2001/XMLSchema-instance'})
    >>> namespaces = list(el.nsmap.items())
    >>> namespaces.sort()
    >>> for prefix, namespace in namespaces:
    ...     print("%s - %s" % (prefix, namespace))
    foo - http://www.w3.org/2001/XMLSchema
    myxsi - http://www.w3.org/2001/XMLSchema-instance
    py - http://codespeak.net/lxml/objectify/pytype
    
    >>> print(el.get("{http://www.w3.org/2001/XMLSchema-instance}type"))
    foo:string
    ```

    Care must be taken if different namespace prefixes have been used for the same namespace. Namespace information gets merged to avoid duplicate definitions when adding a new sub-element to a tree, but this mechanism does not adapt the prefixes of attribute values:

    ```pycon
    >>> root = objectify.fromstring("""<root xmlns:schema="http://www.w3.org/2001/XMLSchema"/>""")
    >>> print(etree.tostring(root, pretty_print=True))
    <root xmlns:schema="http://www.w3.org/2001/XMLSchema"/>
    
    >>> s = objectify.DataElement("17", _xsi="string")
    >>> print(etree.tostring(s, pretty_print=True))
    <value xmlns:py="http://codespeak.net/lxml/objectify/pytype" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" py:pytype="str" xsi:type="xsd:string">17</value>
    
    >>> root.s = s
    >>> print(etree.tostring(root, pretty_print=True))
    <root xmlns:schema="http://www.w3.org/2001/XMLSchema">
      <s xmlns:py="http://codespeak.net/lxml/objectify/pytype" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" py:pytype="str" xsi:type="xsd:string">17</s>
    </root>
    ```

    It is your responsibility to fix the prefixes of attribute values if you choose to deviate from the standard prefixes. A convenient way to do this for xsi:type attributes is to use the xsiannotate() utility:

    ```pycon
    >>> objectify.xsiannotate(root)
    >>> print(etree.tostring(root, pretty_print=True))
    <root xmlns:schema="http://www.w3.org/2001/XMLSchema">
      <s xmlns:py="http://codespeak.net/lxml/objectify/pytype" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" py:pytype="str" xsi:type="schema:string">17</s>
    </root>
    ```

    Of course, it is discouraged to use different prefixes for one and the same namespace when building up an objectify tree.

### 定义附加数据类

=== "中文"

    您可以将其他数据类插入 objectify，其使用方式与预定义类型完全相同。 数据类可以直接从 [ObjectifiedDataElement](https://lxml.de/apidoc/lxml.objectify.html#lxml.objectify.ObjectifiedDataElement){target="_balnk"} 继承，也可以从 [NumberElement](https://lxml.de/apidoc/lxml.objectify.html#lxml.objectify.NumberElement){target="_blank"} 或 [BoolElement](https://lxml.de/apidoc/lxml.objectify.html#lxml.objectify.BoolElement){target="_blank"} 等专用类之一继承。 数字类型需要初始调用 `NumberElement` 的 `self._setValueParser(function)` 方法来设置其类型转换函数（字符串 ->  Python 数字类型）。 此调用应放入 `element _init()` 方法中。
    
    数据类的注册使用 [PyType](https://lxml.de/apidoc/lxml.objectify.html#lxml.objectify.PyType){target="_blank"} 类：

    ```pycon
    >>> class ChristmasDate(objectify.ObjectifiedDataElement):
    ...     def call_santa(self):
    ...         print("Ho ho ho!")
    
    >>> def checkChristmasDate(date_string):
    ...     if not date_string.startswith('24.12.'):
    ...         raise ValueError # or TypeError
    
    >>> xmas_type = objectify.PyType('date', checkChristmasDate, ChristmasDate)
    ```

    `PyType` 构造函数接受字符串类型名称、(可选的)可调用类型检查和自定义数据类。如果提供了类型检查，则必须接受字符串作为参数，如果不能处理字符串值，则引发 ValueError 或 TypeError。

    如果一个元素带有一个 py: pytype 属性来表示它的数据类型，或者在没有这样一个属性的情况下，如果给定的类型检查调用在应用到元素文本时没有引发 ValueError/TypeError 异常，则使用 PyType。
    
    如果需要，您还可以在 XML 架构类型名称下注册此类型：

    ```pycon
    >>> xmas_type.xmlSchemaTypes = ("date",)
    ```

    如果元素具有指定其数据类型的 `xsi:type` 属性，则将考虑 XML 架构类型。 上面的行将 `XSD` 类型日期绑定到新定义的 Python 类型。 请注意，这必须在下一步注册类型之前完成。 然后你就可以使用它：
    
    ```pycon
    >>> xmas_type.register()

    >>> root = objectify.fromstring(
    ...             "<root><a>24.12.2000</a><b>12.24.2000</b></root>")
    >>> root.a.call_santa()
    Ho ho ho!
    >>> root.b.call_santa()
    Traceback (most recent call last):
      ...
    AttributeError: no such child: call_santa
    ```

    如果需要指定类型检查函数之间的依赖关系，可以通过 `register()` 方法的 `before` 和 `after` 关键字参数传递一系列类型名称。 然后，`PyType` 将尝试在相应类型之前或之后注册自身，只要它们当前已注册即可。 请注意，这仅影响注册时当前注册的类型。 稍后注册的类型不会关心已注册类型的依赖关系。

    如果您提供 XML Schema 类型信息，这将覆盖上面定义的类型检查函数：

    ```pycon
    >>> root = objectify.fromstring('''\
    ...    <root xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
    ...      <a xsi:type="date">12.24.2000</a>
    ...    </root>
    ...    ''')
    >>> print(root.a)
    12.24.2000
    >>> root.a.call_santa()
    Ho ho ho!
    ```

    要取消注册类型，请调用其 `unregister()` 方法：

    ```pycon
    >>> root.a.call_santa()
    Ho ho ho!
    >>> xmas_type.unregister()
    >>> root.a.call_santa()
    Traceback (most recent call last):
      ...
    AttributeError: no such child: call_santa
    ```

    但请注意，这并不立即适用于已经存在 Python 引用的元素。 只有在所有引用消失并且 Python 对象被垃圾收集后，它们的 Python 类才会被更改。

=== "英文"

    **Defining additional data classes**

    You can plug additional data classes into objectify that will be used in exactly the same way as the predefined types. Data classes can either inherit from ObjectifiedDataElement directly or from one of the specialised classes like NumberElement or BoolElement. The numeric types require an initial call to the NumberElement method self._setValueParser(function) to set their type conversion function (string -> numeric Python type). This call should be placed into the element _init() method.
    
    The registration of data classes uses the PyType class:

    ```pycon
    >>> class ChristmasDate(objectify.ObjectifiedDataElement):
    ...     def call_santa(self):
    ...         print("Ho ho ho!")
    
    >>> def checkChristmasDate(date_string):
    ...     if not date_string.startswith('24.12.'):
    ...         raise ValueError # or TypeError
    
    >>> xmas_type = objectify.PyType('date', checkChristmasDate, ChristmasDate)
    ```

    The PyType constructor takes a string type name, an (optional) callable type check and the custom data class. If a type check is provided it must accept a string as argument and raise ValueError or TypeError if it cannot handle the string value.

    PyTypes are used if an element carries a py:pytype attribute denoting its data type or, in absence of such an attribute, if the given type check callable does not raise a ValueError/TypeError exception when applied to the element text.
    
    If you want, you can also register this type under an XML Schema type name:

    ```pycon
    >>> xmas_type.xmlSchemaTypes = ("date",)
    ```
    XML Schema types will be considered if the element has an xsi:type attribute that specifies its data type. The line above binds the XSD type date to the newly defined Python type. Note that this must be done before the next step, which is to register the type. Then you can use it:
    
    ```pycon
    >>> xmas_type.register()

    >>> root = objectify.fromstring(
    ...             "<root><a>24.12.2000</a><b>12.24.2000</b></root>")
    >>> root.a.call_santa()
    Ho ho ho!
    >>> root.b.call_santa()
    Traceback (most recent call last):
      ...
    AttributeError: no such child: call_santa
    ```

    If you need to specify dependencies between the type check functions, you can pass a sequence of type names through the before and after keyword arguments of the register() method. The PyType will then try to register itself before or after the respective types, as long as they are currently registered. Note that this only impacts the currently registered types at the time of registration. Types that are registered later on will not care about the dependencies of already registered types.

    If you provide XML Schema type information, this will override the type check function defined above:

    ```pycon
    >>> root = objectify.fromstring('''\
    ...    <root xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
    ...      <a xsi:type="date">12.24.2000</a>
    ...    </root>
    ...    ''')
    >>> print(root.a)
    12.24.2000
    >>> root.a.call_santa()
    Ho ho ho!
    ```

    To unregister a type, call its unregister() method:

    ```pycon
    >>> root.a.call_santa()
    Ho ho ho!
    >>> xmas_type.unregister()
    >>> root.a.call_santa()
    Traceback (most recent call last):
      ...
    AttributeError: no such child: call_santa
    ```

    Be aware, though, that this does not immediately apply to elements to which there already is a Python reference. Their Python class will only be changed after all references are gone and the Python object is garbage collected.

### 高级元素类查找

=== "中文"

    在某些情况下，正常的数据类设置是不够的。 然而，`lxml.objectify` 基于 `lxml.etree`，支持对树中使用的 `Element` 类进行非常细粒度的控制。 您所要做的就是配置一种不同的[类查找](https://lxml.de/element_classes.html)机制（或自己编写一个）。
    
    设置的第一步是创建一个新的解析器来构建对象化文档。 **objectify API** 适用于以数据为中心的 XML（而不是具有混合内容的文档 XML）。 因此，我们将解析器配置为让它从解析的文档中删除纯空白文本（如果该文本未包含在 XML 元素中）。 请注意，这会改变文档信息集，因此如果您将删除的空格视为特定用例中的数据，则应该使用普通的解析器并仅设置元素类查找。 然而，大多数应用程序都可以通过以下设置正常工作：

    ```pycon
    >>> parser = objectify.makeparser(remove_blank_text=True)
    ```
    
    它的内部作用是：

    ```pycon
    >>> parser = etree.XMLParser(remove_blank_text=True)
    
    >>> lookup = objectify.ObjectifyElementClassLookup()
    >>> parser.set_element_class_lookup(lookup)
    ```

    如果您想更改查找方案，例如，获得对[命名空间特定类](https://lxml.de/element_classes.html#namespace-class-lookup)的额外支持，您可以将 objectify 查找注册为后备 命名空间查找。 然而，在这种情况下，您必须注意命名空间类继承自 `objectify.ObjectifiedElement`，而不仅仅是普通的 `lxml.etree.ElementBase`，以便它们支持 `objectify API`。 上面的设置代码就变成了：

    ```pycon
    >>> lookup = etree.ElementNamespaceClassLookup(
    ...                   objectify.ObjectifyElementClassLookup() )
    >>> parser.set_element_class_lookup(lookup)
    ```

    有关更多信息，请参阅有关[类查找](https://lxml.de/element_classes.html)方案的文档。

=== "英文"

    **Advanced element class lookup**

    In some cases, the normal data class setup is not enough. Being based on lxml.etree, however, lxml.objectify supports very fine-grained control over the Element classes used in a tree. All you have to do is configure a different [class lookup](https://lxml.de/element_classes.html) mechanism (or write one yourself).
    
    The first step for the setup is to create a new parser that builds objectify documents. The objectify API is meant for data-centric XML (as opposed to document XML with mixed content). Therefore, we configure the parser to let it remove whitespace-only text from the parsed document if it is not enclosed by an XML element. Note that this alters the document infoset, so if you consider the removed spaces as data in your specific use case, you should go with a normal parser and just set the element class lookup. Most applications, however, will work fine with the following setup:

    ```pycon
    >>> parser = objectify.makeparser(remove_blank_text=True)
    ```
    
    What this does internally, is:

    ```pycon
    >>> parser = etree.XMLParser(remove_blank_text=True)
    
    >>> lookup = objectify.ObjectifyElementClassLookup()
    >>> parser.set_element_class_lookup(lookup)
    ```

    If you want to change the lookup scheme, say, to get additional support for [namespace specific classes](https://lxml.de/element_classes.html#namespace-class-lookup), you can register the objectify lookup as a fallback of the namespace lookup. In this case, however, you have to take care that the namespace classes inherit from objectify.ObjectifiedElement, not only from the normal lxml.etree.ElementBase, so that they support the objectify API. The above setup code then becomes:

    ```pycon
    >>> lookup = etree.ElementNamespaceClassLookup(
    ...                   objectify.ObjectifyElementClassLookup() )
    >>> parser.set_element_class_lookup(lookup)
    ```

    See the documentation on [class lookup](https://lxml.de/element_classes.html) schemes for more information.

## 与 lxml.etree 有什么不同？

=== "中文"

    这种不同的 Element API 显然意味着对 API 其余部分的正常行为有一些副作用。

    * `len(<element>)` 返回同级计数，而不是 `<element>` 的子级数量。 您可以使用`countchildren()`方法检索子级的数量。
    * 元素的迭代不会产生子元素，而是产生兄弟元素。 您可以使用元素上的`iterchildren()`方法访问所有子项，或通过调用`getchildren()`方法检索列表。
    * `find`、`findall` 和 `findtext` 方法需要基于 `ETXPath` 的不同实现。 在`lxml.etree`中，他们使用基于原始迭代方案的Python实现。 这样做的缺点是它们可能无法 100% 向后兼容，另外的优点是它们现在支持任何 `XPath` 表达式。

=== "英文"

    **What is different from lxml.etree?**

    Such a different Element API obviously implies some side effects to the normal behaviour of the rest of the API.

    * `len(<element>)` returns the sibling count, not the number of children of `<element>`. You can retrieve the number of children with the `countchildren()` method.
    * Iteration over elements does not yield the children, but the siblings. You can access all children with the `iterchildren()` method on elements or retrieve a list by calling the `getchildren()` method.
    * The find, findall and findtext methods require a different implementation based on ETXPath. In `lxml.etree`, they use a Python implementation based on the original iteration scheme. This has the disadvantage that they may not be 100% backwards compatible, and the additional advantage that they now support any XPath expression.
