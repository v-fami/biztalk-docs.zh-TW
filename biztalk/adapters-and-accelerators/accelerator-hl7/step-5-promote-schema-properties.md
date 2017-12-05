---
title: "步驟 5： 升級結構描述屬性 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- message enrichment tutorial, pomoted properties
- promoted properties
- schemas, promoted properties
ms.assetid: cb51cece-1b65-4ba2-b8e6-ce8b6694cdb6
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 91d68ece5bedf7ec46a6d5ede7efc6878fa972fc
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
---
# <a name="step-5-promote-schema-properties"></a>步驟 5： 升級結構描述屬性
在此步驟中，您將升級結構描述屬性，讓[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]協調流程可以參考您在稍後步驟中建立那些屬性值。 升級是一套機制，您使用參考訊息執行個體中的特定值，並且讓它存取[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]元件，例如協調流程或以內容為基礎的路由達成目的。 此外，升級的屬性會顯示[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]在 「 運算式編輯器的 IntelliSense [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]。  
  
> [!NOTE]
>  [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]稽核和記錄功能與 「 BizTalk 狀況與活動追蹤 (HAT) 工具可以追蹤只升級的結構描述屬性。  
  
### <a name="to-promote-schema-properties"></a>若要升級結構描述屬性  
  
1.  在 方案總管下**BTAHL7 專案**，連按兩下**DoorBell.xsd**開啟結構描述的節點。  
  
2.  以滑鼠右鍵按一下**FirstName**欄位項目，指向**升階**，然後按一下 **快速升級**。  
  
3.  按一下**確定**將屬性結構描述加入至專案。  
  
    > [!NOTE]
    >  [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]加入圖示的橙色圓形**FirstName**項目，表示已升級項目。  
  
4.  重複這些步驟將升級下列欄位項目：  
  
    -   **MiddleName**  
  
    -   **LastName**  
  
    -   **SSN**  
  
    > [!IMPORTANT]
    >  請務必注意例如身分證號碼 (SSN) 會導致該升級一位病患識別碼 (PID)[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]追蹤整個系統的每個輸入訊息屬性。 造成這種情況的副作用是，訊息追蹤資料庫會保留一份病患 s s n s。 這樣可以建立重大的安全性問題。 您必須保護這個資料存放區，與必須特別小心，或完全避免 PID 資料的升級。  
  
     如需追蹤您已升級的結構描述項目為基礎的文件的詳細資訊，請參閱 < BizTalk Server 說明的健全狀況與活動追蹤的詳細資訊。  
  
 若要繼續[步驟 6： 驗證結構描述](../../adapters-and-accelerators/accelerator-hl7/step-6-validate-the-schemas.md)。  
  
## <a name="see-also"></a>請參閱  
 [訊息擴充教學課程](../../adapters-and-accelerators/accelerator-hl7/message-enrichment-tutorial.md)