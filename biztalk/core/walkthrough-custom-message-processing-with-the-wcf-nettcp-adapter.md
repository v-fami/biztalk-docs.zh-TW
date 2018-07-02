---
title: 逐步解說： 使用自訂訊息處理 Wcf-nettcp 配接器 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b56b7492-2ea0-4c63-8f1b-430eb277517d
caps.latest.revision: 32
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d8b74c2ead4ece353dae155d272a9a1aee5fb676
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37006207"
---
# <a name="walkthrough-custom-message-processing-with-the-wcf-nettcp-adapter"></a>逐步解說： 使用自訂訊息處理 Wcf-nettcp 配接器
在本逐步解說[!INCLUDE[firstref_btsWinCommFoundation](../includes/firstref-btswincommfoundation-md.md)]用戶端提交[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]訊息，其中包含內嵌二進位 JPEG 影像資料的 BizTalk 接收位置使用 Wcf-nettcp 配接器。 透過使用 XPath 陳述式 （具有編碼的 Base64 節點） 中擷取二進位編碼的 JPEG 影像，取得**輸入訊息內文**中配接器的組態設定。 XPath 處理不同的預設方法，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]用以處理內送訊息。 在預設方法中，配接器取得的整個內容**主體**項目[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]訊息，然後再將它提交至 BizTalk MessageBox 資料庫。 處理擷取收到的特定部分的 XPath 訊息[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]來建立自訂的 BizTalk 訊息的訊息。 在此範例中 XPath 處理會尋找名為 XML 項目**SendPicture**在傳入[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]訊息 （這是以 XML 格式）。 找到該項目之後, XPath 擷取的項目值定義為二進位 Base64 編碼物件，並將該二進位值放入 BizTalk 訊息。 訊息會發佈到 MessageBox 資料庫，然後輸出至檔案傳送埠的傳送埠篩選訂用帳戶的協助。 沒有協調流程會在此範例中，以及所有處理都都透過 BizTalk 訊息使用 XPath。  

 A[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]配接器用來與通訊[!INCLUDE[firstref_btsWinCommFoundation](../includes/firstref-btswincommfoundation-md.md)]用戶端並[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]遠端服務從[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。  它可讓協調流程和結構描述發佈為[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]服務，而且也提供 協調流程，以使用外部 WCF 服務的能力。 Wcf-nettcp 配接器會使用**NetTcpBinding**繫結，這表示使用最佳化的二進位訊息編碼的 TCP 傳輸。 Wcf-nettcp 配接器是由傳送配接器和接收配接器所組成。 該配接器可完整存取 SOAP 安全性、可靠性和交易功能。  

 完成此逐步解說之後，您將會瞭解如何執行下列工作：  

- 使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台匯入 MSI 檔案，以建立傳送埠、接受埠和接收位置。  

- 藉由使用[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，設定[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]接收位置，才能執行要從中擷取資料的 XPath 陳述式**SendPicture**項目[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]訊息。  

> [!NOTE]
>  **Hosttrusted**項目會指定與接收處理常式關聯的主控件是否受到信任。 在 bindings.xml 檔案中，它會設定為其預設值`false`因為在此範例中我們不在意[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]企業單一登入服務 」 (SSO)。 SSO 可讓使用者認證，透過傳遞[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]整合第三方應用程式與[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。 A`false`設定可防止 BizTalk 訊息通過 BizTalk 服務，做為 SSO 的處理程序的一部分。  

## <a name="prerequisites"></a>必要條件  
 執行此範例中的步驟會確保您的環境會安裝下列必要條件;  

- 建置組件，並執行部署程序，在電腦和執行此範例中，電腦需要 Microsoft [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)]，Microsoft [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)]，與 Microsoft BizTalk Server。  

- 用來建置組件，並執行部署程序的電腦需要 Microsoft Visual Studio。  

- 執行範例的電腦需要[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]配接器和[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]管理工具。 這些是 Microsoft BizTalk Server 的安裝期間安裝的選項。  

- 在電腦上您用來執行系統管理工作，您必須以成員的使用者帳戶執行[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]若要設定的系統管理員群組[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]內的應用程式設定[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台。 此使用者帳戶也必須管理主控件執行個體，以及可能需要其他工作的應用程式部署的本機系統管理員群組成員。  

- 需要的任何電腦上[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]功能，完成單次安裝程序，如[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]在範例[ http://go.microsoft.com/fwlink/?LinkId=135510 ](http://go.microsoft.com/fwlink/?LinkId=135510)。  

- 執行範例，並匯入到.msi 檔案的電腦上[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，請確定主機不受信任的主機，或匯入將會失敗。  

- 您必須下載逐步解說程式碼，並將它解壓縮到您的電腦。  本逐步解說屬於整個[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]配接器逐步解說 」 套件。 您可以下載檔案**WCFAdapterWalkthroughs.exe**從[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]開發人員中心， [ http://go.microsoft.com/fwlink/?LinkId=194140 ](http://go.microsoft.com/fwlink/?LinkId=194140)。  

### <a name="configure-the-wcfcustommessageprocessing-application-and-artifacts"></a>設定 WCFCustomMessageProcessing 應用程式和成品  

1. 在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下**應用程式**，選取**匯入**，然後選取**MSI 檔案**。 移至**C:\WCFCustomMessageProcessing\WCFCustomMessageProcessing.msi**檔案，然後再按一下**開啟**。 這會建立此應用程式的下列成品：  

   - **FileSP**傳送埠： 本機檔案系統上的位置**C:\WCFCustomMessageProcessing\Out** JPEG 影像資料由其中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]做為最終輸出的範例處理程序。 您可以檢視傳送埠篩選條件的**BTS。RecievePortName = NetTcpRP**中設定**FileSP 屬性** 下的對話方塊**篩選**。 相關聯的篩選器，是使用 NetTcp 接收埠。 接收埠將會傳送至 FileSP NetTcpRP 上接受任何訊息傳送連接埠的輸出位置**C:\WCFCustomMessageProcessing\Out**接收位置執行 XPath 處理訊息之後。  

   - **NetTcpRP**接收埠： 邏輯上包含的連接埠**NetTcpRL**接收位置。  

   - **NetTcpRL**接收位置： 這會使用預設值**PassThroughTransmit**管線和 Wcf-nettcp 配接器執行的 XPath 陳述式，以提取 JPEG 影像從內送的資料[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]訊息。  

### <a name="alternative-steps-to-configure-the-wcfcustommessageprocessing-application"></a>若要設定 WCFCustomMessageProcessing 應用程式的替代步驟  

- 或者，以下是設定應用程式，而不使用的手動步驟**C:\WCFCustomMessageProcessing\bindings.xml**檔案。 您不需要這樣做，如果先前的繫結檔案匯入程序能正常運作。  但是，您也可以讀取它，可能會增加您對現況的 MSI 檔案。  

- 建立單向接收埠 (**NetTcpRP**) 和接收位置 (**NetTcpRL**)。  

  1. 依序展開**WCFCustomMessageProcessing**應用程式，以滑鼠右鍵按一下**接收埠**，選取**新增**，然後選取**單向接收埠**. 在**接收埠屬性**對話方塊方塊中，輸入`NetTcpRP`如**名稱**，然後按一下 **[確定]**。  

  2. 以滑鼠右鍵按一下**NetTcpRP**接收埠中，選取**新增**，然後選取**接收位置**。 在 **接收位置屬性**對話方塊方塊中，輸入`NetTcRL`如**名稱**。 在 **傳輸**區段中，按一下**型別**下拉式清單方塊中，選取**Wcf-nettcp**從下拉式清單中，然後按一下 **設定**.  

  3. 在 **一般**索引標籤上，輸入**net.tcp://localhost/NetTcpRL/Image**中**Address(URI)** 欄位。  

  4. 在上**安全性**索引標籤上，設定**安全性模式**到**None。**  

  5. 在上**訊息**索引標籤上，選取**路徑**選項**輸入 BizTalk 訊息內文**，然後輸入`/*[local-name()="SendPicture" and namespace-uri()='http://tempuri.org/']/*[local-name()="stream"]`內文路徑運算式。 選取  **Base64**作為**節點編碼**。 **路徑**選項設定為值，因為主體[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]訊息，各[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]接收採用下列格式：  **\<SendPicture xmlns ="http://tempuri.org/"\>\<串流\>*實際的 base 64 編碼的二進位影像資料*\</串流\>\</SendPicture\>**  

  6. 在 [**接收位置屬性**] 對話方塊中，按一下**確定**。  

- 建立單向 file 傳送埠 (FileSP) NetTcpRP 訂閱接收埠。  

  1.  以滑鼠右鍵按一下**傳送埠**，選取**新增**，然後選取**單向接收埠**。 選取 **靜態單向連接埠**。 請輸入`FileSP`for**名稱**。  

  2.  在 **傳輸**區段中，按一下**型別**下拉式清單方塊中，選取**檔案**從下拉式清單中，然後按一下**設定**。  

  3.  底下**目的地資料夾**輸入`C:\WCFCustomMessageProcessing\Out`，然後按一下**確定**。  

  4.  按一下 **篩選條件**，選取`BTS.ReceivePortName == NetTcpRP`，然後按一下  **確定。**  

### <a name="configure-the-send-port-and-run-the-application"></a>設定傳送埠和執行應用程式  

1. 以滑鼠右鍵按一下**WCFCustomMessageProcessing**應用程式，然後選取**開始**。 會登錄 NetTcpRL 接收位置，然後啟動 FileSP 傳送埠。  

2. 在  [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]，接著請開啟`Client.sln`檔案**C:WCFCustomMessageProcessing\Client**資料夾。 在 [方案總管] 中，以滑鼠右鍵按一下**用戶端**專案，然後選取**建置**。  

3. 在  [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]，選取**偵錯**，然後選取**啟動但不偵錯**執行 Client.exe 應用程式。 命令提示字元會顯示指出映像已提交給[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。  

4. 觀察成功 {GUID}.jpg 檔案輸出至傳送連接埠檔案資料夾**C:\WCFCustomMessageProcessing\Out**。這會顯示所擷取的 JPEG 檔案，並寫入其出寫入檔案，傳送埠已順利完成的應用程式處理。
