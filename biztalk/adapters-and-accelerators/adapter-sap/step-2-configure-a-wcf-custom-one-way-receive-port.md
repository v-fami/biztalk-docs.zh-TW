---
title: 步驟 2： 設定 Wcf-custom 單向接收埠 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WCF-Custom one-way receive port, configuring
- migration
ms.assetid: e2a8f074-64d5-4e6c-84d0-318fb606c0ba
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6edf75f08bdf6a321188e484eb4f363366f8eb95
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22218550"
---
# <a name="step-2-configure-a-wcf-custom-one-way-receive-port"></a>步驟 2： 設定 Wcf-custom 單向接收埠
![步驟 3 之 2](../../adapters-and-accelerators/adapter-oracle-database/media/step-2of3.gif "Step_2of3")  
  
 **若要完成的時間：** 10 分鐘  
  
 **目標：** 在此步驟中，您可以設定 WCF 自訂連接埠來接收一般檔案 IDOC 從 SAP 系統。 設定連接埠之後, 您可以設定 BizTalk 應用程式使用 WCF 自訂接收埠。  
  
## <a name="prerequisites"></a>必要條件  
 您必須建立和部署 vPrev BizTalk 專案，以從 SAP 系統接收 Idoc。  
  
### <a name="to-configure-a-wcf-custom-one-way-receive-port"></a>若要設定 Wcf-custom 單向接收埠  
  
1.  啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。  
  
2.  在主控台樹狀目錄中，依序展開**BizTalk 群組**，然後展開**應用程式**。  
  
3.  展開您想要在其下建立接收埠的應用程式。  
  
4.  以滑鼠右鍵按一下**接收埠**，指向 **新增**，然後按一下**單向接收埠**。  
  
5.  在**接收埠屬性**對話方塊**一般**索引標籤上，輸入接收埠的名稱。  
  
6.  在**接收位置**索引標籤上，按一下 **新增**。 **接收位置屬性** 對話方塊隨即出現。  
  
7.  在**接收位置屬性**對話方塊方塊中，執行下列動作：  
  
    1.  指定接收位置的名稱。  
  
    2.  從**類型**下拉式清單中，選取**Wcf-custom**，然後按一下 **設定**。  
  
8.  在**Wcf-custom 傳輸屬性**對話方塊方塊中，執行下列動作：  
  
    1.  按一下**一般** 索引標籤，然後在**位址 (URI)** 欄位中，指定連線 URI 從 SAP 系統接收訊息。 連接至從 SAP 系統接收訊息的 URI 必須採用下列格式：  
  
        ```  
        sap://Client=800;lang=EN@A/YourSAPHOST/00?ListenerGwHost=YourSAPHOST&ListenerGwServ=SAPGW00&ListenerProgramId=MyProgramId  
        ```  
  
         下圖顯示具有指定之 URI 的連接埠的 [內容] 對話方塊：  
  
         ![連接至從 SAP 接收訊息的 URI](../../adapters-and-accelerators/adapter-sap/media/91e12582-aea3-4f13-8cdc-af69a9a11a5c.gif "91e12582-aea3-4f13-8cdc-af69a9a11a5c")  
  
         如需連線 URI 的詳細資訊，請參閱[建立連接至 SAP 系統](../../adapters-and-accelerators/adapter-sap/create-a-connection-to-the-sap-system.md)。  
  
    2.  按一下**繫結** 索引標籤，並從**繫結的型別**下拉式清單中，選取**sapBinding**。 請確定指定接收埠的下列繫結屬性。  
  
        |繫結屬性|若要設定的值|  
        |----------------------|------------------|  
        |FlatFileSegmentIndicator|**SegmentType**。 這表示一般的檔案應該包含在 IDOC 中的每個區段的區段類型。|  
        |padReceivedIdocWithSpaces|**True**。 指定 IDOC 中的每一行是否填補空格到正確的長度。|  
        |receiveIDocFormat|**字串**。 這會指定 IDOC 訊息應該以單一字串欄位。|  
  
         如需繫結屬性的詳細資訊，請參閱[了解 BizTalk Adapter for mySAP Business Suite 繫結屬性](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md)。  
  
    3.  按一下**其他**索引標籤，並指定要連接到 SAP 系統的認證。  
  
    4.  按一下**訊息** 索引標籤，然後在**輸入 BizTalk 訊息內文**區段中，選擇**路徑**選項。  
  
    5.  在**內文路徑運算式**文字方塊中，指定用於擷取 XML 訊息從一般檔案 IDOC 的 XPath 查詢。 如此一來，接收埠從 IDOC 擷取資料並修剪是一部分的 XML 標記**ReceiveIdoc** WCF 為基礎的作業[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。 如需有關的訊息結構描述**ReceiveIdoc**作業，請參閱[IDOC 作業的訊息結構描述](../../adapters-and-accelerators/adapter-sap/message-schemas-for-idoc-operations.md)。  
  
         ![XPath 查詢來擷取一般 &#45; 檔案 IDOC](../../adapters-and-accelerators/adapter-sap/media/8b5b8165-a1e7-40ef-bcf7-de3149c6deb0.gif "8b5b8165-a1e7-40ef-bcf7-de3149c6deb0")  
  
         您必須指定下列 XPath 查詢：  
  
        ```  
        /*[local-name()='ReceiveIdoc']/*[local-name()='idocData']  
        ```  
  
    6.  從**節點編碼**下拉式清單中，選取**字串**。  
  
    7.  按一下**套用**，然後按一下 **確定**。  
  
9. 在 [接收位置屬性] 對話方塊從**接收處理常式**下拉式清單中，選取**BizTalkServerApplication**。  
  
10. 從**接收管線**下拉式清單中，選取**ConvertToXML**。 這個一般檔案解譯器管線已轉換成 XML IDOC 一般檔案 IDOC vPrev BizTalk 專案的一部分。  
  
11. 按一下 **[確定]**。  
  
### <a name="to-configure-the-biztalk-application"></a>若要設定 BizTalk 應用程式  
  
1.  在 BizTalk Server 管理主控台中，展開  **BizTalk 群組**，依序展開**應用程式**、 展開協調流程部署所在的 BizTalk 應用程式。  
  
2.  以滑鼠右鍵按一下 BizTalk 應用程式，然後選取**設定**。  
  
3.  從左窗格中，按一下 協調流程設定。 從右窗格中，從**主機**下拉式清單中，選取 BizTalk 主控件執行個體。  
  
4.  在下**繫結**方塊中，將 BizTalk 協調流程的邏輯連接埠對應到 BizTalk Server 管理主控台中的實體連接埠。  
  
    1.  選取 WCF 自訂接收您稍早在本主題中所建立的連接埠。  
  
    2.  選取您將在何處接收一般檔案 IDOC 的 file 連接埠。  
  
    3.  按一下 **[確定]**。  
  
     如需有關如何設定應用程式的詳細資訊，請參閱[http://go.microsoft.com/fwlink/?LinkId=102360](http://go.microsoft.com/fwlink/?LinkId=102360)。  
  
## <a name="next-steps"></a>後續步驟  
 您現在已完成移轉至 BizTalk 專案，從使用 WCF 為基礎的 SAP 系統接收 Idoc vPrev BizTalk 專案的[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。 您必須現在測試已移轉的 BizTalk 應用程式接收一般檔案 IDOC，方式中所述[步驟 3： 測試移轉應用程式](../../adapters-and-accelerators/adapter-sap/step-3-test-the-migrated-application5.md)。  
  
## <a name="see-also"></a>另請參閱  
 [教學課程 4： 移轉 SAP 接收 IDOC 的 BizTalk 專案](../../adapters-and-accelerators/adapter-sap/tutorial-4-migrating-an-sap-receive-idoc-biztalk-project.md)