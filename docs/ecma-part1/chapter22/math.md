# 22.1 Math

=== "中文"

    以下文档指定了 OOXML 数学文本的 XML 表示形式。 这种共享的 ML 称为 Office 数学标记语言 (OMML)。 OMML表示的数学文本包括但不限于：方程、表达式、公式、矩阵和其他数学元素。 显示模式下数学文本实例的最外层 OMML 元素是 oMathPara，一个或多个数学文本实例的数学段落。 数学段落内数学文本的每个实例都表示为单个 oMath。 每个 oMath 内部都是数学运算 (r) 和对象或函数（例如重音符号 (acc) 或分数 (f)）的组合。

=== "英文"

    The following documentation specifies the XML representation of mathematical text for OOXML. This shared ML is known as that Office Math Markup Language (OMML). Mathematical text represented by OMML includes but is not limited to: equations, expressions, formulas, matrices, and other mathematical elements. The outermost OMML element of an instance of mathematical text in display mode is oMathPara, a math paragraph of one or more instances of mathematical text. Each instance of mathematical text inside the math paragraph is represented as a single oMath. Inside each oMath is a combination of mathematical runs (r) and objects or functions such as accents (acc) or fractions (f).

## 目录

"Table of Contents"

This subclause is informative.

- 22.1.2 Elements
    - 22.1.2.1 acc (Accent)
    - 22.1.2.2 accPr (Accent Properties)
    - 22.1.2.3 aln (Alignment)
    - 22.1.2.4 alnScr (Align Scripts)
    - 22.1.2.5 argPr (Argument Properties)
    - 22.1.2.6 argSz (Argument Size)
    - 22.1.2.7 bar (Bar)
    - 22.1.2.8 barPr (Bar Properties)
    - 22.1.2.9 baseJc (Matrix Base Justification)
    - 22.1.2.10 begChr (Delimiter Beginning Character)
    - 22.1.2.11 borderBox (Border-Box Object)
    - 22.1.2.12 borderBoxPr (Border-Box Properties)
    - 22.1.2.13 box (Box Object)
    - 22.1.2.14 boxPr (Box Properties)
    - 22.1.2.15 brk (Break)
    - 22.1.2.16 brkBin (Break on Binary Operators)
    - 22.1.2.17 brkBinSub (Break on Binary Subtraction)
    - 22.1.2.18 cGp (Matrix Column Gap)
    - 22.1.2.19 cGpRule (Matrix Column Gap Rule)
    - 22.1.2.20 chr (Character)
    - 22.1.2.21 count (Matrix Column Count)
    - 22.1.2.22 cSp (Minimum Matrix Column Width)
    - 22.1.2.23 ctrlPr (Control Properties)
    - 22.1.2.24 d (Delimiter Object)
    - 22.1.2.25 defJc (Default Justification)
    - 22.1.2.26 deg (Degree)
    - 22.1.2.27 degHide (Hide Degree)
    - 22.1.2.28 den (Denominator)
    - 22.1.2.29 diff (Differential)
    - 22.1.2.30 dispDef (Use Display Math Defaults)
    - 22.1.2.31 dPr (Delimiter Properties)
    - 22.1.2.32 e (Element (Argument))
    - 22.1.2.33 endChr (Delimiter Ending Character)
    - 22.1.2.34 eqArr (Array Object)
    - 22.1.2.35 eqArrPr (Array Properties)
    - 22.1.2.36 f (Fraction Object)
    - 22.1.2.37 fName (Function Name)
    - 22.1.2.38 fPr (Fraction Properties)
    - 22.1.2.39 func (Function Apply Object)
    - 22.1.2.40 funcPr (Function Properties)
    - 22.1.2.41 groupChr (Group-Character Object)
    - 22.1.2.42 groupChrPr (Group-Character Properties)
    - 22.1.2.43 grow (n-ary Grow)
    - 22.1.2.44 hideBot (Hide Bottom Edge)
    - 22.1.2.45 hideLeft (Hide Left Edge)
    - 22.1.2.46 hideRight (Hide Right Edge)
    - 22.1.2.47 hideTop (Hide Top Edge)
    - 22.1.2.48 interSp (Inter-Equation Spacing)
    - 22.1.2.49 intLim (Integral Limit Locations)
    - 22.1.2.50 intraSp (Intra-Equation Spacing)
    - 22.1.2.51 jc (Justification)
    - 22.1.2.52 lim (Limit)
    - 22.1.2.53 limLoc (n-ary Limit Location)
    - 22.1.2.54 limLow (Lower-Limit Object)
    - 22.1.2.55 limLowPr (Lower-Limit Properties)
    - 22.1.2.56 limUpp (Upper-Limit Object)
    - 22.1.2.57 limUppPr (Upper-Limit Properties)
    - 22.1.2.58 lit (Literal)
    - 22.1.2.59 lMargin (Left Margin)
    - 22.1.2.60 m (Matrix Object)
    - 22.1.2.61 mathFont (Math Font)
    - 22.1.2.62 mathPr (Math Properties)
    - 22.1.2.63 maxDist (Maximum Distribution)
    - 22.1.2.64 mc (Matrix Column)
    - 22.1.2.65 mcJc (Matrix Column Justification)
    - 22.1.2.66 mcPr (Matrix Column Properties)
    - 22.1.2.67 mcs (Matrix Columns)
    - 22.1.2.68 mPr (Matrix Properties)
    - 22.1.2.69 mr (Matrix Row)
    - 22.1.2.70 nary (n-ary Operator Object)
    - 22.1.2.71 naryLim (n-ary Limit Location)
    - 22.1.2.72 naryPr (n-ary Properties)
    - 22.1.2.73 noBreak (No Break)
    - 22.1.2.74 nor (Normal Text)
    - 22.1.2.75 num (Numerator)
    - 22.1.2.76 objDist (Object Distribution)
    - 22.1.2.77 oMath (Office Math)
    - 22.1.2.78 oMathPara (Office Math Paragraph)
    - 22.1.2.79 oMathParaPr (Office Math Paragraph Properties)
    - 22.1.2.80 opEmu (Operator Emulator)
    - 22.1.2.81 phant (Phantom Object)
    - 22.1.2.82 phantPr (Phantom Properties)
    - 22.1.2.83 plcHide (Hide Placeholders (Matrix))
    - 22.1.2.84 pos (Position)
    - 22.1.2.85 postSp (Post-Paragraph Spacing)
    - 22.1.2.86 preSp (Pre-Paragraph Spacing)
    - 22.1.2.87 r (Run)
    - 22.1.2.88 rad (Radical Object)
    - 22.1.2.89 radPr (Radical Properties)
    - 22.1.2.90 rMargin (Right Margin)
    - 22.1.2.91 rPr (Run Properties)
    - 22.1.2.92 rSp (Row Spacing (Array))
    - 22.1.2.93 rSpRule (Row Spacing Rule)
    - 22.1.2.94 scr (Script)
    - 22.1.2.95 sepChr (Delimiter Separator Character)
    - 22.1.2.96 show (Phantom Show)
    - 22.1.2.97 shp (Shape (Delimiters))
    - 22.1.2.98 smallFrac (Small Fraction)
    - 22.1.2.99 sPre (Pre-Sub-Superscript Object)
    - 22.1.2.100 sPrePr (Pre-Sub-Superscript Properties)
    - 22.1.2.101 sSub (Subscript Object)
    - 22.1.2.102 sSubPr (Subscript Properties)
    - 22.1.2.103 sSubSup (Sub-Superscript Object)
    - 22.1.2.104 sSubSupPr (Sub-Superscript Properties)
    - 22.1.2.105 sSup (Superscript Object)
    - 22.1.2.106 sSupPr (Superscript Properties)
    - 22.1.2.107 strikeBLTR (Border Box Strikethrough Bottom-Left to Top-Right)
    - 22.1.2.108 strikeH (Border Box Strikethrough Horizontal)
    - 22.1.2.109 strikeTLBR (Border Box Strikethrough Top-Left to Bottom-Right)
    - 22.1.2.110 strikeV (Border Box Strikethrough Vertical)
    - 22.1.2.111 sty (style)
    - 22.1.2.112 sub (Subscript (Pre-Sub-Superscript))
    - 22.1.2.113 subHide (Hide Subscript (n-ary))
    - 22.1.2.114 sup (Superscript (Superscript object))
    - 22.1.2.115 supHide (Hide Superscript (n-ary))
    - 22.1.2.116 t (Text)
    - 22.1.2.117 transp (Transparent (Phantom))
    - 22.1.2.118 type (Fraction type)
    - 22.1.2.119 vertJc (Vertical Justification)
    - 22.1.2.120 wrapIndent (Wrap Indent)
    - 22.1.2.121 wrapRight (Wrap Right)
    - 22.1.2.122 zeroAsc (Phantom Zero Ascent)
    - 22.1.2.123 zeroDesc (Phantom Zero Descent)
    - 22.1.2.124 zeroWid (Phantom Zero Width)
- 22.1.3 Simple Types
    - 22.1.3.1 ST_BreakBin (Break Binary Operators)
    - 22.1.3.2 ST_BreakBinSub (Break on Binary Subtraction)
    - 22.1.3.3 ST_Char (Character)
    - 22.1.3.4 ST_FType (Fraction Type)
    - 22.1.3.5 ST_Integer2 (Integer value (-2 to 2))
    - 22.1.3.6 ST_Integer255 (Integer value (1 to 255))
    - 22.1.3.7 ST_Jc (Justification)
    - 22.1.3.8 ST_LimLoc (Limit Location)
    - 22.1.3.9 ST_Script (Script)
    - 22.1.3.10 ST_Shp (Shape (Delimiters))
    - 22.1.3.11 ST_SpacingRule (Spacing Rule)
    - 22.1.3.12 ST_Style (Style)
    - 22.1.3.13 ST_TopBot (Top-Bottom)
    - 22.1.3.14 ST_UnSignedInteger (Unsigned integer.)

End of informative text.

## 22.1.2 Elements

=== "中文"

=== "英文"

    "Elements"

### 22.1.2.1 acc (Accent)

=== "中文"

=== "英文"

    "acc (Accent)"

### 22.1.2.2 accPr (Accent Properties)

=== "中文"

=== "英文"

    "accPr (Accent Properties)"

### 22.1.2.3 aln (Alignment)

=== "中文"

=== "英文"

    "aln (Alignment)"

### 22.1.2.4 alnScr (Align Scripts)

=== "中文"

=== "英文"

    "alnScr (Align Scripts)"

### 22.1.2.5 argPr (Argument Properties)

=== "中文"

=== "英文"

    "argPr (Argument Properties)"

### 22.1.2.6 argSz (Argument Size)

=== "中文"

=== "英文"

    "argSz (Argument Size)"

### 22.1.2.7 bar (Bar)

=== "中文"

=== "英文"

    "bar (Bar)"

### 22.1.2.8 barPr (Bar Properties)

=== "中文"

=== "英文"

    "barPr (Bar Properties)"

### 22.1.2.9 baseJc (Matrix Base Justification)

=== "中文"

=== "英文"

    "baseJc (Matrix Base Justification)"

### 22.1.2.10 begChr (Delimiter Beginning Character)

=== "中文"

=== "英文"

    "begChr (Delimiter Beginning Character)"

### 22.1.2.11 borderBox (Border-Box Object)

=== "中文"

=== "英文"

    "borderBox (Border-Box Object)"

### 22.1.2.12 borderBoxPr (Border-Box Properties)

=== "中文"

=== "英文"

    "borderBoxPr (Border-Box Properties)"

### 22.1.2.13 box (Box Object)

=== "中文"

=== "英文"

    "box (Box Object)"

### 22.1.2.14 boxPr (Box Properties)

=== "中文"

=== "英文"

    "boxPr (Box Properties)"

### 22.1.2.15 brk (Break)

=== "中文"

=== "英文"

    "brk (Break)"

### 22.1.2.16 brkBin (Break on Binary Operators)

=== "中文"

=== "英文"

    "brkBin (Break on Binary Operators)"

### 22.1.2.17 brkBinSub (Break on Binary Subtraction)

=== "中文"

=== "英文"

    "brkBinSub (Break on Binary Subtraction)"

### 22.1.2.18 cGp (Matrix Column Gap)

=== "中文"

=== "英文"

    "cGp (Matrix Column Gap)"

### 22.1.2.19 cGpRule (Matrix Column Gap Rule)

=== "中文"

=== "英文"

    "cGpRule (Matrix Column Gap Rule)"

### 22.1.2.20 chr (Character)

=== "中文"

=== "英文"

    "chr (Character)"

### 22.1.2.21 count (Matrix Column Count)

=== "中文"

=== "英文"

    "count (Matrix Column Count)"

### 22.1.2.22 cSp (Minimum Matrix Column Width)

=== "中文"

=== "英文"

    "cSp (Minimum Matrix Column Width)"

### 22.1.2.23 ctrlPr (Control Properties)

=== "中文"

=== "英文"

    "ctrlPr (Control Properties)"

### 22.1.2.24 d (Delimiter Object)

=== "中文"

=== "英文"

    "d (Delimiter Object)"

### 22.1.2.25 defJc (Default Justification)

=== "中文"

=== "英文"

    "defJc (Default Justification)"

### 22.1.2.26 deg (Degree)

=== "中文"

=== "英文"

    "deg (Degree)"

### 22.1.2.27 degHide (Hide Degree)

=== "中文"

=== "英文"

    "degHide (Hide Degree)"

### 22.1.2.28 den (Denominator)

=== "中文"

=== "英文"

    "den (Denominator)"

### 22.1.2.29 diff (Differential)

=== "中文"

=== "英文"

    "diff (Differential)"

### 22.1.2.30 dispDef (Use Display Math Defaults)

=== "中文"

=== "英文"

    "dispDef (Use Display Math Defaults)"

### 22.1.2.31 dPr (Delimiter Properties)

=== "中文"

=== "英文"

    "dPr (Delimiter Properties)"

### 22.1.2.32 e (Element (Argument))

=== "中文"

=== "英文"

    "e (Element (Argument))"

### 22.1.2.33 endChr (Delimiter Ending Character)

=== "中文"

=== "英文"

    "endChr (Delimiter Ending Character)"

### 22.1.2.34 eqArr (Array Object)

=== "中文"

=== "英文"

    "eqArr (Array Object)"

### 22.1.2.35 eqArrPr (Array Properties)

=== "中文"

=== "英文"

    "eqArrPr (Array Properties)"

### 22.1.2.36 f (Fraction Object)

=== "中文"

=== "英文"

    "f (Fraction Object)"

### 22.1.2.37 fName (Function Name)

=== "中文"

=== "英文"

    "fName (Function Name)"

### 22.1.2.38 fPr (Fraction Properties)

=== "中文"

=== "英文"

    "fPr (Fraction Properties)"

### 22.1.2.39 func (Function Apply Object)

=== "中文"

=== "英文"

    "func (Function Apply Object)"

### 22.1.2.40 funcPr (Function Properties)

=== "中文"

=== "英文"

    "funcPr (Function Properties)"

### 22.1.2.41 groupChr (Group-Character Object)

=== "中文"

=== "英文"

    "groupChr (Group-Character Object)"

### 22.1.2.42 groupChrPr (Group-Character Properties)

=== "中文"

=== "英文"

    "groupChrPr (Group-Character Properties)"

### 22.1.2.43 grow (n-ary Grow)

=== "中文"

=== "英文"

    "grow (n-ary Grow)"

### 22.1.2.44 hideBot (Hide Bottom Edge)

=== "中文"

=== "英文"

    "hideBot (Hide Bottom Edge)"

### 22.1.2.45 hideLeft (Hide Left Edge)

=== "中文"

=== "英文"

    "hideLeft (Hide Left Edge)"

### 22.1.2.46 hideRight (Hide Right Edge)

=== "中文"

=== "英文"

    "hideRight (Hide Right Edge)"

### 22.1.2.47 hideTop (Hide Top Edge)

=== "中文"

=== "英文"

    "hideTop (Hide Top Edge)"

### 22.1.2.48 interSp (Inter-Equation Spacing)

=== "中文"

=== "英文"

    "interSp (Inter-Equation Spacing)"

### 22.1.2.49 intLim (Integral Limit Locations)

=== "中文"

=== "英文"

    "intLim (Integral Limit Locations)"

### 22.1.2.50 intraSp (Intra-Equation Spacing)

=== "中文"

=== "英文"

    "intraSp (Intra-Equation Spacing)"

### 22.1.2.51 jc (Justification)

=== "中文"

=== "英文"

    "jc (Justification)"

### 22.1.2.52 lim (Limit)

=== "中文"

=== "英文"

    "lim (Limit)"

### 22.1.2.53 limLoc (n-ary Limit Location)

=== "中文"

=== "英文"

    "limLoc (n-ary Limit Location)"

### 22.1.2.54 limLow (Lower-Limit Object)

=== "中文"

=== "英文"

    "limLow (Lower-Limit Object)"

### 22.1.2.55 limLowPr (Lower-Limit Properties)

=== "中文"

=== "英文"

    "limLowPr (Lower-Limit Properties)"

### 22.1.2.56 limUpp (Upper-Limit Object)

=== "中文"

=== "英文"

    "limUpp (Upper-Limit Object)"

### 22.1.2.57 limUppPr (Upper-Limit Properties)

=== "中文"

=== "英文"

    "limUppPr (Upper-Limit Properties)"

### 22.1.2.58 lit (Literal)

=== "中文"

=== "英文"

    "lit (Literal)"

### 22.1.2.59 lMargin (Left Margin)

=== "中文"

=== "英文"

    "lMargin (Left Margin)"

### 22.1.2.60 m (Matrix Object)

=== "中文"

=== "英文"

    "m (Matrix Object)"

### 22.1.2.61 mathFont (Math Font)

=== "中文"

=== "英文"

    "mathFont (Math Font)"

### 22.1.2.62 mathPr (Math Properties)

=== "中文"

=== "英文"

    "mathPr (Math Properties)"

### 22.1.2.63 maxDist (Maximum Distribution)

=== "中文"

=== "英文"

    "maxDist (Maximum Distribution)"

### 22.1.2.64 mc (Matrix Column)

=== "中文"

=== "英文"

    "mc (Matrix Column)"

### 22.1.2.65 mcJc (Matrix Column Justification)

=== "中文"

=== "英文"

    "mcJc (Matrix Column Justification)"

### 22.1.2.66 mcPr (Matrix Column Properties)

=== "中文"

=== "英文"

    "mcPr (Matrix Column Properties)"

### 22.1.2.67 mcs (Matrix Columns)

=== "中文"

=== "英文"

    "mcs (Matrix Columns)"

### 22.1.2.68 mPr (Matrix Properties)

=== "中文"

=== "英文"

    "mPr (Matrix Properties)"

### 22.1.2.69 mr (Matrix Row)

=== "中文"

=== "英文"

    "mr (Matrix Row)"

### 22.1.2.70 nary (n-ary Operator Object)

=== "中文"

=== "英文"

    "nary (n-ary Operator Object)"

### 22.1.2.71 naryLim (n-ary Limit Location)

=== "中文"

=== "英文"

    "naryLim (n-ary Limit Location)"

### 22.1.2.72 naryPr (n-ary Properties)

=== "中文"

=== "英文"

    "naryPr (n-ary Properties)"

### 22.1.2.73 noBreak (No Break)

=== "中文"

=== "英文"

    "noBreak (No Break)"

### 22.1.2.74 nor (Normal Text)

=== "中文"

=== "英文"

    "nor (Normal Text)"

### 22.1.2.75 num (Numerator)

=== "中文"

=== "英文"

    "num (Numerator)"

### 22.1.2.76 objDist (Object Distribution)

=== "中文"

=== "英文"

    "objDist (Object Distribution)"

### 22.1.2.77 oMath (Office Math)

=== "中文"

=== "英文"

    "oMath (Office Math)"

### 22.1.2.78 oMathPara (Office Math Paragraph)

=== "中文"

=== "英文"

    "oMathPara (Office Math Paragraph)"

### 22.1.2.79 oMathParaPr (Office Math Paragraph Properties)

=== "中文"

=== "英文"

    "oMathParaPr (Office Math Paragraph Properties)"

### 22.1.2.80 opEmu (Operator Emulator)

=== "中文"

=== "英文"

    "opEmu (Operator Emulator)"

### 22.1.2.81 phant (Phantom Object)

=== "中文"

=== "英文"

    "phant (Phantom Object)"

### 22.1.2.82 phantPr (Phantom Properties)

=== "中文"

=== "英文"

    "phantPr (Phantom Properties)"

### 22.1.2.83 plcHide (Hide Placeholders (Matrix))

=== "中文"

=== "英文"

    "plcHide (Hide Placeholders (Matrix))"

### 22.1.2.84 pos (Position)

=== "中文"

=== "英文"

    "pos (Position)"

### 22.1.2.85 postSp (Post-Paragraph Spacing)

=== "中文"

=== "英文"

    "postSp (Post-Paragraph Spacing)"

### 22.1.2.86 preSp (Pre-Paragraph Spacing)

=== "中文"

=== "英文"

    "preSp (Pre-Paragraph Spacing)"

### 22.1.2.87 r (Run)

=== "中文"

=== "英文"

    "r (Run)"

### 22.1.2.88 rad (Radical Object)

=== "中文"

=== "英文"

    "rad (Radical Object)"

### 22.1.2.89 radPr (Radical Properties)

=== "中文"

=== "英文"

    "radPr (Radical Properties)"

### 22.1.2.90 rMargin (Right Margin)

=== "中文"

=== "英文"

    "rMargin (Right Margin)"

### 22.1.2.91 rPr (Run Properties)

=== "中文"

=== "英文"

    "rPr (Run Properties)"

### 22.1.2.92 rSp (Row Spacing (Array))

=== "中文"

=== "英文"

    "rSp (Row Spacing (Array))"

### 22.1.2.93 rSpRule (Row Spacing Rule)

=== "中文"

=== "英文"

    "rSpRule (Row Spacing Rule)"

### 22.1.2.94 scr (Script)

=== "中文"

=== "英文"

    "scr (Script)"

### 22.1.2.95 sepChr (Delimiter Separator Character)

=== "中文"

=== "英文"

    "sepChr (Delimiter Separator Character)"

### 22.1.2.96 show (Phantom Show)

=== "中文"

=== "英文"

    "show (Phantom Show)"

### 22.1.2.97 shp (Shape (Delimiters))

=== "中文"

=== "英文"

    "shp (Shape (Delimiters))"

### 22.1.2.98 smallFrac (Small Fraction)

=== "中文"

=== "英文"

    "smallFrac (Small Fraction)"

### 22.1.2.99 sPre (Pre-Sub-Superscript Object)

=== "中文"

=== "英文"

    "sPre (Pre-Sub-Superscript Object)"

### 22.1.2.100 sPrePr (Pre-Sub-Superscript Properties)

=== "中文"

=== "英文"

    "sPrePr (Pre-Sub-Superscript Properties)"

### 22.1.2.101 sSub (Subscript Object)

=== "中文"

=== "英文"

    "sSub (Subscript Object)"

### 22.1.2.102 sSubPr (Subscript Properties)

=== "中文"

=== "英文"

    "sSubPr (Subscript Properties)"

### 22.1.2.103 sSubSup (Sub-Superscript Object)

=== "中文"

=== "英文"

    "sSubSup (Sub-Superscript Object)"

### 22.1.2.104 sSubSupPr (Sub-Superscript Properties)

=== "中文"

=== "英文"

    "sSubSupPr (Sub-Superscript Properties)"

### 22.1.2.105 sSup (Superscript Object)

=== "中文"

=== "英文"

    "sSup (Superscript Object)"

### 22.1.2.106 sSupPr (Superscript Properties)

=== "中文"

=== "英文"

    "sSupPr (Superscript Properties)"

### 22.1.2.107 strikeBLTR (Border Box Strikethrough Bottom-Left to Top-Right)

=== "中文"

=== "英文"

    "strikeBLTR (Border Box Strikethrough Bottom-Left to Top-Right)"

### 22.1.2.108 strikeH (Border Box Strikethrough Horizontal)

=== "中文"

=== "英文"

    "strikeH (Border Box Strikethrough Horizontal)"

### 22.1.2.109 strikeTLBR (Border Box Strikethrough Top-Left to Bottom-Right)

=== "中文"

=== "英文"

    "strikeTLBR (Border Box Strikethrough Top-Left to Bottom-Right)"

### 22.1.2.110 strikeV (Border Box Strikethrough Vertical)

=== "中文"

=== "英文"

    "strikeV (Border Box Strikethrough Vertical)"

### 22.1.2.111 sty (style)

=== "中文"

=== "英文"

    "sty (style)"

### 22.1.2.112 sub (Subscript (Pre-Sub-Superscript))

=== "中文"

=== "英文"

    "sub (Subscript (Pre-Sub-Superscript))"

### 22.1.2.113 subHide (Hide Subscript (n-ary))

=== "中文"

=== "英文"

    "subHide (Hide Subscript (n-ary))"

### 22.1.2.114 sup (Superscript (Superscript object))

=== "中文"

=== "英文"

    "sup (Superscript (Superscript object))"

### 22.1.2.115 supHide (Hide Superscript (n-ary))

=== "中文"

=== "英文"

    "supHide (Hide Superscript (n-ary))"

### 22.1.2.116 t (Text)

=== "中文"

=== "英文"

    "t (Text)"

### 22.1.2.117 transp (Transparent (Phantom))

=== "中文"

=== "英文"

    "transp (Transparent (Phantom))"

### 22.1.2.118 type (Fraction type)

=== "中文"

=== "英文"

    "type (Fraction type)"

### 22.1.2.119 vertJc (Vertical Justification)

=== "中文"

=== "英文"

    "vertJc (Vertical Justification)"

### 22.1.2.120 wrapIndent (Wrap Indent)

=== "中文"

=== "英文"

    "wrapIndent (Wrap Indent)"

### 22.1.2.121 wrapRight (Wrap Right)

=== "中文"

=== "英文"

    "wrapRight (Wrap Right)"

### 22.1.2.122 zeroAsc (Phantom Zero Ascent)

=== "中文"

=== "英文"

    "zeroAsc (Phantom Zero Ascent)"

### 22.1.2.123 zeroDesc (Phantom Zero Descent)

=== "中文"

=== "英文"

    "zeroDesc (Phantom Zero Descent)"

### 22.1.2.124 zeroWid (Phantom Zero Width)

=== "中文"

=== "英文"

    "zeroWid (Phantom Zero Width)"

## 22.1.3 Simple Types

=== "中文"

=== "英文"

    "Simple Types"

### 22.1.3.1 ST_BreakBin (Break Binary Operators)

=== "中文"

=== "英文"

    "ST_BreakBin (Break Binary Operators)"

### 22.1.3.2 ST_BreakBinSub (Break on Binary Subtraction)

=== "中文"

=== "英文"

    "ST_BreakBinSub (Break on Binary Subtraction)"

### 22.1.3.3 ST_Char (Character)

=== "中文"

=== "英文"

    "ST_Char (Character)"

### 22.1.3.4 ST_FType (Fraction Type)

=== "中文"

=== "英文"

    "ST_FType (Fraction Type)"

### 22.1.3.5 ST_Integer2 (Integer value (-2 to 2))

=== "中文"

=== "英文"

    "ST_Integer2 (Integer value (-2 to 2))"

### 22.1.3.6 ST_Integer255 (Integer value (1 to 255))

=== "中文"

=== "英文"

    "ST_Integer255 (Integer value (1 to 255))"

### 22.1.3.7 ST_Jc (Justification)

=== "中文"

=== "英文"

    "ST_Jc (Justification)"

### 22.1.3.8 ST_LimLoc (Limit Location)

=== "中文"

=== "英文"

    "ST_LimLoc (Limit Location)"

### 22.1.3.9 ST_Script (Script)

=== "中文"

=== "英文"

    "ST_Script (Script)"

### 22.1.3.10 ST_Shp (Shape (Delimiters))

=== "中文"

=== "英文"

    "ST_Shp (Shape (Delimiters))"

### 22.1.3.11 ST_SpacingRule (Spacing Rule)

=== "中文"

=== "英文"

    "ST_SpacingRule (Spacing Rule)"

### 22.1.3.12 ST_Style (Style)

=== "中文"

=== "英文"

    "ST_Style (Style)"

### 22.1.3.13 ST_TopBot (Top-Bottom)

=== "中文"

=== "英文"

    "ST_TopBot (Top-Bottom)"

### 22.1.3.14 ST_UnSignedInteger (Unsigned integer.)

=== "中文"

=== "英文"

    "ST_UnSignedInteger (Unsigned integer.)"
