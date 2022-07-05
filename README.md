# 小論文模板 README
## 前言
### 動機

> 此模板為 [中學生網站](https://www.shs.edu.tw/) 小論文寫作使用  
> 
> 本人算是 $\LaTeX$ 的初學者，如果覺得程式碼有什麼地方可以改進的都歡迎來信：[houjunqimail@gmail.com](mailto:houjunqimail@gmail.com)

先前使用 Word 與同學編排小論文時常遇到一些排板上的問題，其中最常出現的就是階層式標題。每次試每次靈。  
在嘗試了許久後終於弄出想要的排板，卻在請人檢查格式的時候發現原來我們根本寫的就是舊版格式，幾乎全部都要重改…

後來在 Youtube 上面看到 [Papaya 的教學影片](https://www.youtube.com/watch?v=mQamBS6uTOc)得知還有 $\LaTeX$ 這種神奇的排版工具，一方面是出於練習語法，另一方面是出於自己有做小論文的需求，就乾脆刻了一個。

### 特色

- 我設計好的自定義命令，比內建的命令簡短
- 將板型、縮排等固定的格式都先設定完
- 參考文獻已依（書籍/報紙/網路資料等）製作成自定義命令，只需複製後填入對應資料即會生成正確格式。
- 在 Overleaf 上面可以多人共同編輯，且因為是編輯文字檔，不怕多人衝突後格式跑掉

> 建議使用方法：雖然本模板已盡量使大部分的原始碼簡短，但為了避免沒接觸過的人一下子看太多感到噁心，需要使用到某樣功能的時候可以再回來翻找這份文件喔！（不要強求自己直接背下來）

## 開始使用

## 語法

- `\clearpage`：強制換頁
- `\textbf{文字內容}`：粗體
- `\textit{文字內容}`：斜體

### 標題

依規定，小論文的架構分六項：

1. 前言
2. 文獻探討
3. 研究方法
4. 研究分析與結果
5. 研究結果與討論
6. 參考文獻及論文格式

且每一層標題中又要再分層次。

本模板支援四層，語法如下

| 層次                    | 指令              |
|-------------------------|-------------------|
| 壹、貳、參…             | `\h{標題內容}`    |
| 一、二、三…             | `\hh{標題內容}`   |
| （一）、（二）、（三）… | `\hhh{標題內容}`  |
| 1、2、3…                | `\hhhh{標題內容}` |

> 在標題的語法中你只需要輸入標題本身的內容即可，前方編號的部分 $\LaTeX$ 會自動處理好。

來看看使用的例子：

```LaTeX
\h{前言}
    \hh{研究動機}
        \hhh{三級標題測試}
            \hhhh{四級標題測試}
    \hh{研究目的}
\h{文獻探討}
```

輸出結果：

---

<img src="https://i.imgur.com/R0SDCLE.png" width=40%/>

---

### 內文（文字）

既然標題有層次式之分，內文的部分自然也會有縮排的需求。

| 層次   | 指令                                |
|--------|-------------------------------------|
| 最外層 | 不需特別指令，直接輸入內文          |
| 縮一層 | `\hhtext{內文的部分}`  |
| 縮二層 | `\hhhtext {內文的部分}` |
| 縮三層 | `\hhhh{標題內容}`                   |

在 $\LaTeX$ 中，任何超過一格的空白都會被忽略掉，請看範例：

```LaTeX
\h{前言}
	\hh{研究動機}
        \hhtext
        {
            在 \LaTeX 中，任何超過一格的空白都會被忽略掉，在輸入的時候也要注意，段落與段落之間需要多留一行空行。
            像這樣就沒有被分段，會接在剛剛的文字後面。
            
            這樣就分段了。
        }
```

---

<img src="https://i.imgur.com/G69AtrV.png" width=100%/>

---

從上圖你也可以看到：中文開頭空兩格的部分模板會自動處理。你只需要直接輸入內容即可。

### 內文（圖片）

要在文件中置入圖片，首先需要將圖片上傳到 Overleaf 的資料夾：

<img src="https://i.imgur.com/77jECx6.png" width=50%/>

將圖片上傳到 Overleaf 上面之後，使用下列的語法來使用。

> 圖片的語法比較冗長，建議用複製的過去改！

#### 單張圖片

```LaTeX
\begin{figure}[H] %H代表強制圖片放在原始碼對應的相關位置，htbp代表由 LaTeX 彈性調整
\captionsetup{format=hang}
\centering %圖片置中
\vspace{0pt}
\begin{minipage}[t]{1\textwidth}
\centering %圖片在 minipage 置中
\caption{在這裡輸入你的圖說}
\includegraphics[width=0.8\textwidth]{test1.jpg}\\[0.5cm]
%這裡可以調整相對於 minipage 圖片的比例

資料來源：
\label{fig.1}
\end{minipage}
\end{figure}
```

- 在第八行的 `\includegraphics[]{}` 中可以設定圖片的大小及設定要使用哪張圖片。（要注意圖片檔名副檔名要和上傳到 Overleaf 上面的一致）
- 第十一行的 `資料來源：` 後方要輸入圖/表的來源，本模板也有設計相關的指令。小論文規定在圖表下方需註記上資料來源，相關使用方法請參閱後文。

> 事實上，調整圖片大小在這裡有兩種方式，第一種是調整第五行  
> eg.`minipage{0.5\textwidth}`  
> eg.`minipage{2cm}`  
> 第二種是修改檔在 minipage 中的大小，在第八行  
> eg.`\includegraphics[width=5cm]{test1.jpg}\\[0.5cm]`  
> eg.`\includegraphics[width=0.8\textwidth]{test1.jpg}\\[0.5cm]`  
> 差別主要在修改 minipage 的大小的話，圖說及資料來源也會跟著擠到中央。而反之則不。

#### 多張圖片

##### 兩張圖片
```LaTeX
\begin{figure}[H] %H代表強制圖片放在原始碼對應的相關位置，htbp代表由 LaTeX 彈性調整
    \captionsetup{format=hang}
    \centering %整組合併的圖片置中
    \vspace{0pt}
    \begin{minipage}[t]{0.45\textwidth} %可調整子圖區域大小，但所有 minipage 總合不能超過 1
        \centering %在圖片的 minipage 內置中
        \caption{第一張圖的圖說}
        \includegraphics[width=0.8\textwidth]{test1.jpg}\\[0.5cm]
        %圖片相對於 minipage 要多寬
        資料來源：
        \label{fig.2}
    \end{minipage}
    \begin{minipage}[t]{0.45\textwidth}
        \centering
        \caption{第二張圖的圖說}
        \includegraphics[width=0.8\textwidth]{test2.png}
        \label{fig.3}
    \end{minipage}
\end{figure}   
```

##### 三張圖片

```LaTeX
\begin{figure}[H] %H代表強制圖片放在原始碼對應的相關位置，htbp代表由 LaTeX 彈性調整
    \captionsetup{format=hang}
    \centering %整組合併的圖片置中
    \vspace{0pt}
    \begin{minipage}[t]{0.3\textwidth} %可調整子圖區域大小，但所有 minipage 總合不能超過 1
        \centering %在圖片的小區域內置中
        \caption{第一張圖的圖說}
        \includegraphics[width=0.8\textwidth]{test1.jpg}\\[0.5cm]
        %圖片相對於 minipage 要多寬
        資料來源：
        \label{fig.4}
    \end{minipage}
    \begin{minipage}[t]{0.3\textwidth}
        \centering
        \caption{第二張圖的圖說}
        \includegraphics[width=0.8\textwidth]{test2.png}
        \label{fig.5}
    \end{minipage}
    \begin{minipage}[t]{0.3\textwidth}
        \centering
        \caption{第三張圖的圖說}
        \includegraphics[width=0.8\textwidth]{test3.png}
        \label{fig.6}
    \end{minipage}
\end{figure}              
```

##### 四張圖片

```LaTeX
\begin{figure}[H] %H代表強制圖片放在原始碼對應的相關位置，htbp代表由 LaTeX 彈性調整
\captionsetup{format=hang}
\centering %整組合併的圖片置中
\vspace{0pt}
\begin{minipage}[t]{0.23\textwidth} %可調整子圖區域大小，但所有 minipage 總合不能超過 1
    \centering %在圖片的小區域內置中
    \caption{第一張圖的圖說}
    \includegraphics[width=0.8\textwidth]{test1.jpg}\\[0.5cm]
    %圖片相對於 minipage 要多寬
    資料來源：
    \label{fig.4}
\end{minipage}
\begin{minipage}[t]{0.23\textwidth}
    \centering
    \caption{第二張圖的圖說}
    \includegraphics[width=0.8\textwidth]{test2.png}
    \label{fig.5}
\end{minipage}
\begin{minipage}[t]{0.23\textwidth}
    \centering
    \caption{第三張圖的圖說}
    \includegraphics[width=0.8\textwidth]{test3.png}
    \label{fig.6}
\end{minipage}
\begin{minipage}[t]{0.23\textwidth}
    \centering
    \caption{第四張圖的圖說}
    \includegraphics[width=0.8\textwidth]{test4.jpg}
    \label{fig.7}
\end{minipage}    
\end{figure}   
```

#### 在文字中引用圖片

有時候我們會出現這種需求：

---

<img src="https://i.imgur.com/TkoY5qL.png" width=50%/>

---

`圖 1` 的那個編號，當然可以手動輸入，但也可以考慮使用 $\LaTeX$ 好用的引用功能。

在圖片的程式碼中，你可以看到每張圖都有以下的部分：

```LaTeX
\label{fig.x} %把 x 換成一個好記的數字或簡稱
```

在這邊設定好以後，若要在文中引用：

```LaTeX
現在開始測試圖片，請見圖 \ref{fig.x}。
```

就可以達成剛剛的效果嘍！

### 英文引號

LaTeX 中的引號使用上比較奇怪，如果使用一般的引號輸出後只會剩下「右引號」。（中文則沒這個問題）  
- 左引號的部分要用鍵盤上的 `` ` `` 取代，右引號保持不變
- 雙引號的規則與單引號相似，同一個符號敲兩下即可（注意！不是直接輸入 `"`）

| 符號                | 指令    |
|---------------------|---------|
| `'`（英文左引號）   | `` ` `` |
| `'`（英文右引號）   | `'`     |
| `"`（英文左雙引號） | ` `` `  |
| `"`（英文右雙引號） | `''`    |

### 特殊符號

由於在 $\LaTeX$ 中有些符號有其獨特的功能，所以若要在檔案中像在 Word 中打字一般顯示出這些符號，需要使用以下的替代方法。  
格式：`\符號內容` 後續的內容與符號的指令間通常要空一格空白。

> 若是不常接觸程式的，建議需要使用到某個符號的時候再回來翻部分。

| 符號 | 指令   | 範例                                                             |
|------|--------|------------------------------------------------------------------|
| `~`  | `\~{}` | `天氣好熱啊\~{}` = `天氣好熱啊~`                                 |
| `'`  | `\apo` | `Let\apo s go!` = `Let's go!`                                    |
| `#`  | `\#`   | `Hashtag: \# My name` = `Hashtag: #Myname`                       |
| `$`  | `$`    | `This template is cost 0\$ !` = `This template is cost 0$!`      |
| `%`  | `%`    | `This template is 100\% free!` = `This template is 100% free!`   |
| `&`  | `\&`   | `You \& I` = `You & I`                                           |
| `{`  | `\{`   | `a pair of \{ curly brackets\}.` = `a pair of {curly brackets}.` |
| `}`  | `\}`   | 同上                                                             |
| `_`  | `\_{}` |                                                                  |
| `^`  | `\^{}` |

> `\apo` 為本模板自定的語法，非內建的。

如果你已經開始試著使用 $\LaTeX$，你應該會發現幾乎每一行指令都是由反斜線（`\`）開始的，那想必這個符號也沒辦法直接打出來

- `\` 需要用 `\textbackslash` 打出來  
    eg.  
    `這種符號\textbackslash 通常用於程式碼，我一時也沒想到什麼句子。`  
    = `這種符號\通常用於程式碼，我一時也沒想到什麼句子。`

### 方程式

這部分沒什麼特別修改，有興趣可上網查詢 $\LaTeX$ 寫方程式的語法。這裡簡單說一下怎麼告訴 $\LaTeX$ 你準備要開始寫公式。

#### 行內

用兩個半形美元符號將公式框起來  
eg. `$\frac{1}{10}$` = $\frac{1}{10}$

#### 整個區塊

```LaTeX
$$
\fraction{1}{10}
$$
```

行內跟區塊的比較：

---

<img src="https://i.imgur.com/TZEngVz.png"/>

---

### 參考文獻

若為圖表下方的資料來源，參考上文中圖表範例裡的使用方法。  
若為參考文獻請直接寫在本模板 Overleaf 裡的檔案 `ref.tex` 中。

#### 語法表
> 網址部分依小論文規定可放短網址

詳細請參考 Overleaf 模板中 `copy[ref].tex` 檔案中，各種文獻有用註解的方式作分別。使用時取需要的複製去修改即可。

#### 作者名字怎麼填？

在參考文獻的指令中幾乎都需要填寫作者資料，中英在表示上有所不同，請務必填寫正確。

##### 中文文獻

`姓名`

- 作者一位：`王小明`
- 作者二位：`王小明、陳小華`
- 作者三位以上：`王小明等`

> 若為編輯或翻譯的著作：`王小明（譯）`

##### 英文文獻

`last name, F.M`

> 注意結尾的標點符號要省略  
> 例如：不要寫成 `last name, F.M.`

其中：  
- F：First name 的開頭大寫字母  
- M：Middle name 的開頭大寫字母  

假設作者姓名：  
- A 作者：
    - last name（姓）：Porter
    - first name（名）：Ram
    - middle name（中間名）：Prasad
- B 作者：
    - last name（姓）：Srivastava
    - first name（名）：Alan
    - middle name（中間名）：James

則：  
- 作者僅一位 A：
    - `Porter, R.P`  
- 作者為 A 和 B：
    - `Porter, R.P.,& Srivastava, A.J`
- 作者有三人或以上：
    - `Porter, R.P et al`

> 若為編輯的著作：
> `Porter, R.P. (Ed.)`
> 若為編輯的著作（兩人或兩人以上）：
> `Porter, R.P.,& Srivastava, A.J. (Eds.)`

## Reference

- [全國高級中等學校小論文寫作比賽格式說明暨評審要點](https://www.shs.edu.tw/doc_download/%e5%85%a8%e5%9c%8b%e9%ab%98%e7%b4%9a%e4%b8%ad%e7%ad%89%e5%ad%b8%e6%a0%a1%e5%b0%8f%e8%ab%96%e6%96%87%e5%af%ab%e4%bd%9c%e6%af%94%e8%b3%bd%e6%a0%bc%e5%bc%8f%e8%aa%aa%e6%98%8e%e6%9a%a8%e8%a9%95%e5%af%a9%e8%a6%81%e9%bb%9e_110.pdf)
