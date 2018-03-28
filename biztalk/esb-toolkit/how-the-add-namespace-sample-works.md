---
title: 如何新增命名空間範例適用於 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c76a90a9-5898-43b3-98af-ff546dd97153
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 212364030353001cae0589d4d7562641db4b77e6
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
---
# <a name="how-the-add-namespace-sample-works"></a>如何新增命名空間範例的運作方式
第二，第一個和第四個測試會使用**加入命名空間**元件位於 NamespaceSampleReceivePipeline 管線。 它會採用做為輸入的文件沒有命名空間的根節點上，如下所示：  
  
```  
<CanonicalOrder OrderID="OrderID_0" OrderDate="OrderDate_1" Status="Status_2">  
```  
  
 下表顯示設定的屬性值**加入命名空間**元件。  
  
|屬性|型別|Value|  
|--------------|----------|-----------|  
|ExtractionNodeXPath|靜態|(空的)|  
|NamespaceBase|靜態|http://schemas.microsoft.biztalk.esb.test.com/test|  
|NamespacePrefix|靜態|esbTest|  
|分隔符號|靜態|/|  
|XPath|動態|/CanonicalOrder/@OrderID&#124;/CanonicalOrder/@OrderDate|  
  
 表所示的屬性設定會導致元件執行兩個 XPath 查詢來搜尋 XML 文件/CanonicalOrder/@OrderID和/CanonicalOrder/@OrderDate(兩個指定的查詢**Xpath**屬性，以 「 管道 」 分隔字元）。 這些查詢將傳回的值**OrderID**和**OrderDate**屬性的根節點的文件; 在此範例中，兩個值是"OrderID_0"和"OrderDate_1"。  
  
 元件會使用這些值，並在其他內容的值，建構新的根命名空間。 它結合了**NamespaceBase**、 **NamespacePrefix**、**分隔符號**，並以下列格式的兩個 XPath 查詢中的值：  
  
```  
xmlns:{NamespacePrefix}="{NamespaceBase}{Separator}{XPaths[1]}{Seperator}  
                         {XPaths[2]}{Separator}...{XPaths[n]}"  
```  
  
 這會產生新的命名空間，如下所示：  
  
```  
xmlns:esbTest="http://schemas.microsoft.biztalk.esb.test.com/test  
               /OrderID_0/OrderDate_1"  
```  
  
 因此，更新的文件處理後**NamespaceSampleReceivePipeline**管線如下所示：  
  
```  
<esbTest:CanonicalOrder xmlns:esbTest=  
    "http://schemas.microsoft.biztalk.esb.test.com/test/OrderID_0  
    /OrderDate_1" OrderID="OrderID_0" OrderDate="OrderDate_1"   
    Status="Status_2">  
```  
  
## <a name="using-the-extractionnodexpath-property"></a>使用 ExtractionNodeXPath 屬性  
 根據預設，**加入命名空間**加入命名空間和前置詞資訊時，元件會使用訊息內的 XML 文件的根項目。 如果您想要使用的 XML 文件子集做為訊息主體 （在某些案例中信封或一部分的輸入文件具有相關性有用），您可以設定**ExtractionNodeXPath**強制屬性**加入命名空間**来搜尋指定的項目，用於產生訊息的元件。 例如，如果您知道 CanonicalOrder 訊息將會有一個**OrderDetails**取用者，其包含此訊息相關的項目，您可以設定**ExtractionNodeXPath**屬性，以指定的路徑**OrderDetails**項目。 您可以查看加入透過擷取至通過測試稍早所述的程序的範例。  
  
> [!NOTE]
>  **ExtractionNodeXPath**屬性必須傳回只有一個元素的 XPath。 元件將會引發例外狀況，如果結果不是元素或 XPath 查詢傳回多個項目。