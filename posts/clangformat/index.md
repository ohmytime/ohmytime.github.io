# Clangformat


Windows下基于VSC，设置Clangforat  
[Windows下安装Clang format](https://blog.csdn.net/wanlong1215/article/details/109509053)  
&lt;!--more--&gt;

#### 1. .vscode

.vscode 里面加入：
```bash 
&#34;C_Cpp.formatting&#34;: &#34;clangFormat&#34;,
&#34;editor.formatOnSave&#34;: true,
```

#### 2. .cpp properties.json
```bash

{
	&#34;configurations&#34;: [
		{
			&#34;name&#34;: &#34;CMake&#34;,
			&#34;compileCommands&#34;: &#34;${workspaceFolder}/build/compile_commands.json&#34;,
			&#34;configurationProvider&#34;: &#34;ms-vscode.cmake-tools&#34;,
			&#34;defines&#34;: [
				&#34;HAS_TOUCHPAD&#34;,
				&#34;TOUCHPAD_GT911&#34;,
				&#34;LCD_RA8875&#34;,
				&#34;FRONTPANEL_BIG_V1&#34;
			]
		}
	],
	&#34;version&#34;: 4
}

```

#### 3. .clang-format

```c
---
Language:        Cpp
# BasedOnStyle:  LLVM
AccessModifierOffset: -2
AlignAfterOpenBracket: Align
AlignArrayOfStructures: None
AlignConsecutiveMacros: None
AlignConsecutiveAssignments: None
AlignConsecutiveBitFields: None
AlignConsecutiveDeclarations: None
AlignEscapedNewlines: Left
AlignOperands:   Align
AlignTrailingComments: true
AllowAllArgumentsOnNextLine: true
AllowAllParametersOfDeclarationOnNextLine: true
AllowShortEnumsOnASingleLine: true
AllowShortBlocksOnASingleLine: Never
AllowShortCaseLabelsOnASingleLine: false
AllowShortFunctionsOnASingleLine: All
AllowShortLambdasOnASingleLine: All
AllowShortIfStatementsOnASingleLine: Never
AllowShortLoopsOnASingleLine: false
AlwaysBreakAfterDefinitionReturnType: None
AlwaysBreakAfterReturnType: None
AlwaysBreakBeforeMultilineStrings: false
AlwaysBreakTemplateDeclarations: MultiLine
AttributeMacros:
  - __capability
BinPackArguments: true
BinPackParameters: true
BraceWrapping:
  AfterCaseLabel:  true
  AfterClass:      false
  AfterControlStatement: Never
  AfterEnum:       false
  AfterFunction:   true
  AfterNamespace:  false
  AfterObjCDeclaration: false
  AfterStruct:     true
  AfterUnion:      true
  AfterExternBlock: false
  BeforeCatch:     true
  BeforeElse:      false
  BeforeLambdaBody: false
  BeforeWhile:     false
  IndentBraces:    false
  SplitEmptyFunction: true
  SplitEmptyRecord: true
  SplitEmptyNamespace: true
BreakBeforeBinaryOperators: None
BreakBeforeConceptDeclarations: true
BreakBeforeBraces: Attach
BreakBeforeInheritanceComma: false
BreakInheritanceList: BeforeColon
BreakBeforeTernaryOperators: true
BreakConstructorInitializersBeforeComma: false
BreakConstructorInitializers: BeforeColon
BreakAfterJavaFieldAnnotations: false
BreakStringLiterals: true
ColumnLimit:     190
CommentPragmas:  &#39;^ IWYU pragma:&#39;
QualifierAlignment: Leave
CompactNamespaces: false
ConstructorInitializerIndentWidth: 4
ContinuationIndentWidth: 4
Cpp11BracedListStyle: true
DeriveLineEnding: true
DerivePointerAlignment: false
DisableFormat:   false
EmptyLineAfterAccessModifier: Never
EmptyLineBeforeAccessModifier: LogicalBlock
ExperimentalAutoDetectBinPacking: false
PackConstructorInitializers: BinPack
BasedOnStyle:    &#39;&#39;
ConstructorInitializerAllOnOneLineOrOnePerLine: false
AllowAllConstructorInitializersOnNextLine: true
FixNamespaceComments: true
ForEachMacros:
  - foreach
  - Q_FOREACH
  - BOOST_FOREACH
IfMacros:
  - KJ_IF_MAYBE
IncludeBlocks:   Preserve
IncludeCategories:
  - Regex:           &#39;^&#34;(llvm|llvm-c|clang|clang-c)/&#39;
    Priority:        2
    SortPriority:    0
    CaseSensitive:   false
  - Regex:           &#39;^(&lt;|&#34;(gtest|gmock|isl|json)/)&#39;
    Priority:        3
    SortPriority:    0
    CaseSensitive:   false
  - Regex:           &#39;.*&#39;
    Priority:        1
    SortPriority:    0
    CaseSensitive:   false
IncludeIsMainRegex: &#39;(Test)?$&#39;
IncludeIsMainSourceRegex: &#39;&#39;
IndentAccessModifiers: false
IndentCaseLabels: false
IndentCaseBlocks: false
IndentGotoLabels: true
IndentPPDirectives: None
IndentExternBlock: AfterExternBlock
IndentRequires:  false
IndentWidth:     2
IndentWrappedFunctionNames: false
InsertTrailingCommas: None
InsertBraces: true
JavaScriptQuotes: Leave
JavaScriptWrapImports: true
KeepEmptyLinesAtTheStartOfBlocks: true
LambdaBodyIndentation: Signature
MacroBlockBegin: &#39;&#39;
MacroBlockEnd:   &#39;&#39;
MaxEmptyLinesToKeep: 1
NamespaceIndentation: None
ObjCBinPackProtocolList: Auto
ObjCBlockIndentWidth: 2
ObjCBreakBeforeNestedBlockParam: true
ObjCSpaceAfterProperty: false
ObjCSpaceBeforeProtocolList: true
PenaltyBreakAssignment: 2
PenaltyBreakBeforeFirstCallParameter: 19
PenaltyBreakComment: 300
PenaltyBreakFirstLessLess: 120
PenaltyBreakOpenParenthesis: 0
PenaltyBreakString: 1000
PenaltyBreakTemplateDeclaration: 10
PenaltyExcessCharacter: 1000000
PenaltyReturnTypeOnItsOwnLine: 60
PenaltyIndentedWhitespace: 0
PointerAlignment: Right
PPIndentWidth:   -1
ReferenceAlignment: Pointer
ReflowComments:  true
RemoveBracesLLVM: false
SeparateDefinitionBlocks: Leave
ShortNamespaceLines: 1
SortIncludes:    CaseSensitive
SortJavaStaticImport: Before
SortUsingDeclarations: true
SpaceAfterCStyleCast: false
SpaceAfterLogicalNot: false
SpaceAfterTemplateKeyword: true
SpaceBeforeAssignmentOperators: true
SpaceBeforeCaseColon: false
SpaceBeforeCpp11BracedList: false
SpaceBeforeCtorInitializerColon: true
SpaceBeforeInheritanceColon: true
SpaceBeforeParens: ControlStatements
SpaceBeforeParensOptions:
  AfterControlStatements: true
  AfterForeachMacros: true
  AfterFunctionDefinitionName: false
  AfterFunctionDeclarationName: false
  AfterIfMacros:   true
  AfterOverloadedOperator: false
  BeforeNonEmptyParentheses: false
SpaceAroundPointerQualifiers: Default
SpaceBeforeRangeBasedForLoopColon: true
SpaceInEmptyBlock: false
SpaceInEmptyParentheses: false
SpacesBeforeTrailingComments: 1
SpacesInAngles:  Never
SpacesInConditionalStatement: false
SpacesInContainerLiterals: true
SpacesInCStyleCastParentheses: false
SpacesInLineCommentPrefix:
  Minimum:         1
  Maximum:         -1
SpacesInParentheses: false
SpacesInSquareBrackets: false
SpaceBeforesSquareBrackets: false
BitFieldColonSpacing: Both
Standard:        Latest
StatementAttributeLikeMacros:
  - Q_EMIT
StatementMacros:
  - Q_UNUSED
  - QT_REQUIRE_VERSION
TabWidth:        2
UseCRLF:         false
UseTab:          ForIndentation
WhitespaceSensitiveMacros:
  - STRINGIZE
  - PP_STRINGIZE
  - BOOST_PP_STRINGIZE
  - NS_SWIFT_NAME
  - CF_SWIFT_NAME
...


```

#### 4. bat文件

```bash
c:\Keil_v5\ARM\ARMCLANG\bin\clang-format.exe --style=file:.clang-format -i Src/*
c:\Keil_v5\ARM\ARMCLANG\bin\clang-format.exe --style=file:.clang-format -i Src/BiquadDesigner/*
c:\Keil_v5\ARM\ARMCLANG\bin\clang-format.exe --style=file:.clang-format -i Src/FT8/*
c:\Keil_v5\ARM\ARMCLANG\bin\clang-format.exe --style=file:.clang-format -i Src/JPEG/*
c:\Keil_v5\ARM\ARMCLANG\bin\clang-format.exe --style=file:.clang-format -i Src/USBDevice/*
c:\Keil_v5\ARM\ARMCLANG\bin\clang-format.exe --style=file:.clang-format -i WOLF/Inc/* WOLF/Src/*
c:\Keil_v5\ARM\ARMCLANG\bin\clang-format.exe --style=file:.clang-format -i WOLF-2/Inc/* WOLF-2/Src/*
c:\Keil_v5\ARM\ARMCLANG\bin\clang-format.exe --style=file:.clang-format -i WOLF-Lite/Core/Inc/* WOLF-Lite/Core/Src/*
c:\Keil_v5\ARM\ARMCLANG\bin\clang-format.exe --style=file:.clang-format -i WOLF-Lite_V2-Mini/Inc/* WOLF-Lite_V2-Mini/Src/*
c:\Keil_v5\ARM\ARMCLANG\bin\clang-format.exe --style=file:.clang-format -i WOLF-Mini/Inc/* WOLF-Mini/Src/*
c:\Keil_v5\ARM\ARMCLANG\bin\clang-format.exe --style=file:.clang-format -i WOLF-X1/Inc/* WOLF-X1/Src/*


```

---

> 作者: [ohmytime](ohmytime.github.io)  
> URL: https://ohmytime.github.io/posts/clangformat/  

