# apply系列家族應用情境

apply家族主要功能是將所設定的函數應用到指定物件的每一個欄或列，基本使用格式如下: `apply(x,MARGIN,FUN,...)`

-   x: 可以是矩陣(Matrix)、陣列(Array)、數據框(data.frame)

-   MARGIN:1代表每一列,2代表每一欄

-   FUN: 預計使用的函數

-   . . . : FUN函數所需的額外參數，例如na.rm=TRUE





## apply用法

1.apply函數，輸入Matrix資料結構，輸出numeric向量

```{r echo=T, eval=FALSE}
  # 輸入Matrix資料結構，輸出numeric向量
  DT <- matrix(c(8, 9, 6, 5, 7, 2, 10, 6, 8), ncol=3)
  colnames(DT) <- c("獅子","斑馬","熊貓")
  rownames(DT) <- c("Day 1", "Day 2", "Day 3")
  print(DT)
  Vec <-  apply(DT, 2, max)
  class(Vec)
```

apply函數輸出如下

```{r echo=FALSE, eval=TRUE}
  # 輸入Matrix資料結構，輸出numeric向量
  DT <- matrix(c(8, 9, 6, 5, 7, 2, 10, 6, 8), ncol=3)
  colnames(DT) <- c("獅子","斑馬","熊貓")
  rownames(DT) <- c("Day 1", "Day 2", "Day 3")
  print(DT)
 ( Vec <-  apply(DT, 2, max))
  class(Vec)
```

2.apply函數，輸入data.frame資料結構，輸出numeric向量

```{r echo=T, eval=FALSE}
  # 輸入data.frame資料結構，輸出numeric向量
  DT <- data.frame("獅子"=c(8,9,2),"斑馬"=c(5,7,2),"熊貓"=c(10,6,8))
  print(DT)
  (Vec <-  apply(DT, 2, max))
  class(Vec)
```

apply函數輸出如下

```{r echo=FALSE, eval=TRUE}
  # 輸入data.frame資料結構，輸出numeric向量
  DT <- data.frame("獅子"=c(8,9,2),"斑馬"=c(5,7,2),"熊貓"=c(10,6,8))
  print(DT)
  (Vec <-  apply(DT, 2, max))
  class(Vec)
```

## sapply/lapply用法

lapply 和 sapply 是 R 語言中常用的函數，兩者都是用來將一個函數應用到列表或向量的每個元素上，但它們在結果的返回形式上有所不同。以下是它們的主要差異及範例：

-   lapply()總是返回一個list，不管輸入的複雜程度如何。

-   sapply()則嘗試簡化輸出結果，盡可能將其化簡為向量或矩陣。

1.lapply處理向量，輸出list

```{r echo=T, eval=T}
# 使用 lapply 計算每個元素的平方
x <- 1:5  # 定義一個數組向量
result <- lapply(x, function(num) num^2) # 使用 lapply 計算每個元素的平方
print(result)
```

2.lapply處理list，輸出list

```{r echo=T, eval=T}
# 使用 lapply 計算每欄的總和
my_list <- list(a = 1:5, b = 6:10, c = 11:15)
result_lapply <- lapply(my_list, sum)
print(result_lapply)
```

3.  sapply處理向量，輸出向量

```{r echo=T, eval=T}
# 使用 sapply 計算每個元素的平方
x <- 1:5  # 定義一個數組向量
result <- sapply(x, function(num) num^2) # 使用 sapply 計算每個元素的平方
print(result)
```

4.sapply處理list，輸出向量

```{r echo=T, eval=T}
# 使用 sapply 計算每欄的總和
my_list <- list(a = 1:5, b = 6:10, c = 11:15)
result_lapply <- sapply(my_list, sum)
print(result_lapply)
```
