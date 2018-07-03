---
title: 步驟 2： 設定 Wcf-custom 單向傳送埠 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WCF-Custom one-way send port, configuring
- migration
ms.assetid: ae13222e-42e7-45a7-9b2a-0a6779b21736
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 662007dc6f75e1ca0459e53f576c816d23b71404
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37005719"
---
# <a name="step-2-configure-a-wcf-custom-one-way-send-port"></a>步驟 2： 設定 Wcf-custom 單向傳送埠
![步驟 3 之 2](../../adapters-and-accelerators/adapter-oracle-database/media/step-2of3.gif "Step_2of3")  
  
 **若要完成的時間：** 10 分鐘  
  
 **目標：** 在此步驟中，您可以設定 WCF 自訂連接埠來傳送一般檔案 IDOC 到 SAP 系統。 設定連接埠之後, 您可以設定使用 Wcf-custom 傳送埠的 BizTalk 應用程式。  
  
## <a name="prerequisites"></a>必要條件  
 您必須建置並部署 vPrev BizTalk 專案傳送 Idoc 至 SAP 系統。  
  
### <a name="to-configure-a-wcf-custom-one-way-send-port"></a>若要設定 Wcf-custom 單向傳送埠  
  
1. 啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。  
  
2. 在主控台樹狀目錄中，依序展開**BizTalk 群組**，然後展開**應用程式**。  
  
3. 展開您要在其下建立的傳送埠的應用程式。  
  
4. 以滑鼠右鍵按一下**傳送埠**，指向**新增**，然後按一下**靜態單向傳送埠**。  
  
5. 在 **傳送埠屬性**對話方塊的 **一般**索引標籤上，輸入傳送埠的名稱。  
  
6. 從**型別**下拉式清單中，選取**Wcf-custom**，然後按一下**設定**。  
  
7. 在  **Wcf-custom 傳輸屬性**對話方塊方塊中，執行下列動作：  
  
   1. 按一下 [**一般**] 索引標籤，然後在**位址 (URI)** 欄位中，指定連線 URI，將訊息傳送至 SAP 系統。 如需連線 URI 的詳細資訊，請參閱[建立 SAP 系統連接 URI](../../adapters-and-accelerators/adapter-sap/create-the-sap-system-connection-uri.md)。  
  
       ![指定傳送埠中的連線 URI](../../adapters-and-accelerators/adapter-sap/media/53ae71e1-89ec-49c5-8096-ff04a2c94c0a.gif "53ae71e1-89ec-49c5-8096-ff04a2c94c0a")  
  
   2. 在 **一般**索引標籤中，於**動作**文字方塊中，輸入作業的動作。 若要傳送一般檔案 IDOC，您必須使用**SendIdoc**公開的 WCF 為基礎的作業[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。 **SendIdoc**作業可讓配接器用戶端傳送 Idoc 具有弱式型別結構描述。 如需詳細資訊，請參閱 <<c0> [ 對 sap Idoc 的作業](../../adapters-and-accelerators/adapter-sap/operations-on-idocs-in-sap.md)。 下圖顯示**動作**文字方塊中的動作**SendIdoc**作業。  
  
       ![在 傳送埠中指定動作](../../adapters-and-accelerators/adapter-sap/media/94dd1505-5529-43cf-a27b-2588a022dfb9.gif "94dd1505-5529-43cf-a27b-2588a022dfb9")  
  
   3. 按一下 **繫結**索引標籤上，以及從**繫結的型別**下拉式清單中，選取**sapBinding**。  
  
   4. 按一下 **認證**索引標籤，然後指定要連接到 SAP 系統的認證。  
  
   5. 按一下 [**訊息**] 索引標籤，然後在**輸出 WCF 訊息內文**區段中，選擇**範本**選項。  
  
   6. 在  **XML**文字方塊中，指定將用來建構 WCF 訊息的範本。 這樣做，您建立符合訊息**SendIdoc** WCF 為基礎的作業[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。 如需有關的訊息結構**SendIdoc**作業，請參閱[IDOC 作業的訊息結構描述](../../adapters-and-accelerators/adapter-sap/message-schemas-for-idoc-operations.md)。  
  
       ![指定輸出 WCF 訊息的範本](../../adapters-and-accelerators/adapter-sap/media/909835c3-a941-49dc-87f0-858fe0e1fc63.gif "909835c3-a941-49dc-87f0-858fe0e1fc63")  
  
       SendIdoc 作業中，您必須指定下列範本：  
  
      ```  
      <SendIdoc xmlns="http://Microsoft.LobServices.Sap/2007/03/Idoc/">  
      <idocData><bts-msg-body xmlns="http://www.microsoft.com/schemas/bts2007" encoding="string"/></idocData>  
      </SendIdoc>  
      ```  
  
       在上述的範本中，`bts-msg-body`是建立使用一般檔案解譯器與檔案相關聯的 XML IDOC 接收埠。 XML IDOC 被封裝在 SendIdoc 訊息。  
  
   7. 按一下 **套用**，然後按一下**確定**。  
  
8. 在 [**傳送埠屬性**] 對話方塊中，從**傳送處理常式**下拉式清單中，選取**BizTalkServerApplication**。  
  
9. 從**傳送管線**下拉式清單中，選取**ConvertToFlatFile**。 這個一般檔案組合器管線已 vPrev BizTalk 專案的一部分，以及用來將 XML IDOC 轉換成一般檔案 IDOC。  
  
10. 按一下 [確定] 。  
  
### <a name="to-configure-the-biztalk-application"></a>若要設定的 BizTalk 應用程式  
  
1. 在 BizTalk Server 管理主控台中，依序展開**BizTalk 群組**，展開**應用程式**、 展開協調流程的部署位置的 BizTalk 應用程式。  
  
2. 以滑鼠右鍵按一下 BizTalk 應用程式，然後選取**設定**。  
  
3. 從左窗格中，按一下 協調流程設定。 從右窗格中，從**主機**下拉式清單中，選取 BizTalk 主控件執行個體。  
  
4. 底下**繫結**方塊中，將 BizTalk 協調流程的邏輯連接埠對應至 BizTalk Server 管理主控台中的實體連接埠。  
  
   1. 選取您將會卸除一般檔案 IDOC 的檔案連接埠。  
  
   2. 選取您稍早在本主題中建立 Wcf-custom 傳送埠。  
  
   3. 按一下 [確定] 。  
  
      設定應用程式的詳細資訊，請參閱 「 如何設定應用程式 」，網址[ http://go.microsoft.com/fwlink/?LinkId=102360 ](http://go.microsoft.com/fwlink/?LinkId=102360)。  
  
## <a name="next-steps"></a>後續步驟  
 您現在已完成移轉至 BizTalk 專案，以使用以 WCF 為基礎的 SAP 系統傳送 Idoc vPrev BizTalk 專案的[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。 您必須立即測試已移轉的 BizTalk 應用程式所傳送一般檔案 IDOC，如中所述[步驟 3： 測試移轉的應用程式](../../adapters-and-accelerators/adapter-sap/step-3-test-the-migrated-application2.md)。  
  
## <a name="see-also"></a>另請參閱  
 [教學課程 3：移轉 SAP 傳送 IDOC BizTalk 專案](../../adapters-and-accelerators/adapter-sap/tutorial-3-migrating-an-sap-send-idoc-biztalk-project.md)