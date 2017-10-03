---
title: "錯誤-運算質變數輸入不符 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: bts10.map.error.functoidVariableInputMismatch
ms.assetid: fda3066b-d0de-4f61-b78f-4726f6796e1f
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c619c1eded27cb3ac17bcc5a1630a367deaad078
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="error---functoid-variable-input-mismatch"></a>錯誤-運算質變數輸入不符
**錯誤碼**  
  
 btm1011  
  
 **說明**  
  
 指出的運算質未指定正確的輸入參數數目。 輸入參數的數目必須介於指定的範圍間。  
  
 **使用者動作**  
  
 使用下列一或多種方式，針對指定的運算質提供指定數目的輸入參數，應特別注意輸入參數的順序：  
  
-   若要建立其他連結，請使用拖曳方式在指定的運算質與來源結構描述中之節點或其他運算質之輸出間建立連結，這些節點位於指定運算質左邊的地圖格線頁中。  
  
-   若要建立其他連結，請選取指定的運算質，按一下省略符號 (**...**) 相關聯的按鈕**輸入參數**屬性在 microsoft[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]屬性 視窗中，然後設定並重新安排輸入參數順序**設定\<運算質 > 運算質** 對話方塊。 您可以在此對話方塊中建立常數輸入參數、賦予這些參數值，並使用相對於其他輸入參數的順序排列這些參數。  
  
-   若要移除現有連結，為每個連線到指定的運算質左側的連結連結上按一下滑鼠右鍵，然後按一下 **刪除**。  
  
-   若要移除現有連結，選取指定的運算質，請按一下省略符號 (**...**) 相關聯的按鈕**輸入參數**屬性[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]屬性 視窗中，然後在**設定\<運算質 > 運算質**對話方塊方塊中，選取並按一下刪除所有的輸入參數![](../core/media/bts-tls-paramdelete.gif "bts_tls_paramdelete")為每個按鈕。 您必須使用此方式來刪除常數輸入參數。