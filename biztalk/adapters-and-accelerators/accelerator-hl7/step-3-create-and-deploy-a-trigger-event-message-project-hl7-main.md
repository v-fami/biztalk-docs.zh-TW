---
title: "步驟 3： 建立及部署觸發程序事件 （訊息） Project_hl7_main |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: interrogative tutorial, trigger events
ms.assetid: 90b65ad1-7953-4009-a1eb-1c2a85c7980a
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ff7abfcf363d26d068fab067378eb61d5bcf5c3c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-3-create-and-deploy-a-trigger-event-message-projecthl7main"></a>步驟 3： 建立及部署觸發程序事件 （訊息） Project_hl7_main
在此步驟中，您可以建立使用觸發程序事件訊息的結構描述。 例如，許可放電和傳輸系統 (ADT)，傳送訊息醫院資訊系統 (HIS)。 您可以使用此結構描述來定義訊息的格式。  
  
### <a name="to-create-the-project-for-the-trigger-event-message"></a>若要建立觸發程序事件訊息的專案  
  
1.  在[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]上**檔案**功能表上，指向**新增**，然後按一下**專案**。  
  
2.  在 [新增專案] 對話方塊中**專案類型**清單中，展開**BizTalk 專案**，然後按一下 **BTAHL7Projects**。  
  
3.  在**範本**清單中，按一下**空白 BTAHL7 專案**。  
  
4.  在**名稱**欄位中，輸入**BTAHL7V24Body 專案**，然後按一下**確定**。  
  
5.  在 [方案總管] 中，您的新節點下方**BTAHL7V24Body**專案中，以滑鼠右鍵按一下**參考**，然後按一下**加入參考**。  
  
6.  在 [加入參考] 對話方塊中，按一下**專案**索引標籤上，選取**Interrogative_24Schemas**，按一下**新增**，然後按一下**確定**。  
  
## <a name="step-3a-add-the-schemas"></a>步驟 3A： 新增結構描述  
 使用下列程序，將新的結構描述加入至專案。  
  
#### <a name="to-add-the-schemas-to-the-project"></a>將結構描述加入至專案  
  
1.  在 方案總管 中，以滑鼠右鍵按一下**BTAHL7V24Body 專案**，指向 **新增**，然後按一下**新項目**。  
  
2.  在 [加入新項目] 對話方塊中，依序展開**BizTalk 專案項目**，然後按兩下**BTAHL7 結構描述**右窗格中。  
  
3.  在 [HL7 結構描述選取器] 對話方塊中，執行下列動作：  
  
    |使用|動作|  
    |--------------|----------------|  
    |**Message 類別**|保留**V2.X**選取。|  
    |**版本**|選取**2.4**。|  
    |**訊息類型**|選取**QRY**。|  
    |**觸發程序事件**|選取**Q01**。|  
  
4.  按一下**完成**將結構描述加入至專案。  
  
     這會建立查詢的結構描述檔案 QRY_Q01_24_GLO_DEF.xsd。  
  
    > [!NOTE]
    >  請勿關閉 [HL7 結構描述選取器] 對話方塊。  
  
5.  在 [HL7 結構描述選取器] 對話方塊中，執行下列動作：  
  
    |使用|動作|  
    |--------------|----------------|  
    |**Message 類別**|保留**V2.X**選取。|  
    |**版本**|選取**2.4**。|  
    |**訊息類型**|選取**DSR**。|  
    |**觸發程序事件**|選取**Q01**。|  
  
6.  按一下**完成**將結構描述加入至專案。  
  
     這會建立回應結構描述檔 DSR_Q01_24_GLO_DEF.xsd。  
  
7.  按一下**取消**關閉**HL7 結構描述選取器** 對話方塊。  
  
## <a name="step-3b-assign-a-strong-key-to-the-assembly-and-deploy"></a>步驟 3B： 指派強式金鑰組件和部署  
 若要將組件的強式金鑰，然後再部署組件使用下列程序。  
  
#### <a name="to-assign-a-strong-key-and-deploy-the-assembly"></a>指派強式金鑰，並部署組件  
  
1.  在 [方案總管] 中，以滑鼠右鍵按一下**BTAHL7V24Body**專案，然後再按一下**屬性**。  
  
2.  在**BTAHL7V24Body 屬性頁**對話方塊中，按一下 **組件**。  
  
3.  在右窗格中，向下捲動至**強式名稱**區段中，按一下右邊的欄位**組件金鑰檔案**，然後按一下省略符號 （...） 按鈕。  
  
4.  在**組件金鑰檔案**對話方塊中，瀏覽至\<*磁碟機*>: \Program Files\\ [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk\<版本 > Accelerator for HL7\SDK\Interrogative 教學課程，按一下**key.snk**，然後按一下**開啟**。  
  
5.  在**BTAHL7V24Body 屬性頁**對話方塊中，按一下 **確定**以儲存變更。  
  
6.  在 [方案總管] 中以滑鼠右鍵按一下**BTAHL7V24Body 專案**，然後按一下**部署**。 確定成功的訊息出現在 [輸出] 視窗。  
  
    > [!NOTE]
    >  如果不成功的部署訊息，請使用[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]疑難排解您的結構描述。  
  
 若要繼續[步驟 4： 建立接收埠，以便接受 ADT 查詢訊息](../../adapters-and-accelerators/accelerator-hl7/step-4-create-the-receive-port-for-accepting-adt-query-messages.md)。