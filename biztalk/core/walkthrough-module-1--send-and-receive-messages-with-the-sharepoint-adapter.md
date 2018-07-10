---
title: 逐步解說： 模組 1-傳送和接收訊息，與 Windows SharePoint Services 配接器 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Windows SharePoint Services, creating sites
- tutorials, Windows SharePoint Services adapters
- Windows SharePoint Services adapter tutorials, receiving messages
- security, Windows SharePoint Services
- creating, Windows SharePoint Services site
- Windows SharePoint Services, security
- Windows SharePoint Services, document libraries
- Windows SharePoint Services adapters, security
- Windows SharePoint Services
- Windows SharePoint Services adapter tutorials, sending messages
ms.assetid: 6494aef5-bb1d-4a41-8186-1d49625a1013
caps.latest.revision: 41
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 320b64b75bb73e384e2a1af8281e5b578ecf0330
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36986431"
---
# <a name="walkthrough-module-1---sending-and-receiving-messages-with-the-windows-sharepoint-services-adapter"></a>逐步解說： 模組 1-傳送和接收訊息，Windows SharePoint Services 配接器
本逐步解說會示範如何設定 Windows SharePoint Services 和[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]讓您可以傳送和接收訊息，使用 Windows SharePoint Services 配接器和以內容為基礎的路由 (CBR)。 對於繫結至特定連接埠的訊息，以內容為基礎的路由可免除訊息訂閱之需求。 它也提供額外的彈性，讓使用者可傳遞以信封屬性為基礎的訊息，或僅以接收埠組態屬性為基礎的訊息。 如需 Windows SharePoint Services 配接器，請參閱[什麼是 Windows SharePoint Services 配接器？](../core/what-is-the-windows-sharepoint-services-adapter.md)。  
  
## <a name="prerequisites"></a>先決條件  
 下列是執行本主題所述程序的必要條件：  
  
- 您必須已完整安裝上執行的 BizTalk Server 的單一伺服器部署[!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)]或[!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)]。  
  
  在多重伺服器部署中使用的 Windows SharePoint Services 配接器的相關資訊，請參閱[設定和部署 Windows SharePoint Services 配接器](../core/setting-up-and-deploying-the-windows-sharepoint-services-adapter.md)。  
  
## <a name="configure-windows-sharepoint-services"></a>設定 Windows SharePoint Services  
 在此程序中，您會建立 1 個包含 3 個文件庫的 SharePoint 頂層網站。 Windows SharePoint Services 配接器使用這些文件庫，從來源程式庫將訊息移至目的地文件庫。 此訊息也會封存於文件庫。 必須執行本程序，才可讓 Windows Sharepoint Services 網站供這個逐步解說中的 Windows Sharepoint Services 配接器存取，以及設定啟用存取該網站的使用者權限。  
  
#### <a name="create-a-windows-sharepoint-services-site"></a>建立 Windows SharePoint Services 網站  
  
1. 按一下 **開始**，指向**所有程式**，指向**系統管理工具**，然後按一下  **SharePoint 管理中心。**  
  
2. 底下**虛擬伺服器組態**，按一下**建立最上層網站**。  
  
3. 底下**虛擬伺服器清單**，選取您在安裝 Windows SharePoint Services 配接器的網站。 例如， `Default Web Site`。  
  
4. 在 **網址**區段中**URL 名稱**欄位中，輸入`WSSAdapterWalkthrough`。  
  
5. 在 [**網站集合擁有者**區段中**使用者名稱] 欄位，** 輸入使用者名稱。 這位使用者就是網站擁有者，而不需要特殊權限[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。  
  
6. 在 **網站集合擁有者**區段中**電子郵件**欄位中，輸入電子郵件地址。  
  
7. 按一下 [確定] 。  
  
8. 在 **成功建立頂層網站**頁面上，按一下新頂層您剛才建立的 Web 站台。 例如， `http://<server_name>/sites/WSSAdapterWalkthrough`。  
  
9. 選取 **小組網站**範本，從清單中的範本，然後再按一下**確定**。 這樣會開啟「小組網站」首頁。  
  
#### <a name="create-a-source-document-library"></a>建立來源文件庫  
  
1.  在 小組網站首頁 」 的上方導覽列上，按一下 **建立**。  
  
2.  底下**文件庫**，按一下**文件庫**。  
  
3.  在 [**名稱和描述**區段中**名稱] 欄位中**類型`Source`。  
  
4.  在 [**瀏覽**區段中，選取**是**快速啟動] 列上顯示此表單程式庫。  
  
5.  在 **文件範本**區段中**文件範本**下拉式清單中，選取`None`。  
  
6.  按一下 **[建立]**。 會建立文件庫，然後將您重新導向至空白文件庫。  
  
#### <a name="create-a-destination-document-library"></a>建立目的地文件庫  
  
1.  在 小組網站首頁 」 的上方導覽列上，按一下 **建立**。  
  
2.  底下**文件庫**，按一下**文件庫**。  
  
3.  在 **名稱和描述**區段中**名稱欄位**，型別`Destination`。  
  
4.  在 [**瀏覽**區段中，選取**是**快速啟動] 列上顯示此表單程式庫。  
  
5.  在 **文件範本**區段中**文件範本**下拉式清單中，選取`None`。  
  
6.  按一下 **[建立]**。 會建立文件庫，然後將您重新導向至空白文件庫。  
  
#### <a name="create-an-archive-document-library"></a>建立封存文件庫  
  
1.  在 小組網站首頁 」 的上方導覽列上，按一下 **建立**。  
  
2.  底下**文件庫**，按一下**文件庫**。  
  
3.  在 [**名稱**和 [描述] 部分中，在**名稱] 欄位中**，型別`Archive`。  
  
4.  在 [**瀏覽**區段中，選取**是**快速啟動] 列上顯示此表單程式庫。  
  
5.  在 **文件範本**區段中**文件範本**下拉式清單中，選取`None`。  
  
6.  按一下 **[建立]**。 會建立文件庫，然後將您重新導向至空白文件庫。  
  
7.  關閉 `WSSAdapterWalkthrough` 網站。  
  
8.  關閉**SharePoint 管理中心**網站。  
  
#### <a name="configure-windows-security"></a>設定 Windows 安全性  
  
1.  按一下 **開始**，指向**所有程式**，指向**系統管理工具**，然後按一下**電腦管理**。  
  
2.  在主控台樹狀目錄中，依序展開**本機使用者和群組**，然後按一下**群組**。  
  
3.  以滑鼠右鍵按一下**SharePoint 啟用的主控件**群組中，按一下**新增到群組**，然後按一下**新增**。  
  
4.  在 **選取使用者、 電腦或群組 對話方塊中**下方**輸入物件名稱來選取**，輸入您設定 BizTalk Server 主控件執行個體，以執行，然後按一下 帳戶名稱**確定**。  
  
5.  在主控台樹狀目錄中，依序展開**服務和應用程式**，然後按一下**服務**。  
  
6.  以滑鼠右鍵按一下**BizTalk Service BizTalk Group: < Biztalk_host_name&gt >**，然後按一下**重新啟動**。  
  
    > [!NOTE]
    >  <BizTalk_Host_Name> 是主控件的名稱。 根據預設，此名稱為 `BizTalkServerApplication`。  
  
    > [!NOTE]
    >  在重新啟動服務的成員資格才會生效。  
  
7.  關閉**電腦管理**。  
  
#### <a name="configure-sharepoint-security"></a>設定 SharePoint 安全性  
  
1. 開啟 Web 瀏覽器，巡覽至您所建立的網站 URL。 例如， `http://<server_name>/sites/WSSAdapterWalkthrough`。  
  
2. 在 小組網站首頁 」 的上方導覽列上，按一下 **站台設定**。  
  
3. 底下**Administration**，按一下**管理使用者**。  
  
4. 按一下 **[加入使用者]**。  
  
5. 在 **步驟 1： 選擇使用者**，輸入帳戶的名稱，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]執行主控件執行個體。  
  
6. 在 **步驟 2： 選擇網站群組**，選取**讀取器**並**參與者**核取方塊。  
  
7. 按 [下一步] 。  
  
8. 清除**傳送下列電子郵件，讓這些使用者，現在他們已經被加入**核取方塊，然後按一下**完成**。  
  
9. 關閉 `WSSAdapterWalkthrough` 網站。  
  
## <a name="create-and-configure-the-biztalk-server-ports"></a>建立和設定 BizTalk Server 連接埠  
 您會在此程序建立和設定 Windows SharePoint Services 配接器的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 接收埠、接收位置以及傳送埠。 這些連接埠是 Windows Sharepoint Services 配接器接收和傳送文件的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 進出點。  
  
#### <a name="create-the-receive-port"></a>建立接收埠  
  
1. 按一下 **開始**，**所有程式**， [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理]。**  
  
2. 依序展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，依序展開**BizTalk 群組**，展開**應用程式**，依序展開**BizTalk Application 1**，以滑鼠右鍵按一下**接收埠**，按一下**新增**，然後按一下 **單向接收埠...**  
  
3. 在 **接收埠屬性**對話方塊的 **一般**，型別`FromSource`中**名稱**欄位。  
  
4. 按一下 [確定] 。  
  
#### <a name="create-the-receive-location"></a>建立接收位置  
  
1.  在**BizTalk 管理主控台**，以滑鼠右鍵按一下**接收位置**節點中，按一下 **新增**，然後按一下 **單向接收位置**.  
  
2.  在 [**選取接收埠**] 對話方塊中，選取`FromSource`，然後按一下 **[確定]**。  
  
3.  在 **接收位置屬性**對話方塊的 **一般**，型別`SourceLocation`中**名稱**欄位。  
  
4.  在 **傳輸**區段中**型別**下拉式清單中，選取`Windows``SharePoint``Services`。  
  
5.  按一下 **設定**來設定 Windows SharePoint Services 配接器屬性。  
  
6.  在 **配接器 Web 服務連接埠**屬性中，輸入已安裝 Windows SharePoint Services 配接器 Web 服務的虛擬伺服器的連接埠號碼。 預設號碼是連接埠 80。  
  
7.  型別`Archive`中**封存位置**屬性。  
  
8.  型別`10`中**輪詢間隔**屬性。  
  
9. 輸入您的 SharePoint 網站中的 URL **ShareP**sharepoint 網站 Url 屬性。 例如， `http://<server_name>/sites/WSSAdapterWalkthrough`。  
  
10. 型別`Source`for**來源文件庫**屬性。  
  
11. 按一下 [確定] 。  
  
12. 在 **接收位置屬性**對話方塊中，選取`BizTalkServerApplication`作為**接收處理常式**。  
  
13. 在 **接收管線**下拉式清單中，選取`PassThruReceive`。  
  
14. 按一下 [確定] 。  
  
#### <a name="create-the-send-port"></a>建立傳送埠  
  
1.  中**BizTalk 管理主控台**，以滑鼠右鍵按一下**傳送連接埠**節點，按一下 **新增**，然後按一下**靜態單向傳送埠**.  
  
2.  在 **傳送埠屬性**對話方塊的 **一般**，型別`SendToDestination`中**名稱**欄位。  
  
3.  在 **傳輸**區段中，選取`Windows SharePoint Services`類型。  
  
4.  按一下 **設定**來設定 Windows SharePoint Services 配接器屬性。  
  
5.  在 **配接器 Web 服務連接埠**屬性中，輸入已安裝 Windows SharePoint Services 配接器 Web 服務的虛擬伺服器的連接埠號碼。 預設號碼是連接埠 80。  
  
6.  在中輸入`Destination`for**目的地資料夾**屬性。  
  
7.  在中輸入`PurchaseOrder1-%MessageID%.xml`for **Filename**屬性。  
  
8.  設定**覆寫**屬性設`Yes`。  
  
9. 在您的 SharePoint 網站，在 URL 中的型別**SharePoint 網站 Url**屬性。 例如， `http://<server_name>/sites/WSSAdapterWalkthrough`。  
  
10. 設定**Microsoft Office 整合**屬性設`No`。  
  
11. 按一下 [確定] 。  
  
12. 在 [**傳送埠屬性] 對話方塊中**，請在**傳送處理常式**下拉式清單中，選取`BizTalkServerApplication`。  
  
13. 在 **傳送管線**下拉式清單中，選取`PassThruTransmit`。  
  
14. 按一下 [**篩選器**] 索引標籤。  
  
15. 選取 `WSS.InListName`中**屬性**欄位。  
  
16. 選取 `==`中**運算子**欄位。  
  
17. 型別`Source`中**值**欄位。  
  
18. 按一下 [確定] 。  
  
## <a name="enable-and-start-the-receive-location-and-receive-port"></a>啟用和啟動接收位置和接收埠  
 您可在這些程序啟用接收位置和啟動接收埠。 必須完成本程序，Windows Sharepoint Services 配接器才可透過指定的傳送埠和接收位置傳送和接收訊息。  
  
#### <a name="enable-the-receive-location"></a>啟用接收位置  
  
1.  在  **BizTalk 管理主控台**，按一下**接收位置**節點。  
  
2.  以滑鼠右鍵按一下`SourceLocation`，然後按一下**啟用**。  
  
#### <a name="start-the-send-port"></a>啟動傳送埠  
  
1.  在  **BizTalk 管理主控台**，按一下**傳送連接埠**節點。  
  
2.  以滑鼠右鍵按一下`SendToDestination`，然後按一下**啟動**。  
  
3.  關閉**BizTalk 管理主控台**。  
  
## <a name="sending-a-message-through-the-system"></a>透過系統傳送訊息  
 您會在此程序建立 XML 文件並上載至 Windows SharePoint Services 網站。 Windows SharePoint Services 配接器會取得該訊息、封存至「封存」文件庫，然後傳送至「目的地」文件庫。 此程序示範如何在文件從 Sharepoint 網站上，透過流動[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，以及 Sharepoint Services 網站使用的 Windows Sharepoint Services 配接器。  
  
#### <a name="create-a-working-directory"></a>建立工作目錄  
  
-   呼叫您的電腦上建立目錄**WSSAdapterWalkthrough**。 例如， `C:\WSSAdapterWalkthrough`。  
  
#### <a name="create-an-xml-file"></a>建立 XML 檔案  
  
1.  按一下 **開始**，指向**所有程式**，指向**附屬應用程式**，然後按一下  **記事本。**  
  
2.  輸入以下內容：  
  
    ```  
    <?xml version="1.0"?>  
    <PurchaseOrder>  
        <ID>1001</ID>  
        <FirstName>John</FirstName>  
        <LastName>Doe</LastName>  
        <Amount>750</Amount>  
    </PurchaseOrder>  
    ```  
  
3.  在工作目錄中，將檔案另存為 `PurchaseOrder1.xml`。 例如， `C:\WSSAdapterWalkthrough\PurchaseOrder1.xml`。  
  
#### <a name="upload-the-xml-file"></a>上載 XML 檔案  
  
1. 開啟網頁瀏覽器，然後移至您在上一個工作建立的網站之 URL。 例如， `http://<server_name>/sites/WSSAdapterWalkthrough`。  
  
2. 在左側，底下**文件**，按一下**來源**。  
  
3. 按一下 **上傳文件**。  
  
4. 在 **名稱**方塊中，輸入或瀏覽至 XML 檔案您在上面建立。 例如， `C:\WSSAdapterWalkthrough\PurchaseOrder1.xml`，然後按一下**儲存並關閉**。 您現在應該可以在清單中看到檔案。  
  
5. 重新整理瀏覽器視窗。 此文件庫將不會再列出 `PurchaseOrder1.xml` 檔案。  
  
   > [!NOTE]
   >  您可能需要重新整理瀏覽器幾次，因為輪詢間隔設定為 10 秒。  
  
6. 在上方導覽列中，按一下**文件，並列出**。  
  
7. 底下**文件庫**，按一下**目的地**。  
  
8. 在 [目的地] 文件庫中，您現在會看見已列出您的訊息。 您也可以在 [封存] 文件庫中找到封存的複本。  
  
   > [!NOTE]
   >  如果訊息不會出現在 [目的地] 文件庫中，請參閱 「 疑難排解 Windows SharePoint Services 配接器 」 中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助。  
  
## <a name="summary"></a>摘要  
 在本逐步解說中，您已看到如何設定 Windows SharePoint Services 和[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]讓您可以傳送和接收訊息，使用 Windows SharePoint Services 配接器和以內容為基礎的路由 (CBR)。  
  
## <a name="next-steps"></a>後續步驟  
 既然您已完成本逐步解說中，執行[逐步解說： 模組 2-整合 Office 與 Windows SharePoint Services 配接器](../core/walkthrough-module-2--integrate-office-with-the-sharepoint-adapter-in-biztalk.md)逐步解說，它會展開在您完成此逐步解說與顯示的工作您如何整合 Office 與 Windows SharePoint Services 配接器。  
  
## <a name="see-also"></a>另請參閱  
 [什麼是 Windows SharePoint Services 配接器？](../core/what-is-the-windows-sharepoint-services-adapter.md)   
 [Windows SharePoint Services 配接器逐步解說](../core/windows-sharepoint-services-adapter-walkthroughs.md)