# 19.6 幻灯片同步数据

=== "中文"

    通常情况下，幻灯片会从现有演示文稿中重新调整用途，以用于其他演示文稿。 在这种情况下，原始幻灯片与其所有复制实例之间存在关联或配对通常是有益的。 在存在这种配对的情况下，应用程序可以启用各种节省时间的功能，包括当原始幻灯片发生更改时自动更新复制的幻灯片。 幻灯片同步数据部分旨在实现此类应用程序定义的功能。
    
    此信息存储在幻灯片同步数据部件中，该部件通过关联幻灯片部件的隐式关系进行引用。

    ??? info "译注:关系详情"

        参考: [9.2 Office Open Xml 中的关系](../chapter-9.md#92-office-open-xml-中的关系){target="_bank"}

=== "英文"

    **Slide Synchronization Data**

    It is often the case that slides are repurposed from existing presentations to be used in other presentations. In such cases, it is often beneficial for there to be an association, or a pairing, between the original slide and all copied instances of it. In the presence of such a pairing, applications can enable a variety of time-saving features, including the automatic updates of copied slides when the original slide changes. The Slide Synchronization Data part is designed to enable such application-defined functionality.
    
    This information is stored in the Slide Synchronization Data part, which is referenced via an implicit relationship from the associated Slide part.

## 19.6.1 sldSyncPr (幻灯片同步属性)

=== "中文"

    此元素指定将原始幻灯片与其所有复制实例相关联所需的信息。
    
    <table>
        <thead>
            <tr>
                <th>**属性**</th>
                <th>**描述**</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>
                    clientInsertedTime </br>
                    (客户幻灯片插入日期/时间)
                </td>
                <td>
                    当前演示文稿中原始幻灯片上次更新的日期和时间。</br></br>
                    日期/时间(date/time)以 ISO 8601 格式存储。</br></br>
                    [注意: 该值可用于通知用户上次同步的时间，以及确定下次检查更新版本的时间。 ]</br></br>
                    此属性的可能值由 W3C XML Schema `dateTime` 数据类型定义。
                </td>
            </tr>
            <tr>
                <td>
                    serverSldId </br>
                    (服务器的幻灯片文件 ID)
                </td>
                <td>
                    一个字符串，当与幻灯片同步数据部件的外部关系的目标配对时，唯一标识原始幻灯片。</br></br>
                    此属性的可能值由 W3C XML Schema字符串(string)数据类型定义。
                </td>
            </tr>
            <tr>
                <td>
                    serverSldModifiedTime </br>
                     (服务器幻灯片文件的修改日期/时间)
                </td>
                <td>
                    原始幻灯片在其位置（由幻灯片同步数据部件的外部关系的目标定义）最后修改的日期和时间。</br></br>
                    日期和时间以 ISO 8601 格式存储。    </br></br>
                    此属性的可能值由 W3C XML Schema dateTime 数据类型定义。
                </td>
            </tr>
        </tbody>
    </table>

=== "英文"

    **sldSyncPr (Slide Synchronization Properties)**
    
    This element specifies the information needed to associate the original slide with all copied instances of it.
    
    <table>
        <thead>
            <tr>
                <th>**Attributes**</th>
                <th>**Description**</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>
                    clientInsertedTime </br>
                    (Client Slide Insertion date/time)
                </td>
                <td>
                    The date and time that the original slide was last updated in the current presentation.</br></br>
                    The date/time is stored in ISO 8601 format.</br></br>
                    [Note: This value can be used to inform the user of when the last synchronization was, as well as to determine when to next check for an updated version. end note]</br></br>
                    The possible values for this attribute are defined by the W3C XML Schema dateTime datatype.
                </td>
            </tr>
            <tr>
                <td>
                    serverSldId </br>
                    (Server's Slide File ID)
                </td>
                <td>
                    A string that, when paired with the target of the Slide Synchronization Data part’s external relationship, uniquely identifies the original slide.</br></br>
                    The possible values for this attribute are defined by the W3C XML Schema string datatype.
                </td>
            </tr>
            <tr>
                <td>
                    serverSldModifiedTime </br>
                     (Server's Slide File's modification date/time)
                </td>
                <td>
                    The date and time that the original slide was last modified in its location as defined by the target of the Slide Synchronization Data part’s external relationship.</br></br>
                    The date and time are stored in ISO 8601 format.    </br></br>
                    The possible values for this attribute are defined by the W3C XML Schema dateTime datatype.
                </td>
            </tr>
        </tbody>
    </table>
