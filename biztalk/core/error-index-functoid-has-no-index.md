---
title: "錯誤-索引運算質沒有任何索引 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: bts10.map.error.indexFunctoidHasNoIndex
ms.assetid: a523705e-6134-4d98-8ea6-dbfc7b43dae5
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8143442b9d77d6881efe2b64dfb7f5888ab2d466
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="error---index-functoid-has-no-index"></a>錯誤-索引運算質沒有任何索引
**錯誤碼**  
  
 btm1014  
  
 **說明**  
  
 已提供任何索引值為指定**索引**運算質。  
  
 **使用者動作**  
  
 提供適當的索引輸入參數數目為指定**索引**運算質，其由迴圈的數目決定適當的數字**記錄**節點**欄位**巢狀來源結構描述中的節點。 若要建立索引輸入的參數，請選取指定的運算質，按一下省略符號 (**...**) 相關聯的按鈕**輸入參數**屬性在 microsoft[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]屬性 視窗中，然後使用![](../core/media/bts-tls-paraminsert.gif "bts_tls_paraminsert")按鈕內**設定\<運算質 > 運算質**對話方塊以新增一或多個常數輸入的參數，其中第一個代表直屬父迴圈索引**記錄**節點，然後後續索引輸入的參數代表越來越外層的上階迴圈**記錄**節點。