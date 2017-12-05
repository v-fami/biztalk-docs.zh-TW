---
title: "錯誤-表格迴圈資料無效 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: bts10.map.error.tableLoopingDataNotValid
ms.assetid: 19c38e79-bab0-4899-ae24-e1485327e891
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9478026980ecaf3e2049773737250c56d18262c8
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="error---table-looping-data-not-valid"></a>錯誤-表格迴圈資料無效
**錯誤碼**  
  
 btm1065  
  
 **說明**  
  
 關聯的相關資料的資料表**表格迴圈**運算質不是有效的可能是因為運算質，或設定不正確的表格迴圈格線設定不正確第二個輸入參數。  
  
 **使用者動作**  
  
 請確定輸入的參數**表格迴圈**運算質，透過 **輸入參數**屬性和**設定\<運算質\>運算質**對話方塊中，您可以在下表所示。  
  
|「表格迴圈」運算質輸入參數編號|Description|  
|---------------------------------------------------|-----------------|  
|1|輸入執行個體訊息從一筆記錄的連結或來源結構描述中的欄位，其中發生次數控制的一組相關聯的次數**表格抽選程式**運算質會執行。|  
|2|透過設定資料表中的資料行數目**表格迴圈格線**屬性之相關**表格迴圈**運算質。|  
|3 – 100|常數與連結 (來自來源結構描述或其他運算質的輸出)，它們將會成為表格迴圈格線的可能資料來源。|  
  
 此外，請確定您正確設定表格迴圈格線中，透過 [**表格迴圈格線**屬性和**表格迴圈組態**] 對話方塊。 常數或連結的值必須選擇將用來存取每一個儲存格相關聯的**表格抽選程式**運算質。