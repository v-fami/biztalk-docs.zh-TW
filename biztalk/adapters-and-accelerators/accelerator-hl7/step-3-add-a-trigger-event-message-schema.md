---
title: "步驟 3： 新增觸發程序事件 （訊息） 結構描述 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fc4a67d9-9582-4f2b-9bc9-18fbff823d29
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a4eed7ead2f0d50e7841ed6c39ffdcee86c6524f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-3-add-a-trigger-event-message-schema"></a>步驟 3： 新增觸發程序事件 （訊息） 結構描述
在此步驟中，您會建立空的新專案[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]專案範本。 加入此專案中，您將結構描述，[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]用來驗證內送的批次中的訊息 (ADT ^ A03)。 您將參考加入包含 v2.3.1 通用結構描述的專案，專案中，指派強式名稱，然後再部署專案。  
  
### <a name="to-add-the-project-containing-the-message-schema"></a>若要加入包含訊息結構描述的專案  
  
1.  在[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]上**檔案**功能表上，指向**新增**，然後按一下 **專案**。  
  
2.  在 [新增專案] 對話方塊中**專案類型**區段中，展開**BizTalk 專案**，然後選取**BTAHL7Projects**。  
  
3.  在**範本**區段中，選取**空白 BTAHL7 專案**。  
  
4.  在**名稱**方塊中，輸入**BTAHL7V231Body**做為專案名稱。  
  
5.  在**方案**方塊中，選取**將加入至方案**。  
  
6.  按一下 **[確定]**。  
  
7.  在 方案總管 節點下的新專案中，以滑鼠右鍵按一下**參考**，然後按一下 **加入參考**。  
  
8.  在 加入參考 對話方塊上**專案**索引標籤上，按一下  **BTAHL7V231Common 專案**中**專案名稱**資料行中，按一下 **新增**，然後按一下 **確定**。  
  
### <a name="to-add-the-schema-to-the-project"></a>將結構描述加入至專案  
  
1.  在 方案總管 中，以滑鼠右鍵按一下**BTAHL7V231Body**，指向 **新增**，然後按一下 **新項目**。  
  
2.  在 加入新項目 對話方塊中，依序展開**BizTalk 專案項目**，然後按一下  **BTAHL7 結構描述**。 在**範本** 窗格中，按一下  **BTAHL7 結構描述**，然後按一下 **新增**。  
  
3.  在**HL7 結構描述選取器**對話方塊方塊中，執行下列動作：  
  
    |使用|動作|  
    |--------------|----------------|  
    |**Message 類別**|保留**V2.X**為選取狀態。|  
    |**版本**|選取**2.3.1**。|  
    |**訊息類型**|選取**ADT**。|  
    |**觸發程序事件**|選取**A03**。|  
  
4.  按一下**建立**將結構描述加入至專案，然後按一下 **取消**以關閉對話方塊。 請注意該 BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 已加入 BTAHL7V231Body 專案 ADT_A03_231_GLO_DEF.xsd 結構描述。  
  
### <a name="to-assign-a-strong-key-and-deploy"></a>指派強式金鑰和部署  
  
1.  在 方案總管 中，以滑鼠右鍵按一下**BTAHL7V231Body**，然後按一下 **屬性**。  
  
2.  在 [BTAHL7V231Body 屬性頁] 對話方塊中，按一下**簽署**。  
  
3.  請檢查**簽署組件**核取方塊。  
  
4.  在**選擇強式名稱金鑰檔**下拉式清單中，選取**\<瀏覽 >。**  
  
5.  瀏覽至  **\<*磁碟機*>: \Batching 教學課程 * *，選取**key.snk**，然後按一下 **開啟**。  
  
6.  在 方案總管 中，以滑鼠右鍵按一下**BTAHL7V231Body**，然後按一下 **部署**。 請在 [輸出] 視窗中出現的成功訊息。  
  
    > [!NOTE]
    >  如果未出現 successful-deploy 訊息，使用[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]疑難排解您的結構描述。  
  
 若要繼續[步驟 4： 建立接收埠，以便接受批次訊息](../../adapters-and-accelerators/accelerator-hl7/step-4-create-a-receive-port-for-accepting-the-batch-message.md)。