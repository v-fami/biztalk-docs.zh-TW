---
title: 錯誤-索引運算質沒有任何索引 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.map.error.indexFunctoidHasNoIndex
ms.assetid: a523705e-6134-4d98-8ea6-dbfc7b43dae5
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0159d308c9befc90590d281351409ba571921a53
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25968436"
---
# <a name="error---index-functoid-has-no-index"></a>錯誤-索引運算質沒有任何索引
**錯誤碼**  
  
 btm1014  
  
 **說明**  
  
 已提供任何索引值為指定**索引**運算質。  
  
 **使用者動作**  
  
 提供適當的索引輸入參數數目為指定**索引**運算質，其由迴圈的數目決定適當的數字**記錄**節點**欄位**巢狀來源結構描述中的節點。 若要建立索引輸入的參數，請選取指定的運算質，按一下省略符號 (**...**) 相關聯的按鈕**輸入參數**屬性在 microsoft[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]屬性 視窗中，然後使用![](../core/media/bts-tls-paraminsert.gif "bts_tls_paraminsert")按鈕內**設定\<運算質\>運算質**對話方塊以新增一或多個常數輸入的參數，其中第一個代表直屬父索引迴圈**記錄**節點，然後後續索引輸入參數代表越來越外層的上階迴圈**記錄**節點。