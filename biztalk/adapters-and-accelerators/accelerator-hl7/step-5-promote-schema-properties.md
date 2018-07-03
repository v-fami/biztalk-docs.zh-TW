---
title: 步驟 5： 升級結構描述屬性 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- message enrichment tutorial, pomoted properties
- promoted properties
- schemas, promoted properties
ms.assetid: cb51cece-1b65-4ba2-b8e6-ce8b6694cdb6
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 60aa8681e9647e592af3173295c3d32e216f1f2d
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37003215"
---
# <a name="step-5-promote-schema-properties"></a>步驟 5： 升級結構描述屬性
在此步驟中，您將升級結構描述屬性以便[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]協調流程可以參考您在稍後步驟中建立的那些屬性值。 升級是一種機制，用以參考內的訊息執行個體特定值，並讓它能夠存取[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]如協調流程，或以內容為基礎的路由目的的元件。 此外，升級的屬性是由 Microsoft IntelliSense 在運算式編輯器的可見[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]。  
  
> [!NOTE]
>  [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] 稽核和記錄功能，使用 「 BizTalk 狀況與活動追蹤 (HAT) 工具可以追蹤只升級的結構描述屬性。  
  
### <a name="to-promote-schema-properties"></a>若要升級結構描述屬性  
  
1. 在 方案總管底下**BTAHL7 專案**，按兩下**DoorBell.xsd**開啟結構描述的節點。  
  
2. 以滑鼠右鍵按一下**FirstName**欄位項目中，指向**升階**，然後按一下**快速升級**。  
  
3. 按一下 **確定**將屬性結構描述加入至專案。  
  
   > [!NOTE]
   >  [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] 加入的圖示中的橘色的圓形**FirstName**項目，表示已升級的項目。  
  
4. 重複上述步驟來升級下列欄位項目：  
  
   -   **MiddleName**  
  
   -   **lastName**  
  
   -   **SSN**  
  
   > [!IMPORTANT]
   >  請務必請注意，例如社會安全號碼 (SSN) 會導致該升級病患識別碼 (PID)[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]追蹤整個系統的每個輸入訊息屬性。 這種情況造成的副作用是，訊息追蹤資料庫會保留一份病患 Ssn。 這可能產生顯著的安全性問題。 您必須保護必須特別小心使用此資料存放區，或完全避免 PID 資料的升級。  
  
    如需追蹤您已升級的結構描述項目為基礎的文件的詳細資訊，請參閱 BizTalk Server 說明健全狀況與活動追蹤的詳細資訊。  
  
   請繼續進行[步驟 6： 驗證結構描述](../../adapters-and-accelerators/accelerator-hl7/step-6-validate-the-schemas.md)。  
  
## <a name="see-also"></a>另請參閱  
 [訊息擴充教學課程](../../adapters-and-accelerators/accelerator-hl7/message-enrichment-tutorial.md)