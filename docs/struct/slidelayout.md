# 幻灯片布局部件结构

## 根结构

- p:sldLayout - [SlideLayout](../ecma-part1/chapter19/slides.md#193139-sldlayout-幻灯片布局版式) - 幻灯片布局
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
            - p:sp - [Shape](../ecma-part1/chapter19/slides.md#193143-sp-图形) - 形状(常规形状) - 结构参考上面的[常规形状](./slide.md#常规形状)
            - p:grpSp - [GroupShape](../ecma-part1/chapter19/slides.md#193122-grpsp-组合图形) - 组合形状 - 结构参考上面的[组合形状](./slide.md#组合形状)
            - p:graphicFrame - [GraphicalObjectFrame](../ecma-part1/chapter19/slides.md#193121-graphicframe-图框) - 结构参考上面的[图框形状](./slide.md#图框形状)
            - p:cxnSp - [Connector](../ecma-part1/chapter19/slides.md#193119-cxnsp-连接形状) - 连接形状 - 结构参考上面的[链接线结构](./slide.md#链接线结构)
            - p:pic - [Picture](../ecma-part1/chapter19/slides.md#193137-pic-图片) - 图片形状 - 结构参考上面的[图片形状](./slide.md#图片形状)
            - p:contentPart - [Rel](../ecma-part1/chapter19/slides.md#193114-contentpart-内容部分) - 内容部件内容 - 结构参考上面的[内容部件形状](./slide.md#内容部件形状)
        - p:custDataLst - [CustomerDataList](../ecma-part1/chapter19/slides.md#193118-custdatalst-客户资料清单) - 自定义数据
        - p:controls - [ControlList](../ecma-part1/chapter19/slides.md#193115-controls-控件列表) - 控件列表
        - 其他属性，参考文档
    - p:transition - [SlideTransition](../ecma-part1/chapter19/slides.md#193150-transition-幻灯片布局的幻灯片过渡) - 幻灯片动画数据
    - p:timing - [SlideTiming](../ecma-part1/chapter19/slides.md#193148-timing-幻灯片布局的幻灯片计时信息) - 幻灯片动画计时数据
    - p:hf - [HeaderFooter](../ecma-part1/chapter19/slides.md#193125-hf-幻灯片母版的页眉页脚信息) - 页眉页脚信息
        - 其他属性，参考文档
    - 其他属性，参考文档