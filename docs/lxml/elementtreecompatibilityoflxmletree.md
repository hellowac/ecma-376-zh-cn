# lxml.tree 与 ElementTree 的兼容性

**ElementTree compatibility of lxml.etree**

=== "中文"

    为了确保 etree 和 ElementTree 之间的兼容性，我们付出了很多努力。 尽管如此，仍然存在一些差异和不兼容性：

    - 导入 etree 明显不同； etree 使用小写的包名称，而 ElementTree 在导入中使用大写和小写的组合：

        ```python
        # etree
        from lxml.etree import Element
        
        # ElementTree
        from elementtree.ElementTree import Element
        
        # ElementTree in the Python 2.5 standard library
        from xml.etree.ElementTree import Element
        ```
    
        当将代码从 ElementTree 切换到 lxml.etree 时，并且您使用包名称前缀 “ElementTree”，您可以执行以下操作：

        ```python
        # instead of
        from elementtree import ElementTree
        
        # use
        from lxml import etree as ElementTree
        ```
    
    - lxml.etree 提供了更多的功能，例如 XPath、XSLT、Relax NG 和 XML Schema 支持，而 `(c)ElementTree` 不提供这些功能。
    - etree 对 Python unicode 字符串的理解与 ElementTree 不同。 在 API 的大部分部分，ElementTree 按原样使用纯字符串和 unicode 字符串。 这包括 Element.text、Element.tail 和许多其他地方。 但是，ElementTree 解析器默认假定任何字符串（str 或 unicode）都包含 ASCII 数据。 如果字符串与预期的编码不匹配，它们会引发异常。

        etree 对于纯字符串 (str) 的理解与 ElementTree 相同。 然而，对于 unicode 字符串，etree 在整个 API 中假定它们是 Python unicode 编码字符串而不是字节数据。 这包括解析器。 因此，以 Python unicode 字符串的形式将 XML unicode 数据传递到 etree 解析器是完全正确的。 另一方面，如果 unicode 字符串在其 XML 声明中指定编码，则这是一个错误，因为这与 Python unicode 字符串的特征编码冲突。 
    
    - ElementTree 允许您同时将一个元素放置在两个不同的树中。 因此，这个：

        ```python
        a = Element('a')
        b = SubElement(a, 'b')
        c = Element('c')
        c.append(b)
        ```

        将产生以下树a：

        ```xml
        <a><b /></a>
        ```

        在 lxml 中，这种行为有所不同，因为 lxml 构建在维护元素父关系的树之上（如 W3C DOM）。 这意味着一个元素只能同时存在于一棵树中。 将某棵树中的元素添加到另一棵树中将导致该元素被移动。
        
        因此，对于树 a 我们将得到：

        ```xml
        <a></a>
        ```

        对于树 c，我们将得到：

        ```xml
        <c><b/></c>
        ```

        不幸的是，这是行为上相当根本的差异，很难改变。 它不会影响某些应用程序，但如果您想移植代码，您必须不幸地确保它不会影响您的应用程序。

    - etree 允许通过 getparent() 方法导航到节点的父节点，并通过调用 getnext() 和 getprevious() 导航到兄弟节点。 这在 ElementTree 中是不可能的，因为底层树模型没有此信息。
    - 当尝试使用 __setitem__ 设置一个实际上不是 Element 而是其他对象的子元素时，etree 会引发 TypeError，ElementTree 会引发 AssertionError。 这也适用于 API 的其他一些地方。 一般来说，etree 会尝试避免 AssertionErrors，转而更具体地说明异常的原因。
    - 当 iterparse() 中解析失败时，1.2.x 版本之前的 ElementTree 会引发低级 ExpatError，而不是像其他解析器那样引发 SyntaxError。 lxml 和 ElementTree 1.3 都会因解析器错误而引发 ParseError。
    - lxml中的 iterparse()函数 是基于libxml2解析器和树生成器实现的。 这意味着在解析过程中对文档根或当前元素的祖先的修改可能会激怒解析器，甚至出现段错误。 虽然这在 ElementTree 使用的 Python 对象结构中不是问题，但 lxml 底层的 C 树却受到了影响。 因此，lxml 上 iterparse() 的黄金法则是：不要触及解析器稍后必须再次触及的任何内容。 请参阅有关此内容的 lxml 解析器文档。
    - ElementTree在解析XML时会忽略注释和处理指令，而etree会将它们读入并分别将它们视为Comment或ProcessingInstruction元素。 在文本内容中找到注释（然后由 Comment 元素分割）的情况下，这一点尤其明显。
    
        您可以通过将布尔值 remove_comments 和/或 remove_pis 关键字参数传递给您使用的解析器来禁用此行为。 为了方便并支持可移植代码，您还可以使用 etree.ETCompatXMLParser 而不是默认的 etree.XMLParser。 它尝试提供尽可能接近 ElementTree 解析器的默认设置。
    
    - lxml.etree 的 TreeBuilder 类对 start() 方法使用不同的签名。 它接受一个附加参数 nsmap 来传播元素除了其自己的命名空间之外的命名空间声明。 为了确保与 ElementTree（不支持此参数）的兼容性，lxml 在调用该方法之前检查该方法是否接受 3 个参数，否则会删除名称空间映射。 这应该适用于大多数现有的 ElementTree 代码，尽管可能仍然存在冲突的情况。
    - ElementTree 1.2 在将空注释（未给出文本参数）序列化为 XML 时存在错误，etree 成功序列化了该错误。
    - ElementTree 在序列化注释周围添加空格，而 lxml 则没有。 这意味着 ElementTree 序列化为`<!--text -->`的注释文本“text”将在 lxml 中变为 `<!--text-->`。
    - 当字符串 '*' 在 Element.iter() 和 .find*() 方法中用作标记过滤器时，ElementTree 返回树中的所有元素，包括注释和处理指令。 lxml.etree 只返回真实的元素，即具有字符串标签名称的树节点。 如果没有过滤器，两个库都会迭代所有节点。

        请注意，当前只有 lxml.etree 支持将元素工厂函数作为过滤器传递以仅选择元素。 这两个库都支持传递 Comment 和ProcessingInstruction 工厂来选择相应的树节点。

    - ElementTree 将处理指令的目标合并到 `PI.text` 中，而 `lxml.etree` 将其放入 `.target` 属性中并将其排除在 `.text` 属性之外。 因此，ElementTree 中的 `pi.text` 对应于 `lxml.etree` 中的 `pi.target + " " + pi.text`。
    - 因为 etree 构建在 libxml2 之上，所以 etree 保留命名空间声明和前缀，而 ElementTree 则倾向于使用自己的前缀（`ns0`、`ns1` 等）。 然而，当没有给出命名空间前缀时，etree 也会创建 `ElementTree` 样式前缀。
    - etree 在元素上有一个`prefix`属性（只读），如果已知，则给出元素的前缀，否则为`None`（如果根本没有命名空间或默认命名空间）。
    - etree 还允许将 `nsmap` 字典传递给 Element 和 SubElement 元素工厂，以显式地将名称空间前缀映射到名称空间 URI。 这些将被转换为该元素上的名称空间声明。 这意味着，在极少数情况下，您需要构造一个名为`nsmap`的属性，您需要注意，与 ElementTree 不同，您不能将其作为关键字参数直接传递给 Element 和 SubElement 工厂。
    - ElementTree 允许 QName 对象作为属性值，并在序列化时解析它们的前缀（例如，如果`p`是`myns`的命名空间前缀，则属性值 QName(`{myns}myname`) 变为`p:myname`）。 lxml.etree 还允许您从 QName 实例设置属性值（以及 `.text` 值），但它会立即解析它们的前缀并存储纯文本值。 因此，如果稍后修改前缀，例如 通过将子树移动到不同的树（重新分配前缀映射），文本值将不会更新，并且您可能最终会得到未定义的前缀。
    - etree 元素可以使用 `copy.deepcopy()` 和 `copy.copy()` 进行复制，就像 ElementTree 一样。 但是，copy.copy() 不会创建在树之间共享元素的浅表副本，因为这在 libxml2 树的上下文中没有意义。 请注意，lxml 深度复制树的速度比 ElementTree 快得多，因此在您的情况下，深度复制可能仍然足够快以替换浅度复制。

=== "英文"

    A lot of care has been taken to ensure compatibility between etree and ElementTree. Nonetheless, some differences and incompatibilities exist:

    - Importing etree is obviously different; etree uses a lower-case package name, while ElementTree uses a combination of upper-case and lower case in imports:

        ```python
        # etree
        from lxml.etree import Element
        
        # ElementTree
        from elementtree.ElementTree import Element
        
        # ElementTree in the Python 2.5 standard library
        from xml.etree.ElementTree import Element
        ```
    
        When switching over code from ElementTree to lxml.etree, and you're using the package name prefix 'ElementTree', you can do the following:

        ```python
        # instead of
        from elementtree import ElementTree
        
        # use
        from lxml import etree as ElementTree
        ```
    
    - lxml.etree offers a lot more functionality, such as XPath, XSLT, Relax NG, and XML Schema support, which (c)ElementTree does not offer.
    - etree has a different idea about Python unicode strings than ElementTree. In most parts of the API, ElementTree uses plain strings and unicode strings as what they are. This includes Element.text, Element.tail and many other places. However, the ElementTree parsers assume by default that any string (str or unicode) contains ASCII data. They raise an exception if strings do not match the expected encoding.

        etree has the same idea about plain strings (str) as ElementTree. For unicode strings, however, etree assumes throughout the API that they are Python unicode encoded strings rather than byte data. This includes the parsers. It is therefore perfectly correct to pass XML unicode data into the etree parsers in form of Python unicode strings. It is an error, on the other hand, if unicode strings specify an encoding in their XML declaration, as this conflicts with the characteristic encoding of Python unicode strings.
    
    - ElementTree allows you to place an Element in two different trees at the same time. Thus, this:

        ```python
        a = Element('a')
        b = SubElement(a, 'b')
        c = Element('c')
        c.append(b)
        ```

        will result in the following tree a:

        ```xml
        <a><b /></a>
        ```

        In lxml, this behavior is different, because lxml is built on top of a tree that maintains parent relationships for elements (like W3C DOM). This means an element can only exist in a single tree at the same time. Adding an element in some tree to another tree will cause this element to be moved.
        
        So, for tree a we will get:

        ```xml
        <a></a>
        ```

        and for tree c we will get:

        ```xml
        <c><b/></c>
        ```

        Unfortunately this is a rather fundamental difference in behavior, which is hard to change. It won't affect some applications, but if you want to port code you must unfortunately make sure that it doesn't affect yours.

    - etree allows navigation to the parent of a node by the getparent() method and to the siblings by calling getnext() and getprevious(). This is not possible in ElementTree as the underlying tree model does not have this information.
    - When trying to set a subelement using __setitem__ that is in fact not an Element but some other object, etree raises a TypeError, and ElementTree raises an AssertionError. This also applies to some other places of the API. In general, etree tries to avoid AssertionErrors in favour of being more specific about the reason for the exception.
    - When parsing fails in iterparse(), ElementTree up to version 1.2.x raises a low-level ExpatError instead of a SyntaxError as the other parsers. Both lxml and ElementTree 1.3 raise a ParseError for parser errors.
    - The iterparse() function in lxml is implemented based on the libxml2 parser and tree generator. This means that modifications of the document root or the ancestors of the current element during parsing can irritate the parser and even segfault. While this is not a problem in the Python object structure used by ElementTree, the C tree underlying lxml suffers from it. The golden rule for iterparse() on lxml therefore is: do not touch anything that will have to be touched again by the parser later on. See the lxml parser documentation on this.
    - ElementTree ignores comments and processing instructions when parsing XML, while etree will read them in and treat them as Comment or ProcessingInstruction elements respectively. This is especially visible where comments are found inside text content, which is then split by the Comment element.
    
        You can disable this behaviour by passing the boolean remove_comments and/or remove_pis keyword arguments to the parser you use. For convenience and to support portable code, you can also use the etree.ETCompatXMLParser instead of the default etree.XMLParser. It tries to provide a default setup that is as close to the ElementTree parser as possible.
    
    - The TreeBuilder class of lxml.etree uses a different signature for the start() method. It accepts an additional argument nsmap to propagate the namespace declarations of an element in addition to its own namespace. To assure compatibility with ElementTree (which does not support this argument), lxml checks if the method accepts 3 arguments before calling it, and otherwise drops the namespace mapping. This should work with most existing ElementTree code, although there may still be conflicting cases.
    - ElementTree 1.2 has a bug when serializing an empty Comment (no text argument given) to XML, etree serializes this successfully.
    - ElementTree adds whitespace around comments on serialization, lxml does not. This means that a comment text "text" that ElementTree serializes as "<!-- text -->" will become "<!--text-->" in lxml.
    - When the string '*' is used as tag filter in the Element.iter() and .find*() methods, ElementTree returns all elements in the tree, including comments and processing instructions. lxml.etree only returns real Elements, i.e. tree nodes that have a string tag name. Without a filter, both libraries iterate over all nodes.

        Note that currently only lxml.etree supports passing the Element factory function as filter to select only Elements. Both libraries support passing the Comment and ProcessingInstruction factories to select the respective tree nodes.

    - ElementTree merges the target of a processing instruction into PI.text, while lxml.etree puts it into the .target property and leaves it out of the .text property. The pi.text in ElementTree therefore correspondents to pi.target + " " + pi.text in lxml.etree.
    - Because etree is built on top of libxml2, which is namespace prefix aware, etree preserves namespaces declarations and prefixes while ElementTree tends to come up with its own prefixes (ns0, ns1, etc). When no namespace prefix is given, however, etree creates ElementTree style prefixes as well.
    - etree has a 'prefix' attribute (read-only) on elements giving the Element's prefix, if this is known, and None otherwise (in case of no namespace at all, or default namespace).
    - etree further allows passing an 'nsmap' dictionary to the Element and SubElement element factories to explicitly map namespace prefixes to namespace URIs. These will be translated into namespace declarations on that element. This means that in the probably rare case that you need to construct an attribute called 'nsmap', you need to be aware that unlike in ElementTree, you cannot pass it as a keyword argument to the Element and SubElement factories directly.
    - ElementTree allows QName objects as attribute values and resolves their prefix on serialisation (e.g. an attribute value QName("{myns}myname") becomes "p:myname" if "p" is the namespace prefix of "myns"). lxml.etree also allows you to set attribute values from QName instances (and also .text values), but it resolves their prefix immediately and stores the plain text value. So, if prefixes are modified later on, e.g. by moving a subtree to a different tree (which reassigns the prefix mappings), the text values will not be updated and you might end up with an undefined prefix.
    - etree elements can be copied using copy.deepcopy() and copy.copy(), just like ElementTree's. However, copy.copy() does not create a shallow copy where elements are shared between trees, as this makes no sense in the context of libxml2 trees. Note that lxml can deep-copy trees considerably faster than ElementTree, so a deep copy might still be fast enough to replace a shallow copy in your case.
