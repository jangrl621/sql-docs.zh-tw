---
title: 使用 RevoScaleR 查詢和修改 SQL Server 資料
description: 有關如何在 SQL Server 上使用 R 語言來查詢和修改資料的教學課程逐步解說。
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/27/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 9bcf782e509263b087cfc599758ae9492b888aed
ms.sourcegitcommit: 321497065ecd7ecde9bff378464db8da426e9e14
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/01/2019
ms.locfileid: "68715518"
---
# <a name="query-and-modify-the-sql-server-data-sql-server-and-revoscaler-tutorial"></a>查詢和修改 SQL Server 資料 (SQL Server 和 RevoScaleR 教學課程)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

這一課是[RevoScaleR 教學](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md)課程的一部分, 說明如何搭配 SQL Server 使用[RevoScaleR 函數](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler)。

在上一課中, 您已將資料[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]載入。 在此步驟中, 您可以使用**RevoScaleR**來探索及修改資料:

> [!div class="checklist"]
> * 傳回變數的基本資訊
> * 從原始資料建立類別資料

類別資料或*因素變數*適用于探索式資料視覺效果。 您可以使用它們做為長條圖的輸入, 以瞭解變數資料看起來的樣子。

## <a name="query-for-columns-and-types"></a>查詢資料行和類型

使用 R IDE 或 Rgui.exe 來執行 R 腳本。 

首先，取得一份資料行和其資料類型的清單。 您可以使用函數[rxGetVarInfo](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxgetvarinfoxdf) , 並指定您想要分析的資料來源。 根據您的**RevoScaleR**版本而定, 您也可以使用[rxGetVarNames](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxgetvarnames)。 
  
```R
rxGetVarInfo(data = sqlFraudDS)
```

**結果**

```R
Var 1: custID, Type: integer
Var 2: gender, Type: integer
Var 3: state, Type: integer
Var 4: cardholder, Type: integer
Var 5: balance, Type: integer
Var 6: numTrans, Type: integer
Var 7: numIntlTrans, Type: integer
Var 8: creditLine, Type: integer
Var 9: fraudRisk, Type: integer
```

## <a name="create-categorical-data"></a>建立類別資料

所有的變數都會儲存為整數, 但某些變數代表在 R 中稱為「*要素變數*」的類別資料。例如, 資料行*狀態*包含用來作為50狀態識別碼加上哥倫比亞特區的數位。 為了讓您更輕鬆地了解資料，您將數字取代為各州縮寫的清單。

在此步驟中, 您會建立包含縮寫的字串向量, 然後將這些類別值對應至原始的整數識別碼。 接著, 您可以在*colInfo*引數中使用新的變數, 以指定要將此資料行當做一個因素來處理。 每當您分析或移動資料時, 就會使用縮寫, 並以一個因素的形式來處理資料行。

將資料行對應至縮寫，然後才使用它作為因數，實際上也能改善效能。 如需詳細資訊, 請參閱[R 和資料優化](../r/r-and-data-optimization-r-services.md)。

1. 一開始先建立 R 變數*stateAbb*, 並定義要新增至其中的字串向量, 如下所示。
  
    ```R
    stateAbb <- c("AK", "AL", "AR", "AZ", "CA", "CO", "CT", "DC",
        "DE", "FL", "GA", "HI","IA", "ID", "IL", "IN", "KS", "KY", "LA",
        "MA", "MD", "ME", "MI", "MN", "MO", "MS", "MT", "NB", "NC", "ND",
        "NH", "NJ", "NM", "NV", "NY", "OH", "OK", "OR", "PA", "RI","SC",
        "SD", "TN", "TX", "UT", "VA", "VT", "WA", "WI", "WV", "WY")
    ```

2. 接下來，建立名為 *ccColInfo*的資料行資訊物件，指定現有整數值對類別層級 (各州的縮寫) 的對應。
  
    此陳述式也會建立針對 gender 和 cardholder 的因素變數。
  
    ```R
    ccColInfo <- list(
    gender = list(
              type = "factor",
              levels = c("1", "2"),
              newLevels = c("Male", "Female")
              ),
    cardholder = list(
                  type = "factor",
                  levels = c("1", "2"),
                  newLevels = c("Principal", "Secondary")
                   ),
    state = list(
             type = "factor",
             levels = as.character(1:51),
             newLevels = stateAbb
             ),
    balance = list(type = "numeric")
    )
    ```
  
3. 若要建立[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]使用更新資料的資料來源, 請像之前一樣呼叫**RxSqlServerData**函數, 但新增*colInfo*引數。
  
    ```R
    sqlFraudDS <- RxSqlServerData(connectionString = sqlConnString,
    table = sqlFraudTable, colInfo = ccColInfo,
    rowsPerRead = sqlRowsPerRead)
    ```
  
    - 針對 *table* 參數，傳入變數 *sqlFraudTable*，其中包含您稍早建立的資料來源。
    - 針對 *colInfo* 參數，傳入 *ccColInfo* 變數，其中包含資料行資料類型和因素層級。

4.  您現在可以使用 **rxGetVarInfo** 函數檢視新資料來源中的變數。
  
    ```R
    rxGetVarInfo(data = sqlFraudDS)
    ```

    **結果**
    
    ```R
    Var 1: custID, Type: integer
    Var 2: gender  2 factor levels: Male Female
    Var 3: state   51 factor levels: AK AL AR AZ CA ... VT WA WI WV WY
    Var 4: cardholder  2 factor levels: Principal Secondary
    Var 5: balance, Type: integer
    Var 6: numTrans, Type: integer
    Var 7: numIntlTrans, Type: integer
    Var 8: creditLine, Type: integer
    Var 9: fraudRisk, Type: integer
    ```

現在您指定的三個變數 (*gender*、 *state*和 *cardholder*) 被視為因素。

## <a name="next-steps"></a>後續步驟

> [!div class="nextstepaction"]
> [定義及使用計算內容](../../advanced-analytics/tutorials/deepdive-define-and-use-compute-contexts.md)