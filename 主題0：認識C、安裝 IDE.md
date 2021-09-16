<!--
---
title: 1101 計算機程式與應用 主題0：認識C、安裝 IDE
---
-->

# 主題0：認識C、安裝 IDE
###### tags: `TA-整理資料`, `ntust-1101`

## What is Programming

### Understanding Programming in layman terms …

>　Programming is a way to “*instruct the computer to perform various tasks*”.

### Instruct the computer

+ 基本上意味著你向電腦提供了一組以電腦可以理解的語言編寫指令。
+ 指令可以是各種類型。
+ 就像我們人類可以理解好幾種語言一樣，電腦也可以理解特定的語法寫出來的指令。
（就是所謂的 **programming language**）

### Perform various tasks

這些任務可以是簡單的任務，也可以是涉及多個指令序列的複雜任務。

---


> A programming language is the set of instructions through which humans interact with computers.
The code is pretty much like writing a paragraph of instruction or creating a to-do list to computers. Unlike us humans, the to-do list and instructions you write for the computer has to be <font color=red>**extremely detailed**</font> and <font color=red>**written in some logic**</font>.


撰寫程式碼就好像是在寫一段指令，或是為電腦列出一個 to-do list。而電腦並不像我們人類一樣，我們為電腦列出的 to-do list 需要非常的詳細，並且要用某種邏輯來撰寫。


## 程式語言的分類

### 機器語言 Machine Language

+ 指硬體內部所使用的語言，也是電腦唯一能直接辨識的語言。
+ 由於電腦是由電子電路所構成，在這個世界裡只懂得兩種訊號：1或0，用來表示開或關。也因此最早的電腦語言就是使用 0 和 1 所寫成的。
+ 完全由這兩個數字使用二進位編碼來表示要執行的命令，這種語言不需要經過任何翻譯，電腦就可以直接執行，這也就代表執行速度快，使用的電腦資源也少；但是要了結由「1」和「0」組合成的機器語言代表的意義，就必須透過查表才能得知，可讀性相當低，於是，組合語言、高階語言就陸陸續續產生了。

### 組合語言  Assembly

+ 最接近機器語言的程式語言。
+ 使用助憶符號（Mnemonics）取代機器語言的指令。例如：以 ADD 代表機器語言的加法動作指令。
+ 相較於機器語言，組合語言更有利於我們撰寫程式，但是電腦無法直接執行組合語言程式，因此執行前必須先翻譯成機器語言，而將組合語言翻譯成機器語言的工具我們稱它為組譯程式（Assembler）。
+ 通常我們會將組合語言和機器語言都歸類在「低階語言」，而所謂低階語言，就是比較能直接對硬體去做輸入或輸出控制的語言。組合語言與機器語言十分相似，撰寫這兩種程式碼之前都必須了解電腦的架構，才能正確使用。


### 高階語言 High-Level Language

+ 為了讓電腦更廣泛地使用，就出現了以人類日常生活中常使用的文字或符號來表達的程式語言，我們稱它為高階語言。其文法接近日常的英文用語，當然也包含一班常用的數學運算符號。
+ 從撰寫者的角度來看，比起低階語言，用高階語言所寫出來的程式較容易被我們所了解，也更容易維護。
+ 從電腦的角度來看，組合語言跟機器的相關性很高，不同的機器必須使用不同的組合語言，而高階語言在不同的機器上差異不大。
+ 但是電腦真正能夠理解的語言還是機器語言，所以高階語言還是必須先透過編譯程式（Compiler）或直譯程式（Interpreter）翻譯成機器語言才能執行。

### 直譯程式 vs. 編譯程式

|          | 直譯程式<br>Interpreted Language | 編譯程式<br>Compiled Language |
| -------- | :------: | :------: |
| 說明 | 需搭配直譯器（Interpreter）<br>每翻譯一行指令後，就立刻交付電腦執行，不須經過編譯。 | 需搭配編譯器（Compiler）<br>將全部的程式翻譯後，先產生目的檔（.obj），再將其他要連結的程式連結以後，才交由電腦執行。 |
| 優點 | 佔用的記憶體較少。<br>修改及除錯容易。 | 執行時不需要重複編譯，所以執行速度及效率較高。 |
| 缺點 | 每次執行前才翻譯，執行速度慢、效率較低。 | 原始程式經過修改就必須重新編譯。<br>較佔用記憶體空間。 |
| 舉例 | BASIC<br>HTML<br>JavaScript<br>Python<br>Ruby 等 | C/C++<br>COBAL<br>PASCAL 等 |

![](https://i.imgur.com/rhfDN0j.png)

## 計算機程式組成與執行概念

### 電腦怎麼來的？ ENIAC

+ 我們認為最早的通用電腦是由美國賓州大學的莫奇來（Mauchly）和他的學生埃克特（Eckert）在 1946年2月14日當天所發表的「ENIAC」（Electronic Numerical Integrator And Computer，電子數值積分計算機）。

![](https://i.imgur.com/Vy5WvYj.png)


+ ENIAC 在進行每一次運算之前，都需要根據運算要求把不同的元件用人工插接線路的方式連接在一起。將輸入輸出裝置設置好後，才進行通電。
+ 因為 ENIAC 沒有儲存程式的功能。最早的計算機器僅內涵固定用途的程式。

### 電腦怎麼來的？ EDVAC

+ EDVAC 全名是 Electronic Discrete Variable Automatic Computer，離散變量自動電子計算機。
+ 建造者跟 ENIAC 一樣皆由莫奇來（Mauchly）和埃克特（Eckert）。
+ EDVAC 可以說是第一台現代意義的通用計算機，採用的是范紐曼架構。

![](https://i.imgur.com/2pLBDXd.png)

### 范紐曼架構 Von Neumann Architecture

**范紐曼架構的設計概念**
![](https://i.imgur.com/cdaJlFK.png)

+ 范紐曼架構一詞出自約翰．范紐曼的論文 First Draft of a Report on the EDVAC, June 30, 1945，其中建立了現代電腦的兩大建構原則：
    1. 大膽捨棄了十進制，改以二進制運算和儲存資料。
    2. 要被執行的程式得先放在記憶體中，等要執行時再去記憶體中抓出來。
+ 而這兩點原則都指向了報告最核心的概念－「儲存程序電腦」（Stored Program Computer）。
+ 1951年，美國軍方根據這份報告並透過范紐曼的協助打造了計算機 EDVAC。

---

+ 講白點，范紐曼架構就是一個打造電腦的數學模型，也是目前唯一被成功實作出來，全世界電腦唯一使用的數學模型。
+ 當然，電腦架構不只范紐曼架構，其他還有比如說：哈佛架構、仿生電腦、量子電腦等等，但基本上都還處於理論階段。
+ 另外補充，儲存程序電腦的概念並不是由范紐曼提出的，而是圖靈（Turing）提出來的圖靈機（Turing Machine）。在這裡推薦一部電影－[模仿遊戲](https://youtu.be/spkUZQt_4pI)（ The Imitation Game ）

---

+ 范紐曼架構使用記憶體來儲存計算機的指令與資料（program），方便 CPU 可以根據中間的結果來修改後續指令。
+ 而在范紐曼式的電腦中，電腦被分成了五大單元缺一不可。
    1. 控制器 Control Unit
    2. 運算器 Arithmetic Logic Unit, ALU
    3. 記憶體 Memory
    4. 輸入設備 Input Device
    5. 輸出設備 Output Device

![](https://i.imgur.com/1MMiXvD.png)

### Why better than ENIAC?

因為我們會先把要執行的程式碼跟資料都儲存於記憶體，所以如果我們想要變更任務，只需要修改程式即可，不需要去更改線路，省去這個步驟的麻煩。

### 指令集架構

+ 任何產品在設計的時候，都要先制定規格、再依據規格設計出相應的產品。
+ 所以，當我們想要設計 CPU 時，要制定的規格就是「指令集架構」（Instruction Set Architecture, ISA）。
+ 指令集架構包含：
    1. 指令集。
    2. 該指令集依附的機器結構敘述（Hardware Information）

---

+ 聽起來有點抽象，但是我們可以用一條簡單的敘述來描述指令集架構跟范紐曼架構的關係：

$$
ISA + Von\text{ }Neuman\text{ }Machine = Basic\text{ }Computer\text{ }Structure
$$


##### 如果對電腦的基底有興趣的話，未來可以去修「計算機程式」這門課 :smiley: 

## 認識 C 語言

### C-Language Introduction

+ C 語言是由美國貝爾實驗室（Bell Laboratory）的 Dennis Ritchie 在 1972 年所開發出來的。
+ 前身是 B 語言（Basic Combined Programming Language - BCPL）。
+ 1978 年，Dennis Ritchie 和 Brain Kernighan 發布了第一版“ The C Programming Language”，俗稱  K&RC。
+ C 語言在各種平台上快速發展，之後出了許多版本，為了統一各版本，1983 年美國國家標準局（ANSI）成立了一個委員會，為 C 語言提供了一套標準，我們把這一套標準 C 稱為“ANSI standard”或“ANSI C”。而這套 ANSI C 也在 1989 年通過審查。於 1999 年進行了修訂。

### Features of C-Language

+ 可靠性 Reliability
+ 可攜性 Portability
+ 靈活性 Flexibility
+ 互動性 Interactivity
+ 模組化 Modularity
+ 效率和有效性 Efficiency and Effectiveness

### Uses of C-Language

> C 語言常用於開發作業系統（如：Windows、UNIX 和 Linux）

* 數據庫系統 Database systems
* Graphics packages
* 文字處理器 Word processors
* 試算表 Spreadsheets
* 作業系統開發 Operating system development
* 編譯程式與組譯程式 Compilers and Assemblers
* 網路驅動 Network drivers
* 直譯器 Interpreters

### C 程式的開發環境

> C 程式在執行前會經過六個階段

1. 編輯：使用者可利用編輯器撰寫或修改 C 程式碼（source code）。
1. 前置處理：前置處理器（preprocessor）會在開始編譯前自動執行，依據程式碼中 # 所標示的指示，進行代換或插入等動作。例如：`#include <studio.h>` 告訴編譯器在為編譯程式之前，先將程式庫中的標頭黨 `stdio.h` 插入該位置。
1. 編譯：編譯器（compiler）將程式碼編譯為目的碼（object code）。
1. 連結：連結器（linker）將一個或多個目的檔（.obj）與靜態程式庫檔（.lib）連結，產生可執行檔（.exe）。
1. 載入：載入器（loader）將可執行檔（.exe）載入記憶體，並與動態程式庫檔（.dll）連結。動態程式庫可減少執行檔所佔的硬碟和記憶體空間。
1. 執行：最後，電腦在 CPU 的控制下，開始執行所載入的程式。

![](https://i.imgur.com/6YfJWhU.png)





















