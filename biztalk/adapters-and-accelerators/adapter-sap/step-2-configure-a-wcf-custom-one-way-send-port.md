---
title: 步驟 2： 設定 Wcf-custom 單向傳送埠 |Microsoft 文件
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
ms.openlocfilehash: 8aab14799076d3f774130b357ab90c5ed5335f4a
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25962788"
---
# <a name="step-2-configure-a-wcf-custom-one-way-send-port"></a>步驟 2： 設定 Wcf-custom 單向傳送埠
![步驟 3 之 2](../../adapters-and-accelerators/adapter-oracle-database/media/step-2of3.gif "Step_2of3")  
  
 **若要完成的時間：** 10 分鐘  
  
 **目標：** 在此步驟中，您可以設定 WCF 自訂連接埠來傳送一般檔案 IDOC 到 SAP 系統。 設定連接埠之後, 您可以設定使用 Wcf-custom 傳送埠的 BizTalk 應用程式。  
  
## <a name="prerequisites"></a>必要條件  
 您必須建立和部署 vPrev BizTalk 專案，以傳送 Idoc 至 SAP 系統。  
  
### <a name="to-configure-a-wcf-custom-one-way-send-port"></a>若要設定 Wcf-custom 單向傳送埠  
  
1.  啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。  
  
2.  在主控台樹狀目錄中，依序展開**BizTalk 群組**，然後展開**應用程式**。  
  
3.  展開您要在其下建立傳送埠的應用程式。  
  
4.  以滑鼠右鍵按一下**傳送埠**，指向 **新增**，然後按一下**靜態單向傳送埠**。  
  
5.  在**傳送埠屬性**對話方塊**一般**索引標籤上，輸入傳送埠的名稱。  
  
6.  從**類型**下拉式清單中，選取**Wcf-custom**，然後按一下 **設定**。  
  
7.  在**Wcf-custom 傳輸屬性**對話方塊方塊中，執行下列動作：  
  
    1.  按一下**一般** 索引標籤，然後在**位址 (URI)** 欄位中，指定連線將訊息傳送至 SAP 系統的 URI。 如需連線 URI 的詳細資訊，請參閱[建立 SAP 系統連接 URI](../../adapters-and-accelerators/adapter-sap/create-the-sap-system-connection-uri.md)。  
  
         ![指定傳送埠中的連線 URI](../../adapters-and-accelerators/adapter-sap/media/53ae71e1-89ec-49c5-8096-ff04a2c94c0a.gif "53ae71e1-89ec-49c5-8096-ff04a2c94c0a")  
  
    2.  在**一般**索引標籤的**動作**文字方塊中，輸入作業的動作。 若要傳送一般檔案 IDOC，您必須使用**SendIdoc**作業由 WCF 基礎[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。 **SendIdoc**作業可讓配接器用戶端傳送 Idoc 具有弱式型別的結構描述。 如需詳細資訊，請參閱[sap Idoc 的作業](../../adapters-and-accelerators/adapter-sap/operations-on-idocs-in-sap.md)。 下圖顯示**動作**文字方塊的動作與**SendIdoc**作業。  
  
         ![在 傳送埠中指定動作](../../adapters-and-accelerators/adapter-sap/media/94dd1505-5529-43cf-a27b-2588a022dfb9.gif "94dd1505-5529-43cf-a27b-2588a022dfb9")  
  
    3.  按一下**繫結** 索引標籤，並從**繫結的型別**下拉式清單中，選取**sapBinding**。  
  
    4.  按一下**認證**索引標籤並指定要連接到 SAP 系統的認證。  
  
    5.  按一下**訊息** 索引標籤，然後在**輸出 WCF 訊息內文**區段中，選擇**範本**選項。  
  
    6.  在**XML**文字方塊中，指定將用來建構 WCF 訊息的範本。 如此一來，您會建立符合訊息**SendIdoc** WCF 為基礎的作業[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。 如需有關的訊息結構**SendIdoc**作業，請參閱[IDOC 作業的訊息結構描述](../../adapters-and-accelerators/adapter-sap/message-schemas-for-idoc-operations.md)。  
  
         ![指定輸出 WCF 訊息的範本](../../adapters-and-accelerators/adapter-sap/media/909835c3-a941-49dc-87f0-858fe0e1fc63.gif "909835c3-a941-49dc-87f0-858fe0e1fc63")  
  
         SendIdoc 作業中，您必須指定下列範本：  
  
        ```  
        <SendIdoc xmlns="http://Microsoft.LobServices.Sap/2007/03/Idoc/">  
        <idocData><bts-msg-body xmlns="http://www.microsoft.com/schemas/bts2007" encoding="string"/></idocData>  
        </SendIdoc>  
        ```  
  
         在上述範本中，`bts-msg-body`是 XML IDOC 建立使用一般檔案解譯器與檔案相關聯的接收埠。 XML IDOC 被封裝在 SendIdoc 訊息。  
  
    7.  按一下**套用**，然後按一下 **確定**。  
  
8.  在**傳送埠屬性**對話方塊中，從**傳送處理常式**下拉式清單中，選取**BizTalkServerApplication**。  
  
9. 從**傳送管線**下拉式清單中，選取**ConvertToFlatFile**。 這個一般檔案組合器管線已 vPrev BizTalk 專案的一部分，用來將 XML IDOC 轉換成一般檔案 IDOC。  
  
10. 按一下 **[確定]**。  
  
### <a name="to-configure-the-biztalk-application"></a>若要設定 BizTalk 應用程式  
  
1.  在 BizTalk Server 管理主控台中，展開  **BizTalk 群組**，依序展開**應用程式**、 展開協調流程部署所在的 BizTalk 應用程式。  
  
2.  以滑鼠右鍵按一下 BizTalk 應用程式，然後選取**設定**。  
  
3.  從左窗格中，按一下 協調流程設定。 從右窗格中，從**主機**下拉式清單中，選取 BizTalk 主控件執行個體。  
  
4.  在下**繫結**方塊中，將 BizTalk 協調流程的邏輯連接埠對應到 BizTalk Server 管理主控台中的實體連接埠。  
  
    1.  選取您將在此置放一般檔案 IDOC 的檔案連接埠。  
  
    2.  選取您稍早在本主題中所建立的 WCF 自訂傳送連接埠。  
  
    3.  按一下 **[確定]**。  
  
     如需有關如何設定應用程式的詳細資訊，請參閱 「 如何設定應用程式 」 在[http://go.microsoft.com/fwlink/?LinkId=102360](http://go.microsoft.com/fwlink/?LinkId=102360)。  
  
## <a name="next-steps"></a>後續步驟  
 您現在已完成的 vPrev BizTalk 專案，以傳送 Idoc 到 SAP 系統使用 WCF 為基礎的 BizTalk 專案移轉[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。 您必須現在測試已移轉的 BizTalk 應用程式傳送一般檔案 IDOC 中, 所述[步驟 3： 測試移轉應用程式](../../adapters-and-accelerators/adapter-sap/step-3-test-the-migrated-application2.md)。  
  
## <a name="see-also"></a>請參閱  
 [教學課程 3：移轉 SAP 傳送 IDOC BizTalk 專案](../../adapters-and-accelerators/adapter-sap/tutorial-3-migrating-an-sap-send-idoc-biztalk-project.md)