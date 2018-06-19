---
title: 擴充編碼支援 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 93a40fa6-d0da-416e-97fb-675ddde3f005
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9e36c3baff4ac33f2878295791bb3f6615c1b25d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22204830"
---
# <a name="extended-encoding-support"></a>擴充編碼支援
根據預設，接收 HL7 管線，BTAHL72X，僅支援 ASCII 編碼方式。 這表示，為相等的值大於 127 會被取代的輸入訊息中的任何字元"？"。 這是因為不會顯示具有相等值大於 127 個字元的 ASCII 字元集。  
  
 [!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)]提供兩個新的編碼方式的支援：  
  
-   西歐語系  
  
-   UTF-8  
  
 您建立並建置自訂管線元件實作擴充編碼支援。 自訂管線元件會使用 BTAHL7 2.X 解譯器。 您建立使用自訂的管線來處理訊息的接收位置。 若要測試的接收位置和自訂管線，您可以建立使用 BTAHL7 2.XSendPipeline 的傳送埠。  
  
### <a name="to-create-a-custom-pipeline"></a>若要建立自訂管線  
  
1.  在[!INCLUDE[btsVStudio2008](../../includes/btsvstudio2008-md.md)]，加入新**空白 BizTalk Server 專案**。  
  
2.  在 方案總管 中，以滑鼠右鍵按一下新的專案中，按一下**新增**，然後按一下 **新項目**。  
  
3.  在**加入新項目**對話方塊方塊中，加入新**接收管線**。  
  
4.  從管線工具箱，拖曳**BTAHL7 2.X 解譯器**到 「 管線 」 編輯器並將其放置**解譯**階段**放在此處**目標。  
  
    > [!NOTE]
    >  如果 BTAHL7 2.7 解譯器不在 [工具箱] 中，以滑鼠右鍵按一下工具箱] 中，按一下 [**選擇項目**。 在**選擇工具箱項目**對話方塊**BizTalk 管線元件**索引標籤上，選取**BTAHL7 2.X 解譯器**核取方塊，然後 **[確定]**.  
  
5.  在 [屬性] 窗格中**BTAHL7 2.X 解譯器**，從**編碼字元集**下拉式清單中，選取**西歐**或**UTF8**編碼方式。  
  
    > [!NOTE]
    >  HL7 僅支援 ASCII （預設值）、 歐洲 Western 和 UTF8 編碼方式。 請勿選取其他編碼選項，因為 HL7 不支援它們。  
  
6.  按一下 [ **檔案** ] 功能表上的 [ **全部儲存**]。  
  
7.  部署專案。  
  
     建立新接收位置，以繼續。  
  
### <a name="to-create-a-receive-location-that-uses-the-custom-pipeline"></a>若要建立使用自訂管線的接收位置  
  
1.  上**啟動**功能表上，按一下 **程式**，指向  [!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)]，然後按一下  **BizTalk Server 管理**。  
  
2.  在 BizTalk Server 管理主控台中，展開  [!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)] **管理**，依序展開**BizTalk 群組**，依序展開**應用程式**，依序展開 應用程式您指定的管線組件 (根據預設， **BizTalk Application 1**)，以滑鼠右鍵按一下**接收位置**，指向 **新增**，然後按一下**單向接收位置**。  
  
3.  在**接收位置屬性**對話方塊中，於**接收管線**下拉式清單中選取名稱的自訂管線，您所建立。 (這是自訂的管線物件，而不 BTAHL7 名稱 2 X 管線。)  
  
### <a name="to-create-a-send-port-to-test-the-receive-location-and-pipeline"></a>若要建立要測試的接收位置和管線的傳送埠  
  
1.  上**啟動**功能表上，按一下 **程式**，指向  [!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)]，然後按一下  **BizTalk Server 管理**。  
  
2.  在 BizTalk Server 管理主控台中，展開  [!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)] **管理**，依序展開**BizTalk 群組**，依序展開**應用程式**，依序展開 應用程式您指定的管線組件 (根據預設， **BizTalk Application 1**)，以滑鼠右鍵按一下**傳送埠**，指向 **新增**，然後按一下  **靜態單向傳送埠**。  
  
3.  在**傳送埠屬性**對話方塊中，於**傳送管線**下拉式清單中，選取**BTAHL72XSendPipeline**。  
  
### <a name="to-test-the-receive-location-and-pipeline"></a>若要測試的接收位置和管線  
  
-   卸除包含特殊字元和儲存具有相同的編碼成指定的接收位置的位置在自訂管線中所指定的檔案。 在 輸出位置的檔案應該保留的特殊字元。  
  
    > [!NOTE]
    >  如果您嘗試處理會使用不受支援的編碼方式的檔案 （請記住，只有 ASCII 西歐上，支援、 和 UTF8），錯誤會記錄在應用程式事件檢視器發生錯誤識別碼： 5633。  
  
    > [!NOTE]
    >  如果您要測試自訂管線設定為 UTF8 編碼方式，您應該附加位元組順序標記 (BOM) 字元至您傳遞的訊息。 如果您要測試自訂管線西歐編碼設定，請勿附加 BOM 字元。