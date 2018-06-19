---
title: 步驟 3： 建立專案並部署觸發程序事件 （訊息） |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- end-to-end tutorial, trigger events
- trigger events
ms.assetid: 5d21a923-fc2c-4d50-b146-daca0aa26e2a
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 49fd078f64cbd4163eef648f7a0d58fe6e8db6b2
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25961276"
---
# <a name="step-3-create-and-deploy-a-trigger-event-message-project"></a>步驟 3： 建立專案並部署觸發程序事件 （訊息）
在此步驟中，您可以建立結構描述觸發程序事件訊息。 例如，您可能許可放電和傳輸系統 (ADT) 醫院資訊系統 (HIS) 傳送訊息的人員。 您需要這個結構描述來定義訊息的格式。  
  
### <a name="to-create-the-project-for-the-trigger-event-message"></a>若要建立觸發程序事件訊息的專案  
  
1.  在[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]上**檔案**功能表上，指向**新增**，然後按一下 **專案**。  
  
2.  在 新增專案 對話方塊中**專案類型**區段中，展開**BizTalk 專案**，然後按一下  **BTAHL7Projects**。  
  
3.  在 範本 區段中，按一下**空白 BTAHL7 專案**，請在**名稱**方塊中，輸入**BTAHL7V231Body 專案**，然後按一下 **確定**。  
  
4.  在 方案總管 節點下的新專案中，以滑鼠右鍵按一下**參考**，然後按一下 **加入參考**。  
  
5.  在 加入參考 對話方塊上**專案**索引標籤上，選取**BTAHL7V231Common Project1**，按一下**新增**，然後按一下 **確定**。  
  
## <a name="step-3a-add-the-schema"></a>步驟 3A： 加入結構描述  
 使用下列程序，將新的結構描述加入至專案。  
  
#### <a name="to-add-the-schema-to-the-project"></a>將結構描述加入至專案  
  
1.  在 方案總管 中，以滑鼠右鍵按一下**BTAHL7V231Body 專案**，指向 **新增**，然後按一下 **新項目**。  
  
2.  在 [加入新項目] 對話方塊中**類別**區段中，展開**BizTalk 專案項目**，然後選取**BTAHL7 結構描述**。  
  
3.  在 [範本] 區段中，按兩下**BTAHL7 結構描述**。  
  
4.  在 [HL7 結構描述選取器] 對話方塊中，執行下列動作：  
  
    |使用|動作|  
    |--------------|----------------|  
    |**Message 類別**|保留預設的**V2.X**選取。|  
    |**版本**|選取**2.3.1**。|  
    |**訊息類型**|選取**ADT**。|  
    |**觸發程序事件**|選取**A03**。|  
  
5.  按一下**完成**將結構描述加入至專案。  
  
## <a name="step-3b-assign-a-strong-key-to-the-assembly-and-deploy"></a>步驟 3B： 指派強式金鑰組件和部署  
 若要將組件的強式金鑰，然後再部署組件使用下列程序。  
  
#### <a name="to-assign-a-strong-key-and-deploy-the-assembly"></a>指派強式金鑰，並部署組件  
  
1.  在 方案總管 中，以滑鼠右鍵按一下**BTAHL7V231Body 專案**，然後按一下 **屬性**。  
  
2.  在專案屬性頁 頁面中，按一下**組件**。  
  
3.  在右窗格中，向下捲動至**強式名稱**區段中，按一下右邊的欄位**組件金鑰檔案**，然後按一下省略符號 (**...**) 按鈕。  
  
4.  在 組件金鑰檔案 對話方塊中，瀏覽至\<*磁碟機*\>: \Program Files\Microsoft BizTalk\<版本\>Accelerator for HL7\SDK\End 端對端教學課程中，按一下  **key.snk**，然後按一下 **開啟**。  
  
5.  在 [專案屬性頁] 對話方塊中，按一下**確定**以儲存變更。  
  
6.  在 方案總管 中以滑鼠右鍵按一下**BTAHL7V231Body 專案**，然後按一下 **部署**。 確定成功的訊息出現在 [輸出] 視窗。  
  
    > [!NOTE]
    >  如果不成功的部署訊息，請使用[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]疑難排解您的結構描述。  
  
 若要繼續[步驟 4： 建立接收埠，以便接受 ADT ^ ADT 系統使用 MLLP 配接器從 A03 訊息](../../adapters-and-accelerators/accelerator-hl7/step-4-create-receive-port-to-accept-adt^a03-messages-from-adt-using-mllp.md)。