---
title: 步驟 7： 設定傳送埠以傳送通知給交易夥伴 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3a082870-894c-4f64-a575-3681d8a5c4ea
caps.latest.revision: 22
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bb00e99fc28c857e85d88733baced60299f58ef8
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36971495"
---
# <a name="step-7-configure-a-send-port-to-send-the-acknowledgment-to-your-trading-partner"></a>步驟 7： 設定傳送埠以傳送通知給交易夥伴
![步驟 9 的 7](../adapters-and-accelerators/wcf-lob-adapter-sdk/media/step-7of9.gif "Step_7of9")  

 您可以在此步驟中設定傳送埠以傳送所產生的 997 通知訊息[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]fabrikam **toTHEM_997**資料夾。  

## <a name="prerequisites"></a>先決條件  
 您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」群組的成員身分登入。  

### <a name="to-configure-a-send-port-that-subscribes-to-the-997-acknowledgment"></a>設定訂閱 997 通知的傳送埠  

1. 在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下**傳送埠**，指向**新增**，然後按一下 **靜態單向傳送埠**。  

2. 在 **傳送埠屬性**對話方塊方塊中，執行下列動作：  

   |使用|以進行此動作|  
   |--------------|----------------|  
   |**名稱**|輸入`toTHEM_997`。|  
   |**型別**|選取 **檔案**。|  
   |**設定**|按一下 **設定**。|  

   > [!NOTE]
   >  傳送埠的傳輸類型是 FILE，因為 997 是將傳送到資料夾的一般檔案。  

3. 在  **FILE 傳輸屬性**對話方塊方塊中，執行下列動作，然後按一下**確定**:  


   |        使用        |                                                                                                              以進行此動作                                                                                                              |
   |------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   | **目的地資料夾** | 按一下 [**瀏覽**，然後在**瀏覽資料夾** 對話方塊中，移至[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\EDI 介面 Developer Tutorial\ProcessEDI_TestLocations\ Scenario a\tothem_997。 |
   |     **檔案名稱**      |                                                                                           請輸入`%MessageID%.txt`，然後按一下 **[確定]**。                                                                                            |

   > [!NOTE]
   >  設定的值**檔案名**屬性，可確保，輸出檔案會使用副檔名.txt。  

4. 在 [**傳送埠屬性**] 對話方塊中，如**傳送管線**，選取**EdiSend**。  

   > [!NOTE]
   >  用來傳送 EDI 交換 (除了透過 AS2 傳輸所傳送的交換之外) 的傳送管線是 EdiSend 管線 (透過 AS2 傳輸所傳送的 EDI 交換則使用 AS2EdiSend 傳送管線傳送)。  

5. 在主控台樹狀目錄中，按一下**篩選**，然後執行下列操作：  


   |   使用   |                           以進行此動作                           |
   |--------------|----------------------------------------------------------------|
   | **屬性** |                  選取**BTS。MessageType**。                   |
   | **[運算子]** |                         選取  **==**。                         |
   |  **ReplTest1**   | 請輸入**<http://schemas.microsoft.com/Edi/X12#X12_997_Root>**。 |

   > [!NOTE]
   >  篩選條件可確保傳送埠將挑選 997 訊息類型的訊息。  

6. 按一下 [確定] 。  

7. 在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，按一下**傳送埠**。 以滑鼠右鍵按一下**toTHEM_997**，然後按一下**開始**登錄並啟動該連接埠。  

8. 在 BizTalk Server 管理主控台的主控台樹狀目錄中，按一下**平台設定**，然後按一下**主控件執行個體**。 在 [主控件執行個體] 窗格中，按一下**BizTalkServerApplication**，然後按一下**重新啟動**。  

## <a name="next-steps"></a>後續步驟  
 中所述，您會建立兩個交易夥伴之間的協議[步驟 8： 設定合作對象之間交易夥伴協議](../core/step-8-configure-the-trading-partner-agreement-between-the-parties.md)。  

## <a name="see-also"></a>另請參閱  
 [設定靜態傳送埠以傳送 EDI 交換和通知](../core/configuring-a-static-send-port-to-send-edi-interchanges-and-acknowledgments.md)