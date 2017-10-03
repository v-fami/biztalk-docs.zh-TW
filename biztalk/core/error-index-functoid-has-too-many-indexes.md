---
title: "錯誤-索引運算質有太多索引 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: bts10.map.error.indexFunctoidHasTooManyIndices
ms.assetid: 5dd2d5b4-3f7a-45be-b6f4-708b0a76805a
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4899ec5f03e3474e61e4272ffd0612c77c90ea32
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="error---index-functoid-has-too-many-indexes"></a>錯誤-索引運算質有太多索引
**錯誤碼**  
  
 btm1016  
  
 **說明**  
  
 指定**索引**運算質有太多索引輸入的參數指定。 索引輸入參數數目不能超過上階迴圈的數目**記錄**節點**欄位**節點指定為巢狀的第一個輸入的參數。  
  
 **使用者動作**  
  
 選取指定**索引**運算質，按一下省略符號 (**...**) 相關聯的按鈕**輸入參數**屬性在 microsoft[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]屬性 視窗中，然後在**設定\<運算質 > 運算質**對話方塊中，刪除多餘的索引輸入參數，選取並按一下![](../core/media/bts-tls-paramdelete.gif "bts_tls_paramdelete")為每個按鈕。