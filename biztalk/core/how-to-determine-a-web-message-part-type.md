---
title: "如何判斷 Web 訊息部分類型 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Web messages, message types
- Web services, Web messages
- Web messages, parts
ms.assetid: bdd1f604-ec35-41e3-b5a8-1e0ad0193eff
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6102e39eb38e919c68405ae18bebde0b46c0b053
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-determine-a-web-message-part-type"></a>如何判斷 Web 訊息部分類型
您可以使用指定之 Web 訊息類型的 [屬性] 視窗，判斷 Web 訊息部分類型是基本 .NET 類型還是結構描述類型。  
  
### <a name="to-determine-a-web-message-part-type"></a>若要判斷 Web 訊息部分類型  
  
1.  開啟，請在協調流程與**檢視**功能表上，按一下 **其他視窗**，然後按一下 **協調流程檢視**。  
  
2.  展開**多部分訊息類型** 節點，然後展開 Web 訊息類型。  
  
3.  選取訊息部分。  
  
     開頭為 Web 訊息部分簽章  **\<*專案預設命名空間*\>。\<*Web 參考名稱*\>。參考。\<*結構描述根*\>* * 是結構描述型別。   **\<*結構描述根*\>* * 類型的一部分是建構 Web 訊息部分的 Web 參考結構描述的根項目。 否則，訊息部分簽章是基本.NET 類型例如**System.String**或**System.Int32**。  
  
## <a name="see-also"></a>請參閱  
 [建構 Web 訊息](../core/constructing-web-messages.md)