---
title: 執行個體驗證 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f906f2e9-2bf9-448b-927f-dd2d7d9b2272
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0f4e4901d11bda5fb6633c00dd72899ee1b72db4
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37012871"
---
# <a name="instance-validation"></a>執行個體驗證
BizTalk 編輯器會叫用**IInstanceValidator.ValidateInstance**符合下列條件時，擴充功能的方法：  
  
- 延伸模組，會使用設定為標準**標準**屬性**結構描述**節點。  
  
- 在上**屬性頁**結構描述中，相關聯的對話方塊**產生的執行個體輸出類型**屬性設定為**原生。**  
  
- 在 **屬性頁**結構描述中，相關聯的對話方塊**輸入執行個體檔案名稱**屬性設定為包含要驗證的執行個體訊息的檔案名稱。  
  
  中指定的檔案**輸入執行個體檔案名稱**屬性會做為參數傳遞**IInstanceValidator.ValidateInstance**方法。  
  
  如果發生錯誤，錯誤訊息會傳回為陣列**IValidationInfo**物件，而且會顯示在[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]工作清單 視窗。  
  
> [!NOTE]
>  如果結構描述包含模式陳述式，而且檔案傳遞至**Poschema**方法所產生的對應**產生的執行個體**命令時，執行個體訊息可能無法通過驗證。  
  
## <a name="see-also"></a>另請參閱  
 [延伸 BizTalk 編輯器](../core/extending-biztalk-editor.md)