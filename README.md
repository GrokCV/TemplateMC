# Overleaf PPT 模板使用指南

## 文件结构

本模板包含以下两个主要文件：

1. **`MCPPT.tex`**
   
   - 主文件，包含 PPT 的整体结构和内容。
   - 包括封面页、目录页、内容页、问答页和结束页。
2. **`configs.tex`**
   
   - 配置文件，定义了模板的颜色、字体、主题、页眉页脚样式等。
   - 包含颜色定义、导航栏设置、列表样式、表格样式等。

所有文件均位于同一目录下，无需额外的文件夹结构。

---

## 配置文件内容

### 1. **颜色定义**

# 颜色定义

在 `configs.tex` 中定义的颜色供模板使用，下面的颜色表以直观的色块展示各颜色及其 RGB 值，整体风格简洁大气，适合于技术文档和论文模板。

| **颜色名称**   | **色块展示**                                                                                                                                              | **RGB 值**         | **说明**         |
| -------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------ | ---------------- |
| **lightblue**  |                                        | (46, 117, 182)     | **浅蓝色（主题色）**  |
| **midblue**    |                                          | (0, 82, 155)       | **中蓝色（主题色）**  |
| **darkblue**   |                                          | (0, 53, 107)       | **深蓝色（主题色）**  |
| **myblue**     |                                          | (41, 128, 185)     | 深蓝             |
| **myred**      |                                          | (192, 57, 43)      | 酒红             |
| **mygreen**    |                                          | (39, 174, 96)      | 祖母绿           |
| **mypurple**   |                                          | (155, 89, 182)     | 浅紫             |
| **myorange**   |                                          | (211, 84, 0)       | 橙色             |
| **myitem**     |                                          | (0, 0, 0)          | 黑色             |
| **borderblue** |                                          | (0, 50, 100)       | 边框蓝色         |

---

### 2. **字体设置**

模板使用了以下字体：

- **英文字体**：`Liberation Sans` 和 `Liberation Mono`
- **中文字体**：`Noto Sans CJK SC`
- **数学字体**：`TeX Gyre Termes Math`

### 3. **页眉页脚设置**

- **页眉**：显示当前页面的标题（`frametitle`），顶部有一条蓝色分隔线。
- **页脚**：分为三部分：
  - 左侧：作者信息和链接
  - 中间：项目名称
  - 右侧：当前页码

### 4. **列表样式**

- **无序列表**：默认使用圆形图标，大小可切换（大圆圈或小圆圈）。
- **有序列表**：数字编号，颜色为深蓝色。

### 5. **表格样式**

提供了三种表格样式：

- **普通表格**：`PlainTable`
- **三线表**：`ThreeLineTable`
- **交替颜色表格**：`AltColorTable`

### 6. **公式背景**

提供了一个公式背景框命令 `BehindEqBox`，可以自定义背景颜色、边框样式和间距。

---

## 主文件结构

### 1. **封面页**

```latex
\newcommand{\mytitle}{The title of the presentation is here}
\newcommand{\myauthor}{Your Name}
\newcommand{\myinstitute}{Nankai University}

\begin{frame}
  \begin{tikzpicture}[remember picture, overlay]
    % 蓝色标题栏背景
    \node[fill=midblue, minimum width=1.0\paperwidth, minimum height=0.5\paperheight, anchor=north] at (current page.north) {};
    
    % 标题
    \node[text=white, font=\fontsize{32}{36}\selectfont\bfseries, text width=0.9\paperwidth, align=center] at ([yshift=-0.265\paperheight]current page.north) {\mytitle};
    
    % 作者信息
    \node[text=black, font=\Large] at ([yshift=-1.5cm]current page.center) {\myauthor};
    
    % 机构信息
    \node[text=black, font=\Large] at ([yshift=-2.5cm]current page.center) {\myinstitute};
  \end{tikzpicture}
\end{frame}
```

### 2. **目录页**

```latex
\begin{frame}{Contents}
  \vspace{1em}
  \begin{enumerate}
    \item Introduction
    \item Methodology
    \item Experimental Results
    \item Conclusion
  \end{enumerate}
\end{frame}
```

### 3. **内容页**

```latex
\section{Richer convolutional feature}
\begin{frame}{Richer convolutional feature}
  \begin{itemize}
    \item APP: Classification (Res2Net-v1b)
      \begin{itemize}
        \item Results on mmdetection
      \end{itemize}
  \end{itemize}
  \vspace{0.5em}
  \centering
  \ThreeLineTable{%
    \begin{tabular}{lcccc}
      \toprule
      \textbf{Backbone}      & \textbf{Params} & \textbf{GFLOPs} & \textbf{Top-1 err.} & \textbf{Top-5 err.} \\
      \midrule
      ResNet-101           & 44.6 M  & 7.8  & 22.63 & 6.44 \\
      ResNeXt-101-64x4d    & 83.5 M  & 15.5 & 20.40 & --   \\
      HRNetV2p-W48         & 77.5 M  & 16.1 & 20.70 & 5.50 \\
      Res2Net-v1b-50       & 25.23 M & 4.5  & 19.73 & 4.96 \\
      Res2Net-v1b-101      & 45.2 M  & 8.3  & 18.77 & 4.64 \\
      \bottomrule
    \end{tabular}
  }
\end{frame}
```

### 4. **问答页**

```latex
\begin{frame}{Questions and Answers}
  \centering
  \vspace{0.8cm}
  {\Huge \bfseries Q\&A}
\end{frame}
```

### 5. **结束页**

```latex
\begin{frame}[plain]
  \begin{tikzpicture}[remember picture,overlay]
    \node[fill=midblue, opacity=1, minimum width=\paperwidth, minimum height=\paperheight] at (current page.center) {};
    \node[font=\fontsize{40}{70}\selectfont\bfseries, text=white] at (current page.center) {THANKS};
  \end{tikzpicture}
\end{frame}
```

---

## 如何使用本模板

### 1. **编译方式**

- 使用 `XeLaTeX` 编译（模板已指定编译器）。
- 在 Overleaf 中默认会自动选择正确的编译器。

### 2. **修改内容**

#### 封面页

- 修改标题：编辑 `\mytitle` 的内容。
- 修改作者：编辑 `\myauthor` 的内容。
- 修改机构：编辑 `\myinstitute` 的内容。

#### 目录页

- 修改目录项：在 `enumerate` 环境中添加或删除 `\item`。

#### 内容页

- 添加新页面：复制 `frame` 环境并修改内容。
- 修改表格：使用 `\ThreeLineTable` 或其他表格样式。

#### 问答页和结束页

- 问答页：直接显示 "Q&A"。
- 结束页：显示 "THANKS"，背景为深蓝色。

### 3. **修改页眉和页脚**

#### 页眉

- 修改页眉显示：在 `configs.tex` 中找到以下代码：
  
  ```latex
  \setbeamertemplate{headline}{%
    \ifnum\value{framenumber}>1
      \begin{tikzpicture}[remember picture,overlay]
        \node[anchor=west, font=\normalsize, text=black, xshift=0.2cm, yshift=-0.35cm]
              at (current page.north west){\insertframetitle};
        \draw[line width=1pt, color=midblue]
              ([yshift=-0.7cm]current page.north west) -- ([yshift=-0.7cm]current page.north east);
      \end{tikzpicture}
    \fi
  }
  ```
  
  - 修改 `frametitle` 的字体颜色：将 `text=black` 改为其他颜色。
  - 修改分隔线颜色：将 `color=midblue` 改为其他颜色。

#### 页脚

- 修改页脚显示：在 `configs.tex` 中找到以下代码：
  
  ```latex
  \setbeamertemplate{footline}{%
    \begin{tikzpicture}[remember picture,overlay]
      \node[fill=lightblue, minimum width=0.3\paperwidth, minimum height=0.4cm, anchor=south west]
           at (current page.south west) (leftblock) {};
      \node[fill=midblue, minimum width=0.6\paperwidth, minimum height=0.4cm, anchor=south west]
           at ([xshift=0.3\paperwidth]current page.south west) (midblock) {};
      \node[fill=darkblue, minimum width=0.1\paperwidth, minimum height=0.4cm, anchor=south west]
           at ([xshift=0.9\paperwidth]current page.south west) (rightblock) {};
      \node[anchor=center, font=\tiny, text=white] at (leftblock.center) {程明明, http://mmcheng.net};
      \node[anchor=center, font=\tiny, text=white] at (midblock.center) {大规模图像的多粒度目标检测};
      \node[anchor=center, font=\tiny, text=white] at (rightblock.center) {\insertframenumber};
    \end{tikzpicture}
  }
  ```
  
  - 修改左侧内容：编辑 `leftblock` 中的文本。
  - 修改中间内容：编辑 `midblock` 中的文本。
  - 修改右侧内容：编辑 `rightblock` 中的文本。

### 4. **字体色块**

使用 `BehindEqBox` 命令插入公式：

```latex
\BehindEqBox{ $ E = mc^2 $ }
```

- 修改背景颜色：在命令中添加颜色参数，例如 `\BehindEqBox[myred]{ ... }`。
- 修改边框样式：在命令中添加边框参数，例如 `\BehindEqBox[myred]{ ... }{8mm}{10pt}{dashed}`。

### 5. **插入图片**

使用 `includegraphics` 插入图片：

```latex
\includegraphics[width=0.68\textwidth]{demo.jpg}
```

- 修改图片路径：将 `demo.jpg` 替换为实际图片的路径。
- 修改图片大小：调整 `width` 参数。

---

## 总结

本模板提供了一个美观且功能丰富的 PPT 框架，适合学术报告或项目展示。通过修改 `configs.tex` 和 `0MCPPT.tex` 中的内容，您可以轻松定制模板的样式和内容。希望本 README 能帮助您快速上手！
