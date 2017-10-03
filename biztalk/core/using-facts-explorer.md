---
title: "使用 [事實總管] |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Business Rule Composer, Facts Explorer
- business rules, vocabularies
- business rules, schemas
- business rules, databases
- business rules, .NET classes
- Facts Explorer [Business Rule Composer]
ms.assetid: ee125eb1-d5b9-4121-8a25-fcb7a640570e
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f4c84b01625bb1566d02c1679bfadd0100b7b406
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="using-facts-explorer"></a>使用 [事實總管]
[事實總管] 包含四個索引標籤：**詞彙**， **XML 結構描述**，**資料庫**，和**.NET 類別**。  
  
## <a name="vocabularies-tab"></a>詞彙索引標籤  
 使用**詞彙** 索引標籤管理詞彙版本及定義 事實總管 中的。  
  
 使用捷徑功能表來存取下列選項。  
  
|使用|動作|  
|--------------|----------------|  
|**加入新詞彙**|建立新詞彙。|  
|**加入新的版本**|建立選取詞彙的新空白版本。 您可以複製其他版本的定義貼到新版本。|  
|**貼上詞彙版本**|貼上先前複製的詞彙版本內容做為選取詞彙的新版本。|  
|**Delete**|刪除選取的詞彙及其所有版本。|  
|**加入新的定義**|啟動 [詞彙定義精靈]，在選取的詞彙版本中建立新定義。|  
|**儲存**|儲存對選取詞彙及其定義所作的變更。|  
|**發行**|發佈選取的詞彙版本。 請注意，您無法直接修改已發佈的版本。 您可以複製已發佈的版本並貼到詞彙的新版本。|  
|**重新載入**|重新載入選取的詞彙版本及其定義，可以選擇是否捨棄對該版本所做的目前變更，並從規則存放區還原其內容。|  
|**修改**|啟動 [詞彙定義精靈]，變更選取的定義。 請注意，您無法修改屬於已發佈詞彙版本之一部分的定義。|  
|**移至來源事實**|對於選取的定義，請移至 .NET 組件、XML 結構描述或資料庫資料表中的對應來源事實。|  
  
## <a name="xml-schemas-tab"></a>XML 結構描述索引標籤  
 瀏覽 XSD 結構描述尋找 XML 項目和屬性的定義。 您可以拖曳項目拖曳至未發佈的詞彙版本上**詞彙**索引標籤上，以建立定義，或您可以將項目拖曳到條件編輯器或動作編輯器，以定義述詞、 動作和引數。  
  
|使用|動作|  
|--------------|----------------|  
|**選取根節點**|選取要從包含多個根節點的 XML 結構描述載入的根節點。|  
  
## <a name="databases-tab"></a>資料庫索引標籤  
 瀏覽資料庫伺服器尋找資料庫和資料表定義。 您可以拖曳項目拖曳至未發佈的詞彙版本上**詞彙**索引標籤上，以建立定義，或您可以將項目拖曳到條件編輯器或動作編輯器，以定義述詞、 動作和引數。  
  
## <a name="net-classes-tab"></a>.NET 類別索引標籤  
 瀏覽 .NET 組件尋找 .NET 公開類別定義。 您可以拖曳項目拖曳至未發佈的詞彙版本上**詞彙**索引標籤上，以建立定義，或您可以將項目拖曳到條件編輯器或動作編輯器，以定義述詞、 動作和引數。  
  
|使用|動作|  
|--------------|----------------|  
|**瀏覽**|從全域組件快取載入 .NET 組件|  
|**移除**|移除 .NET 組件|