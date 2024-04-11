# 解析xsd文件

参考包: <https://github.com/sissaschool/xmlschema>

文档: <https://xmlschema.readthedocs.io/en/latest/components.html>

```python
from lxml import etree
from lxml import objectify

from typing import List
import xmlschema
from xmlschema.validators.schemas import XMLSchema10
from xmlschema.validators.elements import XsdElement
from xmlschema.validators.simple_types import XsdSimpleType
from xmlschema.validators.complex_types import XsdComplexType
from xmlschema.namespaces import NamespaceView
from xmlschema.validators.groups import XsdGroup
from xmlschema.validators.attributes import XsdAttributeGroup


def main():
    print(f"hello world")


def main2():
    """解析xsd文件

    参考: https://xmlschema.readthedocs.io/en/latest/components.html
    """
    xsd_file = "xsd/xmlSchema/pml.xsd"

    my_schema: XMLSchema10 = xmlschema.XMLSchema(xsd_file)

    print(f"{type(my_schema)}")

    # print(f"{my_schema.xsd_element_class.text = }")
    # print(f"{my_schema.schema_location = }")
    # print(f"{my_schema.tag = }")
    # print(f"{my_schema.version = }")
    # print(f"{my_schema.all_errors = }")
    # print(f"{my_schema.allow = }")
    # print(f"{my_schema.all_errors = }")
    # print(f"{my_schema.annotations = }")
    # print(f"{my_schema.attrib = }")
    # print(f"{my_schema.target_prefix = }")
    # print(f"{my_schema.root_elements = }")

    all_components = list(my_schema.iter_components())
    all_children = list(my_schema.iterchildren())
    all_globals = list(my_schema.iter_globals())

    elements: List[XsdElement] = my_schema.elements

    root_elements: List[XsdElement] = my_schema.root_elements

    simple_elements: List[XsdSimpleType] = my_schema.simple_types

    complex_types: List[XsdComplexType] = my_schema.complex_types

    groups: NamespaceView[XsdGroup] = my_schema.groups

    attribute_groups: NamespaceView[XsdAttributeGroup] = my_schema.attribute_groups

    print(f"schema 命名空间: {my_schema.namespaces = }")
    print(f"所有组件数量: {len(all_components) = }")
    print(f"所有children数量: {len(all_children) = }")
    print(f"所有globals数量: {len(all_globals) = }")
    print(f"element节点数量: {len(elements) = }")
    print(f"根节点数量: {len(root_elements) = }")
    print(f"简单类型数量: {len(simple_elements) = }")
    print(f"复杂类型数量: {len(complex_types) = }")
    print(f"group类型数量: {len(groups) = }")
    print(f"属性group类型数量: {len(attribute_groups) = }")

    # for element in root_elements:
    #     print(f"*" * 50)
    #     print(f"{element.tag = }")
    # print(f"{element.name = }")
    # print(f"{element.local_name = }")
    # print(f"{element.default_namespace = }")
    # print(f"{element.target_namespace = }")
    #     print(f"{element.target_namespace = }")
    #     print(f"{element.namespaces = }")
    #     print(f"{element.type = }")
    #     print(f"{element.type.elem = }")
    #     print(f"{element.annotation = }")
    #     print(f"{element.attrib = }")
    #     print(f"{element.attributes = }")
    #     print(f"{element.elem = }")
    # print(f"{element.attrib['TargetMode'] = }")

    for complex_type in complex_types:
        # print(f"{complex_type.name = }")
        # print(f"{complex_type.local_name = }")
        # if complex_type.local_name == "CT_TransitionStartSoundAction":
        if isinstance(complex_type.content, XsdSimpleType):
            print(f"{complex_type.local_name = } -> {complex_type.content = }")
        else:
            continue
        # for item in complex_type.content:

    for index, global_componet in enumerate(all_globals, start=1):
        print(f"{index} - {global_componet } ")  # { global_componet.local_name = }

    print(f"{len(my_schema.maps.elements) = }")
    print(f"{len(my_schema.types) = }")
    print(f"{my_schema.types['ST_TLBehaviorOverrideType'] = }")


if __name__ == "__main__":
    main2()

```
