---
title: 如何新增命名空間範例運作 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c76a90a9-5898-43b3-98af-ff546dd97153
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 33fc168ff5461ffc4145e83efaf2192cbc785820
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36975063"
---
# <a name="how-the-add-namespace-sample-works"></a>如何新增命名空間範例運作
第二，第一個和第四個測試會使用**新增的命名空間**元件位於 NamespaceSampleReceivePipeline 管線。 它會作為輸入的文件，在沒有命名空間的根節點上，如下所示：  

```  
<CanonicalOrder OrderID="OrderID_0" OrderDate="OrderDate_1" Status="Status_2">  
```  

 下表顯示設定的屬性值**新增的命名空間**元件。  


|      屬性       |  類型   |                          ReplTest1                           |
|---------------------|---------|----------------------------------------------------------|
| ExtractionNodeXPath | 靜態  |                         (空的)                          |
|    NamespaceBase    | 靜態  |    http://schemas.microsoft.biztalk.esb.test.com/test    |
|   NamespacePrefix   | 靜態  |                         esbTest                          |
|      分隔符號      | 靜態  |                            /                             |
|       XPath        | 動態 | /CanonicalOrder/@OrderID&#124;/CanonicalOrder/@OrderDate |

 表所示的屬性設定會導致要執行兩個 XPath 查詢來搜尋 XML 文件的元件/CanonicalOrder/@OrderID並/CanonicalOrder/@OrderDate(針對指定的兩個查詢**Xpath**屬性，以分隔的 「 管道 」字元）。 這些查詢傳回的值**OrderID**並**OrderDate**屬性的根節點的文件; 在此範例中，兩個值會是"OrderID_0 」 和 「 OrderDate_1"。  

 此元件接著會使用這些值和其他內容中的值建構新的根命名空間。 它結合了**NamespaceBase**，則**NamespacePrefix**，則**分隔符號**，並以下列格式的兩個 XPath 查詢中的值：  

```  
xmlns:{NamespacePrefix}="{NamespaceBase}{Separator}{XPaths[1]}{Seperator}  
                         {XPaths[2]}{Separator}...{XPaths[n]}"  
```  

 這會產生新的命名空間，如下所示：  

```  
xmlns:esbTest="http://schemas.microsoft.biztalk.esb.test.com/test  
               /OrderID_0/OrderDate_1"  
```  

 因此，更新的文件處理後**NamespaceSampleReceivePipeline**管線如下：  

```  
<esbTest:CanonicalOrder xmlns:esbTest=  
    "http://schemas.microsoft.biztalk.esb.test.com/test/OrderID_0  
    /OrderDate_1" OrderID="OrderID_0" OrderDate="OrderDate_1"   
    Status="Status_2">  
```  

## <a name="using-the-extractionnodexpath-property"></a>使用 ExtractionNodeXPath 屬性  
 根據預設，**新增的命名空間**元件會新增命名空間和前置詞的資訊時，會使用訊息內的 XML 文件的根項目。 如果您想要使用的 XML 文件子集做為訊息主體 （在某些信封的情況下，或只包含輸入文件的一部分有關聯性時，此項會很有用），您可以設定**ExtractionNodeXPath**強制的屬性**新增命名空間**来搜尋指定的項目，用於產生訊息的元件。 例如，如果您知道已接收的 CanonicalOrder 訊息將會有一個**OrderDetails**其內所含此訊息的取用者相關的項目，您可以設定**ExtractionNodeXPath**屬性，以指定的路徑**OrderDetails**項目。 您可以看到此程序的新增透過擷取至稍早所述的傳遞測試的範例。  

> [!NOTE]
>  **ExtractionNodeXPath**屬性必須傳回只有一個元素的 XPath。 此元件將會引發例外狀況，如果結果不是元素或 XPath 查詢傳回多個項目。