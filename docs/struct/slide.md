# 幻灯片部件结构

## 根元素

- p:sld - [Slide](../ecma-part1/chapter19/slides.md#193138-sld-演示幻灯片) - 演示幻灯片
    - p:clrMapOvr - [ColorMappingOverride](../ecma-part1/chapter19/slides.md#19317-clrmapovr-配色方案地图覆盖) - 配色方案映射覆盖 - [2选1]
        - a:masterClrMapping - [EmptyElement](../ecma-part1/chapter20/main/shared_style_sheet.md#20166-masterclrmapping-主颜色映射) - 母板配色方案映射
        - a:overrideClrMapping - [ColorMapping](../ecma-part1/chapter20/main/shared_style_sheet.md#20168-overrideclrmapping-颜色映射覆盖) - 配色方案映射覆盖
    - p:cSld - [CommonSlideData](../ecma-part1/chapter19/slides.md#193116-csld-通用幻灯片数据) - 通用幻灯片数据
        - p:bg - [Background](../ecma-part1/chapter19/slides.md#19311-bg-幻灯片背景) - 幻灯片背景 - [2选1]
            - p:bgPr - [BackgroundProperties](../ecma-part1/chapter19/slides.md#19312-bgpr-背景属性) - 背景属性
                - fill - 填充样式 [可选][6选1]
                    - a:noFill - [NoFillProperties](../ecma-part1/chapter20/main/shape_fill.md#201844-nofill-无填充) - 无填充
                    - a:solidFill - [SolidColorFillProperties](../ecma-part1/chapter20/main/shape_fill.md#201854-solidfill-实心填充) - 实心填充
                    - a:gradFill - [GradientFillProperties](../ecma-part1/chapter20/main/shape_fill.md#201833-gradfill-渐变填充) - 渐变填充
                    - a:blipFill - [BlipFillProperties](../ecma-part1/chapter20/main/shape_fill.md#201814-blipfill-图片填充) - 图片填充
                    - a:pattFill - [PatternFillProperties](../ecma-part1/chapter20/main/shape_fill.md#201847-pattfill-图案填充) - 图案填充
                    - a:grpFill - [GroupFillProperties](../ecma-part1/chapter20/main/shape_fill.md#201835-grpfill-组合填充)
                - effect - 效果样式 [可选][2选1]
                    - a:effectLst - [EffectList](../ecma-part1/chapter20/main/shape_fill.md#201826-effectlst-效果列表) - 效果列表
                    - a:effectDag - [EffectContainer](../ecma-part1/chapter20/main/shape_fill.md#201820-cont-效果容器) - 效果容器
                - 其他属性，参考文档
            - p:bgRef - [StyleMatrixReference](../ecma-part1/chapter19/slides.md#19313-bgref-背景样式参考) - 背景样式引用
        - p:spTree - [GroupShape](../ecma-part1/chapter19/slides.md#193145-sptree-图形树) - 图形树 形状列表 联合类型
            - p:sp - [Shape](../ecma-part1/chapter19/slides.md#193143-sp-图形) - 形状(常规形状) - 结构参考上面的[常规形状](#常规形状)
            - p:grpSp - [GroupShape](../ecma-part1/chapter19/slides.md#193122-grpsp-组合图形) - 组合形状 - 结构参考上面的[组合形状](#组合形状)
            - p:graphicFrame - [GraphicalObjectFrame](../ecma-part1/chapter19/slides.md#193121-graphicframe-图框) - 结构参考上面的[图框形状](#图框形状)
            - p:cxnSp - [Connector](../ecma-part1/chapter19/slides.md#193119-cxnsp-连接形状) - 连接形状 - 结构参考上面的[链接线结构](#链接线结构)
            - p:pic - [Picture](../ecma-part1/chapter19/slides.md#193137-pic-图片) - 图片形状 - 结构参考上面的[图片形状](#图片形状)
            - p:contentPart - [Rel](../ecma-part1/chapter19/slides.md#193114-contentpart-内容部分) - 内容部件内容 - 结构参考上面的[内容部件形状](#内容部件形状)
        - p:custDataLst - [CustomerDataList](../ecma-part1/chapter19/slides.md#193118-custdatalst-客户资料清单) - 自定义数据
        - p:controls - [ControlList](../ecma-part1/chapter19/slides.md#193115-controls-控件列表) - 控件列表
        - 其他属性，参考文档
    - p:transition - [SlideTransition](../ecma-part1/chapter19/slides.md#193150-transition-幻灯片布局的幻灯片过渡) - 幻灯片动画数据
    - p:timing - [SlideTiming](../ecma-part1/chapter19/slides.md#193148-timing-幻灯片布局的幻灯片计时信息) - 幻灯片动画计时数据
    - 其他属性，参考文档

## 形状结构

### 常规形状

- p:sp - [Shape](../ecma-part1/chapter19/slides.md#193143-sp-图形) - 形状(常规形状)
    - p:nvSpPr - [ShapeNonVisual](../ecma-part1/chapter19/slides.md#193134-nvsppr-形状的非视觉属性) - 形状的非视觉属性 - 结构参考下面的[非可视绘图属性](#非可视绘图属性)
    - p:spPr - [ShapeProperties](../ecma-part1/chapter19/slides.md#193144-sppr-图形属性) - 图形属性 - 结构参考下面的[图形属性](#图形属性)
    - p:style- [ShapeStyle](../ecma-part1/chapter19/slides.md#193146-style-图形样式) - 图形样式 - 结构参考下面的[图形样式](#图形样式)
    - p:txBody - [TextBody](../ecma-part1/chapter21/main.md#21121-正文格式) - 正文格式 - 结构参考下面的[正文格式](#正文格式)
    - 其他属性，参考文档

### 图框形状

该框架包含由外部源生成的图形，并且需要一个容器来在幻灯片表面上显示。

- p:graphicFrame - [GraphicalObjectFrame](../ecma-part1/chapter19/slides.md#193121-graphicframe-图框)
    - p:nvGraphicFramePr - [GraphicalObjectFrameNonVisual](../ecma-part1/chapter19/slides.md#193130-nvgraphicframepr-图形框架的非视觉属性) - 图形框架的非视觉属性
        - p:cNvPr - [NonVisualDrawingProps](../ecma-part1/chapter19/slides.md#193112-cnvpr-非可视绘图属性) - 非可视绘图属性
            - a:hlinkClick - [Hyperlink](../ecma-part1/chapter21/main.md#211235-hlinkclick-单击超链接) - 单击超链接
            - a:hlinkHover - [Hyperlink](../ecma-part1/chapter20/main/basics.md#2012223-hlinkhover-悬停的超链接) - 悬停的超链接
            - 其他属性，参考文档
        - p:cNvGraphicFramePr - [NonVisualGraphicFrameProperties](../ecma-part1/chapter19/slides.md#19319-cnvgraphicframepr-非可视图形框架绘图属性) - 非可视图形框架绘图属性
            - a:graphicFrameLocks - [GraphicalObjectFrameLocking](../ecma-part1/chapter20/main/basics.md#2012219-graphicframelocks-图形框架锁) - 图形框架锁定属性
        - p:nvPr - [ApplicationNonVisualDrawingProps](../ecma-part1/chapter19/slides.md#193133-nvpr-非视觉属性) - 非视觉属性
            - p:ph - [Placeholder](../ecma-part1/chapter19/slides.md#193136-ph-占位符形状) - 占位符形状
            - media - 媒体 [可选][5选1]
                - a:audioCd - [AudioCD](../ecma-part1/chapter20/main/audioandvideo.md#20131-audiocd-cd-中的音频) - CD 中的音频
                - a:wavAudioFile - [EmbeddedWAVAudioFile](../ecma-part1/chapter20/main/audioandvideo.md#20137-wavaudiofile-wav-文件中的音频) - WAV 音频文件
                - a:audioFile - [AudioFile](../ecma-part1/chapter20/main/audioandvideo.md#20132-audiofile-文件中的音频) - 文件中的音频
                - a:videoFile - [VideoFile](../ecma-part1/chapter20/main/audioandvideo.md#20136-videofile-文件中的视频) - 文件中的视频
                - a:quickTimeFile - [QuickTimeFile](../ecma-part1/chapter20/main/audioandvideo.md#20134-quicktimefile-来自文件的-quicktime) - 文件的 QuickTime
    - p:xfrm - [Transform2D](../ecma-part1/chapter19/slides.md#193153-xfrm-图形框架的-2d-变换) - 2d-变换
    - a:graphic - [GraphicalObject](../ecma-part1/chapter20/main/basics.md#2012216-graphic-图形对象) - graphic-图形对象
        - a:graphicData - [GraphicalObjectData](../ecma-part1/chapter20/main/basics.md#2012217-graphicdata-图形对象数据) - 图形对象数据
            - uri - 统一资源标识符 - 关联的外部部件，可能是表格、图表、或其他数据...
    - 其他属性，参考文档



### 链接线结构

- p:cxnSp - [Connector](../ecma-part1/chapter19/slides.md#193119-cxnsp-连接形状) - 连接形状
    - p:nvCxnSpPr - [ConnectorNonVisual](../ecma-part1/chapter19/slides.md#193129-nvcxnsppr-连接形状的非视觉属性) - 连接形状的非视觉属性
        - p:cNvPr - [NonVisualDrawingProps](../ecma-part1/chapter20/main/basics.md#201228-cnvpr-非可视绘图属性) - 非可视绘图属性
            - a:hlinkClick - [Hyperlink](../ecma-part1/chapter21/main.md#211235-hlinkclick-单击超链接) - 单击超链接
            - a:hlinkHover - [Hyperlink](../ecma-part1/chapter20/main/basics.md#2012223-hlinkhover-悬停的超链接) - 悬停的超链接
            - 其他属性，参考文档
        - p:cNvCxnSpPr - [NonVisualConnectorProperties](../ecma-part1/chapter19/slides.md#19318-cnvcxnsppr-非可视连接器形状绘图属性) - 非可视连接器形状绘图属性
            - a:cxnSpLocks - [ConnectorLocking](../ecma-part1/chapter20/main/basics.md#2012211-cxnsplocks-连接形状锁) - 连接形状锁定属性
            - a:stCxn - [Connection](../ecma-part1/chapter20/main/basics.md#2012236-stcxn-连接开始) - 开始连接点
            - a:endCxn - [Connection](../ecma-part1/chapter20/main/basics.md#2012213-endcxn-连接结束) - 结束连接点
        - p:nvPr - [ApplicationNonVisualDrawingProps](../ecma-part1/chapter19/slides.md#193133-nvpr-非视觉属性) - 非视觉属性
            - p:ph - [Placeholder](../ecma-part1/chapter19/slides.md#193136-ph-占位符形状) - 占位符形状
            - media - 媒体 [可选][5选1]
                - a:audioCd - [AudioCD](../ecma-part1/chapter20/main/audioandvideo.md#20131-audiocd-cd-中的音频) - CD 中的音频
                - a:wavAudioFile - [EmbeddedWAVAudioFile](../ecma-part1/chapter20/main/audioandvideo.md#20137-wavaudiofile-wav-文件中的音频) - WAV 音频文件
                - a:audioFile - [AudioFile](../ecma-part1/chapter20/main/audioandvideo.md#20132-audiofile-文件中的音频) - 文件中的音频
                - a:videoFile - [VideoFile](../ecma-part1/chapter20/main/audioandvideo.md#20136-videofile-文件中的视频) - 文件中的视频
                - a:quickTimeFile - [QuickTimeFile](../ecma-part1/chapter20/main/audioandvideo.md#20134-quicktimefile-来自文件的-quicktime) - 文件的 QuickTime
    - p:spPr - [ShapeProperties](../ecma-part1/chapter19/slides.md#193144-sppr-图形属性) - 图形属性 - 结构参考下面的[图形属性](#图形属性)
    - p:style- [ShapeStyle](../ecma-part1/chapter19/slides.md#193146-style-图形样式) - 图形样式 - 结构参考下面的[图形样式](#图形样式)

### 图片形状

- p:pic - [Picture](../ecma-part1/chapter19/slides.md#193137-pic-图片) - 图片形状
    - p:nvPicPr - [PictureNonVisual](../ecma-part1/chapter19/slides.md#193132-nvpicpr-图片的非视觉属性) - 图片形状的非视觉属性
        - p:cNvPr - [NonVisualDrawingProps](../ecma-part1/chapter20/main/basics.md#201228-cnvpr-非可视绘图属性) - 非可视绘图属性
            - a:hlinkClick - [Hyperlink](../ecma-part1/chapter21/main.md#211235-hlinkclick-单击超链接) - 单击超链接
            - a:hlinkHover - [Hyperlink](../ecma-part1/chapter20/main/basics.md#2012223-hlinkhover-悬停的超链接) - 悬停的超链接
            - 其他属性，参考文档
        - p:cNvPicPr - [NonVisualPictureProperties](../ecma-part1/chapter19/slides.md#193111-cnvpicpr-非视觉绘图属性) - 非视觉绘图属性
            - a:picLocks - [PictureLocking](../ecma-part1/chapter20/main/basics.md#2012231-piclocks-图片锁) - 图片锁定属性
            - 其他属性，参考文档
        - p:nvPr - [ApplicationNonVisualDrawingProps](../ecma-part1/chapter19/slides.md#193133-nvpr-非视觉属性) - 非视觉属性
            - p:ph - [Placeholder](../ecma-part1/chapter19/slides.md#193136-ph-占位符形状) - 占位符形状
            - media - 媒体 [可选][5选1]
                - a:audioCd - [AudioCD](../ecma-part1/chapter20/main/audioandvideo.md#20131-audiocd-cd-中的音频) - CD 中的音频
                - a:wavAudioFile - [EmbeddedWAVAudioFile](../ecma-part1/chapter20/main/audioandvideo.md#20137-wavaudiofile-wav-文件中的音频) - WAV 音频文件
                - a:audioFile - [AudioFile](../ecma-part1/chapter20/main/audioandvideo.md#20132-audiofile-文件中的音频) - 文件中的音频
                - a:videoFile - [VideoFile](../ecma-part1/chapter20/main/audioandvideo.md#20136-videofile-文件中的视频) - 文件中的视频
                - a:quickTimeFile - [QuickTimeFile](../ecma-part1/chapter20/main/audioandvideo.md#20134-quicktimefile-来自文件的-quicktime) - 文件的 QuickTime
    - p:blipFill - [BlipFillProperties](../ecma-part1/chapter19/slides.md#193132-nvpicpr-图片的非视觉属性)
    - p:spPr - [ShapeProperties](../ecma-part1/chapter19/slides.md#193144-sppr-图形属性) - 图形属性 - 结构参考下面的[图形属性](#图形属性)
    - p:style- [ShapeStyle](../ecma-part1/chapter19/slides.md#193146-style-图形样式) - 图形样式 - 结构参考下面的[图形样式](#图形样式)
    - 其他属性，参考文档

### 内容部件形状

此元素指定对 XML 内容的引用，其格式未由 ECMA-376 定义。

    这部分允许本机使用其他常用的交换格式，例如：

    - MathML (http://www.w3.org/TR/MathML2/)
    - SMIL (http://www.w3.org/TR/REC-smil/)
    - SVG (http://www.w3.org/TR/SVG11/)

- p:contentPart - [Rel](../ecma-part1/chapter19/slides.md#193114-contentpart-内容部分) - 内容部件内容
    - relationship_id - 关系ID - 指定内容部件的关系 ID.

### 组合形状

- p:grpSp - [GroupShape](../ecma-part1/chapter19/slides.md#193122-grpsp-组合图形) - 组合形状
    - p:nvGrpSpPr - [GroupShapeNonVisual](../ecma-part1/chapter19/slides.md#193131-nvgrpsppr-组合形状的非视觉属性) - 组合形状的非视觉属性
        - p:cNvPr - [NonVisualDrawingProps](../ecma-part1/chapter20/main/basics.md#201228-cnvpr-非可视绘图属性) - 非可视绘图属性
            - a:hlinkClick - [Hyperlink](../ecma-part1/chapter21/main.md#211235-hlinkclick-单击超链接) - 单击超链接
            - a:hlinkHover - [Hyperlink](../ecma-part1/chapter20/main/basics.md#2012223-hlinkhover-悬停的超链接) - 悬停的超链接
            - 其他属性，参考文档
        - p:cNvGrpSpPr - [NonVisualGroupDrawingShapeProps](../ecma-part1/chapter20/main/basics.md#201226-cnvgrpsppr-非可视组形状绘图属性) - 非可视组形状绘图属性
            - a:grpSpLocks - [GroupLocking](../ecma-part1/chapter20/main/basics.md#2012221-grpsplocks-组合形状锁) - 组合形状锁定信息
                - 其他属性，参考文档
        - p:nvPr - [ApplicationNonVisualDrawingProps](../ecma-part1/chapter19/slides.md#193133-nvpr-非视觉属性) - 非视觉属性
            - p:ph - [Placeholder](../ecma-part1/chapter19/slides.md#193136-ph-占位符形状) - 占位符形状
            - media - 媒体 [可选][5选1]
                - a:audioCd - [AudioCD](../ecma-part1/chapter20/main/audioandvideo.md#20131-audiocd-cd-中的音频) - CD 中的音频
                - a:wavAudioFile - [EmbeddedWAVAudioFile](../ecma-part1/chapter20/main/audioandvideo.md#20137-wavaudiofile-wav-文件中的音频) - WAV 音频文件
                - a:audioFile - [AudioFile](../ecma-part1/chapter20/main/audioandvideo.md#20132-audiofile-文件中的音频) - 文件中的音频
                - a:videoFile - [VideoFile](../ecma-part1/chapter20/main/audioandvideo.md#20136-videofile-文件中的视频) - 文件中的视频
                - a:quickTimeFile - [QuickTimeFile](../ecma-part1/chapter20/main/audioandvideo.md#20134-quicktimefile-来自文件的-quicktime) - 文件的 QuickTime
    - p:grpSpPr - [GroupShapeProperties](../ecma-part1/chapter19/slides.md#193123-grpsppr-组合图形属性) - 组合图形属性
    - shape_list - 形状列表 联合类型
        - p:sp - [Shape](../ecma-part1/chapter19/slides.md#193143-sp-图形) - 形状(常规形状) - 结构参考上面的[常规形状](#常规形状)
        - p:grpSp - [GroupShape](../ecma-part1/chapter19/slides.md#193122-grpsp-组合图形) - 组合形状 - 结构参考上面的[组合形状](#组合形状)
        - p:graphicFrame - [GraphicalObjectFrame](../ecma-part1/chapter19/slides.md#193121-graphicframe-图框) - 结构参考上面的[图框形状](#图框形状)
        - p:cxnSp - [Connector](../ecma-part1/chapter19/slides.md#193119-cxnsp-连接形状) - 连接形状 - 结构参考上面的[链接线结构](#链接线结构)
        - p:pic - [Picture](../ecma-part1/chapter19/slides.md#193137-pic-图片) - 图片形状 - 结构参考上面的[图片形状](#图片形状)
        - p:contentPart - [Rel](../ecma-part1/chapter19/slides.md#193114-contentpart-内容部分) - 内容部件内容 - 结构参考上面的[内容部件形状](#内容部件形状)

## 通用结构

### 非可视绘图属性

- p:nvSpPr - [ShapeNonVisual](../ecma-part1/chapter19/slides.md#193134-nvsppr-形状的非视觉属性) - 形状的非视觉属性
    - p:cNvPr - [NonVisualDrawingProps](../ecma-part1/chapter20/main/basics.md#201228-cnvpr-非可视绘图属性) - 非可视绘图属性
        - a:hlinkClick - [Hyperlink](../ecma-part1/chapter21/main.md#211235-hlinkclick-单击超链接) - 单击超链接
        - a:hlinkHover - [Hyperlink](../ecma-part1/chapter20/main/basics.md#2012223-hlinkhover-悬停的超链接) - 悬停的超链接
        - 其他属性，参考文档
    - p:cNvSpPr - [NonVisualDrawingShapeProps](../ecma-part1/chapter19/slides.md#193113-cnvsppr-形状的非可视绘图属性) - 形状的非可视绘图属性
        - a:spLocks - [NonVisualDrawingShapeProps](../ecma-part1/chapter19/slides.md#193113-cnvsppr-形状的非可视绘图属性) - 形状锁定属性
            - 其他属性，参考文档
        - text_box - 是否为文本框
        - 其他属性，参考文档
    - p:nvPr - [ApplicationNonVisualDrawingProps](../ecma-part1/chapter19/slides.md#193133-nvpr-非视觉属性) - 非视觉属性
        - p:ph - [Placeholder](../ecma-part1/chapter19/slides.md#193136-ph-占位符形状) - 占位符形状
        - media - 媒体 [可选][5选1]
            - a:audioCd - [AudioCD](../ecma-part1/chapter20/main/audioandvideo.md#20131-audiocd-cd-中的音频) - CD 中的音频
            - a:wavAudioFile - [EmbeddedWAVAudioFile](../ecma-part1/chapter20/main/audioandvideo.md#20137-wavaudiofile-wav-文件中的音频) - WAV 音频文件
            - a:audioFile - [AudioFile](../ecma-part1/chapter20/main/audioandvideo.md#20132-audiofile-文件中的音频) - 文件中的音频
            - a:videoFile - [VideoFile](../ecma-part1/chapter20/main/audioandvideo.md#20136-videofile-文件中的视频) - 文件中的视频
            - a:quickTimeFile - [QuickTimeFile](../ecma-part1/chapter20/main/audioandvideo.md#20134-quicktimefile-来自文件的-quicktime) - 文件的 QuickTime


### 图形属性

- p:spPr - [ShapeProperties](../ecma-part1/chapter19/slides.md#193144-sppr-图形属性) - 图形属性 - 结构参考下面的[图形属性](#图形属性)
    - a:xfrm - [Transform2D](../ecma-part1/chapter19/slides.md#193153-xfrm-图形框架的-2d-变换) - 2d-变换
    - geometry - 【2选1】
        - a:custGeom - [CustomGeometry2D](../ecma-part1/chapter20/main/shape_definitions.md#20198-custgeom-定制几何形状) - 定制几何形状
        - a:prstGeom - [PresetGeometry2D](../ecma-part1/chapter20/main/shape_definitions.md#201918-prstgeom-预设几何形状) - 预设几何形状
    - fill - 填充样式 [可选][6选1]
        - a:noFill - [NoFillProperties](../ecma-part1/chapter20/main/shape_fill.md#201844-nofill-无填充) - 无填充
        - a:solidFill - [SolidColorFillProperties](../ecma-part1/chapter20/main/shape_fill.md#201854-solidfill-实心填充) - 实心填充
        - a:gradFill - [GradientFillProperties](../ecma-part1/chapter20/main/shape_fill.md#201833-gradfill-渐变填充) - 渐变填充
        - a:blipFill - [BlipFillProperties](../ecma-part1/chapter20/main/shape_fill.md#201814-blipfill-图片填充) - 图片填充
        - a:pattFill - [PatternFillProperties](../ecma-part1/chapter20/main/shape_fill.md#201847-pattfill-图案填充) - 图案填充
        - a:grpFill - [GroupFillProperties](../ecma-part1/chapter20/main/shape_fill.md#201835-grpfill-组合填充)
    - a:ln - [LineProperties](../ecma-part1/chapter20/main/basics.md#2012224-ln-大纲) - 线/轮廓特性/属性
    - effect - 效果样式 [可选][2选1]
        - a:effectLst - [EffectList](../ecma-part1/chapter20/main/shape_fill.md#201826-effectlst-效果列表) - 效果列表
        - a:effectDag - [EffectContainer](../ecma-part1/chapter20/main/shape_fill.md#201820-cont-效果容器) - 效果容器
    - a:scene3d - [Scene3D](../ecma-part1/chapter20/main/styles.md#2014126-scene3d-3d-场景属性) - 3D场景属性
    - a:sp3d - [Shape3D](../ecma-part1/chapter20/main/styles.md#21456-xxx) - 3D形状属性 - 未翻译
    - 其他属性，参考文档

### 图形样式

- p:style- [ShapeStyle](../ecma-part1/chapter19/slides.md#193146-style-图形样式) - 图形样式
    - a:lnRef - [StyleMatrixReference](../ecma-part1/chapter20/main/styles.md#2014219-lnref-线条样式引用) - 线条样式引用
        - color - [可选][6选1]
            - a:scrgbClr - [ScRgbColor](../ecma-part1/chapter20/main/basics.md#2012330-scrgbclr-rgb-颜色模型---百分比变体) - rgb-颜色模型---百分比变体
            - a:srgbClr - [SRgbColor](../ecma-part1/chapter20/main/basics.md#2012332-srgbclr-rgb-颜色模型---十六进制变体) - rgb-颜色模型---十六进制变体
            - a:hslClr - [HslColor](../ecma-part1/chapter20/main/basics.md#2012313-hslclr-色相饱和度亮度颜色模型) - 色相饱和度亮度颜色模型
            - a:sysClr - [SystemColor](../ecma-part1/chapter20/main/basics.md#2012333-sysclr-系统颜色) - 系统颜色
            - a:schemeClr - [SchemeColor](../ecma-part1/chapter20/main/basics.md#2012329-schemeclr-方案颜色) - 方案颜色
            - a:prstClr - [PresetColor](../ecma-part1/chapter20/main/basics.md#2012322-prstclr-预设颜色) - 预设颜色
        - 其他属性，参考文档
    - a:fillRef - [StyleMatrixReference](../ecma-part1/chapter20/main/styles.md#2014210-fillref-填充引用) - 填充引用
        - color - [可选][6选1]
            - a:scrgbClr - [ScRgbColor](../ecma-part1/chapter20/main/basics.md#2012330-scrgbclr-rgb-颜色模型---百分比变体) - rgb-颜色模型---百分比变体
            - a:srgbClr - [SRgbColor](../ecma-part1/chapter20/main/basics.md#2012332-srgbclr-rgb-颜色模型---十六进制变体) - rgb-颜色模型---十六进制变体
            - a:hslClr - [HslColor](../ecma-part1/chapter20/main/basics.md#2012313-hslclr-色相饱和度亮度颜色模型) - 色相饱和度亮度颜色模型
            - a:sysClr - [SystemColor](../ecma-part1/chapter20/main/basics.md#2012333-sysclr-系统颜色) - 系统颜色
            - a:schemeClr - [SchemeColor](../ecma-part1/chapter20/main/basics.md#2012329-schemeclr-方案颜色) - 方案颜色
            - a:prstClr - [PresetColor](../ecma-part1/chapter20/main/basics.md#2012322-prstclr-预设颜色) - 预设颜色
        - 其他属性，参考文档
    - a:effectRef - [StyleMatrixReference](../ecma-part1/chapter20/main/styles.md#201428-effectref-效果引用) - 效果引用
        - color - [可选][6选1]
            - a:scrgbClr - [ScRgbColor](../ecma-part1/chapter20/main/basics.md#2012330-scrgbclr-rgb-颜色模型---百分比变体) - rgb-颜色模型---百分比变体
            - a:srgbClr - [SRgbColor](../ecma-part1/chapter20/main/basics.md#2012332-srgbclr-rgb-颜色模型---十六进制变体) - rgb-颜色模型---十六进制变体
            - a:hslClr - [HslColor](../ecma-part1/chapter20/main/basics.md#2012313-hslclr-色相饱和度亮度颜色模型) - 色相饱和度亮度颜色模型
            - a:sysClr - [SystemColor](../ecma-part1/chapter20/main/basics.md#2012333-sysclr-系统颜色) - 系统颜色
            - a:schemeClr - [SchemeColor](../ecma-part1/chapter20/main/basics.md#2012329-schemeclr-方案颜色) - 方案颜色
            - a:prstClr - [PresetColor](../ecma-part1/chapter20/main/basics.md#2012322-prstclr-预设颜色) - 预设颜色
        - 其他属性，参考文档
    - a:fontRef - [FontReference](../ecma-part1/chapter20/main/styles.md#2014117-fontref-字体引用) - 字体引用
        - color - [可选][6选1]
            - a:scrgbClr - [ScRgbColor](../ecma-part1/chapter20/main/basics.md#2012330-scrgbclr-rgb-颜色模型---百分比变体) - rgb-颜色模型---百分比变体
            - a:srgbClr - [SRgbColor](../ecma-part1/chapter20/main/basics.md#2012332-srgbclr-rgb-颜色模型---十六进制变体) - rgb-颜色模型---十六进制变体
            - a:hslClr - [HslColor](../ecma-part1/chapter20/main/basics.md#2012313-hslclr-色相饱和度亮度颜色模型) - 色相饱和度亮度颜色模型
            - a:sysClr - [SystemColor](../ecma-part1/chapter20/main/basics.md#2012333-sysclr-系统颜色) - 系统颜色
            - a:schemeClr - [SchemeColor](../ecma-part1/chapter20/main/basics.md#2012329-schemeclr-方案颜色) - 方案颜色
            - a:prstClr - [PresetColor](../ecma-part1/chapter20/main/basics.md#2012322-prstclr-预设颜色) - 预设颜色
        - 其他属性，参考文档


### 正文格式

- p:txBody - [TextBody](../ecma-part1/chapter21/main.md#21121-正文格式) - 正文格式
    - p:bodyPr - [TextBodyProperties](../ecma-part1/chapter21/main.md#211211-bodypr-正文属性) - 正文特性(属性)
        - a:prstTxWarp - [PresetTextShape](../ecma-part1/chapter20/main/shape_definitions.md#201919-prsttxwarp-预设文本变形) - 预设文本变形(扭曲) - 可选
        - autofit - 文本自适应方式 - 3 选 1
            - a:noAutofit - [TextNoAutofit](../ecma-part1/chapter21/main.md#211212-noautofit-不自动调整) - 不自动调整
            - a:normAutofit - [TextNormalAutofit](../ecma-part1/chapter21/main.md#211213-normautofit-正常自动调整) - 正常自动调整
                - 其他属性，参考文档
            - a:spAutoFit - [TextShapeAutofit](../ecma-part1/chapter21/main.md#211214-spautofit-形状自动调整) - 形状自动调整
        - a:scene3d - [Scene3D](../ecma-part1/chapter20/main/styles.md#2014126-scene3d-3d-场景属性) - 3D场景属性
    - p:lstStyle - [TextListStyle](../ecma-part1/chapter21/main.md#2112412-lststyle-文本列表样式) - 文本列表样式
        - a:defPPr - [TextParagraphProperties](../ecma-part1/chapter21/main.md#211222-defppr-默认段落样式) - 默认段落样式
        - a:lvl1pPr - [TextParagraphProperties](../ecma-part1/chapter21/main.md#2112413-lvl1ppr-列表级别-1-文本样式) - 列表级别-1-文本样式
        - a:lvl2pPr - [TextParagraphProperties](../ecma-part1/chapter21/main.md#2112414-lvl2ppr-列表级别-2-文本样式) - 列表级别-2-文本样式
        - ...
        - a:lvl9pPr - [TextParagraphProperties](../ecma-part1/chapter21/main.md#2112421-lvl9ppr-列表级别-9-文本样式) - 列表级别-9-文本样式
    - p:p - [TextParagraph](../ecma-part1/chapter21/main.md#211226-p-文本段落) - 文本段落 - 列表
        - a:pPr - [TextParagraphProperties](../ecma-part1/chapter21/main.md#211227-ppr-文本段落特性) - 文本段落特性(属性)
            - a:lnSpc - [TextSpacing](../ecma-part1/chapter21/main.md#211225-lnspc-行间距) - 段行间距
            - a:spcBef - [TextSpacing](../ecma-part1/chapter21/main.md#2112210-spcbef-前间距) - 段前间距
            - a:spcAft - [TextSpacing](../ecma-part1/chapter21/main.md#211229-spcaft-后间距) - 段后间距
            - text_bullet_color - 项目列表符号颜色 [可选][2选1]
                - a:buClrTx - [TextBulletColorFollowText](../ecma-part1/chapter21/main.md#211245-buclrtx-跟随文字) - 跟随文字
                - a:buClr - [Color](../ecma-part1/chapter21/main.md#211244-buclr-指定颜色) - 指定颜色
            - text_bullet_size - 项目列表符号尺寸 [可选][3选1]
                - a:buSzTx - [TextBulletColorFollowText](../ecma-part1/chapter21/main.md#2112411-busztx-项目符号大小跟随文本) - 项目符号大小跟随文本
                - a:buSzPct - [TextBulletSizePercent](../ecma-part1/chapter21/main.md#211249-buszpct-项目符号大小百分比) - 项目符号大小百分比
                - a:buSzPts - [TextBulletSizePoint](../ecma-part1/chapter21/main.md#2112410-buszpts-项目符号大小points) - 项目符号大小points
            - text_bullet_typeface - 项目列表符号字体 [可选][2选1]
                - a:buFontTx - [TextBulletTypefaceFollowText](../ecma-part1/chapter21/main.md#211247-bufonttx-跟随文字) - 跟随文字
                - a:buFont - [TextFont](../ecma-part1/chapter21/main.md#211246-bufont-特定字体) - 特定字体
            - text_bullet - 项目列表符号类型 [可选][4选1]
                - a:buNone - [TextNoBullet](../ecma-part1/chapter21/main.md#211248-bunone-无项目符号) - 无项目符号
                - a:buAutoNum - [TextAutonumberBullet](../ecma-part1/chapter21/main.md#211241-buautonum-自动编号项目符号) - 自动编号项目符号
                - a:buChar - [TextCharBullet](../ecma-part1/chapter21/main.md#211243-buchar-字符项目符号) - 字符项目符号
                - a:buBlip - [TextBlipBullet](../ecma-part1/chapter21/main.md#211242-bublip-图片项目符号) - 图片项目符号
            - a:tabLst - tab_lst - [TextTabStopList](../ecma-part1/chapter21/main.md#2112214-tablst-制表位列表) - 制表位列表
            - a:defRPr - default_RPr - [TextCharacterProperties](../ecma-part1/chapter21/main.md#211232-defrpr-默认文本运行特性) - 默认文本运行特性
            - 其他属性，参考文档
        - runs - 文本字符 - 3选1
            - a:r - [RegularTextRun](../ecma-part1/chapter21/main.md#211238-r-文本运行) - 文本运行
                - a:rPr - [TextCharacterProperties](../ecma-part1/chapter21/main.md#211239-rpr-文本运行特性) - 文本字符属性
                    - a:ln - [LineProperties](../ecma-part1/chapter20/main/basics.md#2012224-ln-大纲) - 线/轮廓特性/属性
                    - fill - 填充样式 [可选][6选1]
                        - a:noFill - [NoFillProperties](../ecma-part1/chapter20/main/shape_fill.md#201844-nofill-无填充) - 无填充
                        - a:solidFill - [SolidColorFillProperties](../ecma-part1/chapter20/main/shape_fill.md#201854-solidfill-实心填充) - 实心填充
                        - a:gradFill - [GradientFillProperties](../ecma-part1/chapter20/main/shape_fill.md#201833-gradfill-渐变填充) - 渐变填充
                        - a:blipFill - [BlipFillProperties](../ecma-part1/chapter20/main/shape_fill.md#201814-blipfill-图片填充) - 图片填充
                        - a:pattFill - [PatternFillProperties](../ecma-part1/chapter20/main/shape_fill.md#201847-pattfill-图案填充) - 图案填充
                        - a:grpFill - [GroupFillProperties](../ecma-part1/chapter20/main/shape_fill.md#201835-grpfill-组合填充)
                    - effect - 效果样式 [可选][2选1]
                        - a:effectLst - [EffectList](../ecma-part1/chapter20/main/shape_fill.md#201826-effectlst-效果列表) - 效果列表
                        - a:effectDag - [EffectContainer](../ecma-part1/chapter20/main/shape_fill.md#201820-cont-效果容器) - 效果容器
                    - a:highlight - [Color](../ecma-part1/chapter21/main.md#211234-highlight-高亮颜色) - 高亮颜色
                    - text_underline_line - 下划线类型 [可选][2选1]
                        - a:uLnTx - [TextUnderlineLineFollowText](../ecma-part1/chapter21/main.md#2112315-ulntx-下划线跟随文本) - 下划线跟随文本
                        - a:ln - [LineProperties](../ecma-part1/chapter20/main/basics.md#2012224-ln-大纲) - 下划线=/轮廓特性/属性
                    - text_underline_fill - 下划线填充样式 [可选][2选1]
                        - a:uFillTx - [TextUnderlineFillFollowText](../ecma-part1/chapter21/main.md#2112313-ufilltx-下划线填充属性跟随文本) - 下划线填充属性跟随文本
                        - a:uFill - [TextUnderlineFillGroupWrapper](../ecma-part1/chapter21/main.md#2112312-ufill-下划线填充) - 下划线填充
                    - a:latin - [TextFont](../ecma-part1/chapter21/main.md#211237-latin-拉丁字体) - 拉丁字体
                    - a:ea - [TextFont](../ecma-part1/chapter21/main.md#211233-ea-东亚字体) - 东亚字体
                    - a:cs - [TextFont](../ecma-part1/chapter21/main.md#211231-cs-复杂脚本字体) - 复杂脚本字体
                    - a:sym - [TextFont](../ecma-part1/chapter21/main.md#2112310-sym-符号字体) - 符号字体
                    - a:hlinkClick - [Hyperlink](../ecma-part1/chapter21/main.md#211235-hlinkclick-单击超链接) - 单击超链接
                    - a:hlinkMouseOver - [Hyperlink](../ecma-part1/chapter21/main.md#211235-hlinkclick-单击超链接) - 鼠标悬停超链接
                    - a:rtl - [Boolean](../ecma-part1/chapter21/main.md#211228-rtl-run从右向左) - run从右向左
                    - 其他属性，参考文档
                - a:t - [TextCharacterProperties](../ecma-part1/chapter21/main.md#211236-hlinkmouseover-鼠标悬停超链接) - 文本字符串
            - a:br - [TextLineBreak](../ecma-part1/chapter21/main.md#211221-br-文本换行) - 文本换行
                - a:rPr - [TextCharacterProperties](../ecma-part1/chapter21/main.md#211239-rpr-文本运行特性) - 文本字符属性
            - a:fld - [TextField](../ecma-part1/chapter21/main.md#211224-fld-文本域) - 文本域
                - a:rPr - [TextCharacterProperties](../ecma-part1/chapter21/main.md#211239-rpr-文本运行特性) - 文本字符属性
                - a:pPr - [TextParagraphProperties](../ecma-part1/chapter21/main.md#211227-ppr-文本段落特性) - 文本段落特性(属性)
                - a:t - [TextCharacterProperties](../ecma-part1/chapter21/main.md#2112311-t-文本字符串) - 文本字符串
        - a:endParaRPr - [TextCharacterProperties](../ecma-part1/chapter21/main.md#211223-endpararpr-段落结尾的运行属性) - 段落结尾的运行属性