---
title: "執行個體產生 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 14060dca-5e14-474a-bf2c-4e8bc56e3c61
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 46bd3d2bc6852ec0c73fbbe4ffc55924a8012ce5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="instance-generation"></a>執行個體產生
BizTalk 編輯器會叫用**IInstanceGenerator.GenerateInstance**符合下列條件時的擴充方法：  
  
-   擴充功能，會使用設定為標準**標準**屬性**結構描述**節點。  
  
-   在**屬性頁**結構描述中，與相關聯的對話方塊**產生執行個體輸出類型**屬性設定為**原生。**  
  
-   在**屬性頁**結構描述中，與相關聯的對話方塊**輸出執行個體檔案名稱**屬性設定為輸出執行個體將會儲存至檔案的名稱。  
  
> [!NOTE]
>  如果**輸出執行個體檔案名稱**屬性未設定、 檔案的暫存資料夾中會使用預設名稱產生的執行個體訊息時，和 [輸出] 視窗中提供的連結。  
  
 之前**IInstanceValidator.ValidateInstance**呼叫方法，BizTalk 編輯器會產生範例 XML 執行個體訊息，並再將其傳遞到中指定的檔案**輸出執行個體檔案名稱**屬性或至該方法的預設檔案名稱。  
  
 如果發生錯誤，錯誤訊息會傳回為陣列**IValidationInfo**物件，並會顯示在[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]工作清單 視窗。  
  
## <a name="see-also"></a>另請參閱  
 [延伸 BizTalk 編輯器](../core/extending-biztalk-editor.md)