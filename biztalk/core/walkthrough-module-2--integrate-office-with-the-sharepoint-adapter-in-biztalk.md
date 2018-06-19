---
title: 逐步解說： 模組 2-整合 Office 與 Windows SharePoint Services 配接器 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Windows SharePoint Services adapters, InfoPath forms
- InfoPath forms, creating
- InfoPath forms, Windows SharePoint Services adapters
- tutorials, Windows SharePoint Services adapters
- Windows SharePoint Services adapter tutorials, integrating Microsoft Office
- Windows SharePoint Services, document libraries
ms.assetid: 2f81a712-bb20-4c32-bbac-fb438deded38
caps.latest.revision: 48
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 64e23cef8b362accba726c60945548a3345c9c45
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22291454"
---
# <a name="walkthrough-module-2---integrating-office-with-the-windows-sharepoint-services-adapter"></a>逐步解說： 模組 2-整合 Office 與 Windows SharePoint Services 配接器
這個逐步解說是工作的接續[逐步解說： 模組 1-傳送和接收訊息，Windows SharePoint Services 配接器](../core/walkthrough-module-1--send-and-receive-messages-with-the-sharepoint-adapter.md)，並示範如何整合 Microsoft Office 與[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]以內容為基礎您所建立的路由 (CBR) 應用程式。 如需 Windows SharePoint Services 配接器的簡介，請參閱[什麼是 Windows SharePoint Services 配接器？](../core/what-is-the-windows-sharepoint-services-adapter.md)。  
  
## <a name="prerequisites"></a>必要條件  
 下列是執行本主題所述程序的必要條件：  
  
-   您必須擁有的完整安裝的單一伺服器部署[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。  
  
-   您必須完成下列逐步解說：[逐步解說： 模組 1-傳送和接收訊息，Windows SharePoint Services 配接器](../core/walkthrough-module-1--send-and-receive-messages-with-the-sharepoint-adapter.md)  
  
 在多重伺服器部署中使用 Windows SharePoint Services 配接器的相關資訊，請參閱[設定和部署 Windows SharePoint Services 配接器](../core/setting-up-and-deploying-the-windows-sharepoint-services-adapter.md)。  
  
## <a name="create-a-biztalk-project"></a>建立 BizTalk 專案  
 在此程序中，您要使用 [BizTalk 編輯器] 建立空白的 BizTalk 專案與結構描述。 必須執行這個程序，才能建立稍後要使用的 InfoPath 表單結構描述。  
  
#### <a name="create-a-strong-name-key-file"></a>建立強式名稱金鑰檔案  
  
1.  啟動**Visual Studio 命令提示字元**。  
  
2.  型別`sn -k C:\WSSAdapterWalkthrough\OrderProcess.snk`，然後按下**Enter**。 將會撰寫金鑰組。  
  
3.  關閉命令提示字元。  
  
#### <a name="create-an-empty-biztalk-project"></a>建立空白 BizTalk 專案  
  
1.  啟動**Microsoft Visual Studio**。  
  
2.  按一下**檔案**，**新增**，然後按一下 **專案**。  
  
3.  在下**專案類型**，選取**BizTalk 專案**。  
  
4.  在下**範本**，選取**空白 BizTalk Server 專案**。  
  
5.  型別`OrderProcess`中**名稱**欄位。  
  
6.  輸入您的工作目錄中的檔案路徑**位置**欄位。 例如， `C:\WSSAdapterWalkthrough\`。  
  
7.  按一下 **[確定]**。  
  
#### <a name="associate-the-key-file-with-the-assembly"></a>將金鑰檔案與組件建立關聯  
  
1.  在 [方案總管] 中，以滑鼠右鍵按一下`OrderProcess`專案，然後再按一下**屬性**為啟動專案設計工具。  
  
2.  按一下 [ **簽署** ] 索引標籤。  
  
3.  選取 **[簽署組件]** 選項、按一下 **[選擇強式名稱金鑰檔]** 選項的下拉式清單，然後按一下 **[瀏覽]**。  
  
4.  輸入 `C:\WSSAdapterWalkthrough\OrderProcess.snk`。  
  
5.  按一下 **[開啟]**。  
  
#### <a name="create-an-xsd-schema-by-using-the-biztalk-editor"></a>使用 [BizTalk 編輯器] 建立 XSD 結構描述  
  
1.  在 方案總管 中，以滑鼠右鍵按一下`OrderProcess`專案中，按一下 **新增**，然後按一下 **新項目**。  
  
2.  在下**類別**，按一下 **結構描述檔案**。  
  
3.  在下**範本**，按一下 **結構描述**。  
  
4.  型別`OrderProcessSchema`中**名稱**欄位，，然後按一下**新增**。  
  
5.  在 [屬性] 視窗中`OrderProcessSchema`，選取`Qualified`如**Element FormDefault**屬性。  
  
6.  在 [屬性] 視窗中`OrderProcessSchema`，型別`http://OrderProcess.PurchaseOrder`中**目標命名空間**欄位。  
  
7.  在**BizTalk 編輯器**，以滑鼠右鍵按一下`Root`，按一下 **重新命名**，然後輸入`PurchaseOrder`。  
  
8.  以滑鼠右鍵按一下**PurchaseOrder**節點中，按一下 **插入結構描述節點**，然後按一下 **子欄位項目**。  
  
9. 將它命名為 `PurchaseOrderID`。  
  
10. 建立另一個子欄位項目並命名為`BillTo`。  
  
11. 建立另一個子欄位項目並命名為`Amount`。  
  
12. 在 [屬性] 視窗中，設定**資料型別**屬性`Amount`為 xs: unsignedint。  
  
13. 建立另一個子欄位項目並命名為`PurchaseOrderDate`。  
  
14. 在 [屬性] 視窗中，設定**資料型別**屬性`PurchaseOrderDate`為 xs: datetime。  
  
15. 按一下**檔案**，然後按一下 **全部儲存**。  
  
16. 關閉 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]。  
  
## <a name="create-an-infopath-form"></a>建立 InfoPath 表單  
 在此程序中，您要根據在上一個程序所建立的結構描述，建立另一個文件庫與 InfoPath 表單。 此 InfoPath 表單會用來提交文件[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。  
  
> [!NOTE]
>  本逐步解說需要 Microsoft Office InfoPath 2007  
  
#### <a name="create-a-new-document-library"></a>建立新文件庫  
  
1.  開啟 Web 瀏覽器，巡覽至您所建立的網站 URL。 例如， `http://<server_name>/sites/WSSAdapterWalkthrough`。  
  
2.  在上方導覽列中，按一下 **建立**。  
  
3.  在下**文件庫**，按一下 **文件庫**。  
  
4.  在**名稱和描述**區段中，輸入`InfoPathSolutions`中**名稱 欄位**。  
  
5.  在**瀏覽**區段中，選取**是**快速啟動 列上顯示此表單庫。  
  
6.  在**文件範本**區段中，選取`None`如**文件範本**。  
  
7.  按一下 **[建立]**。 您將被重新導向至剛建立的空白文件庫。  
  
8.  在左側，按一下 **修改的設定和資料行**。  
  
9. 在下**資料行**，按一下 **加入新的資料行**。  
  
10. 在下**名稱和型別**，型別`Namespace`中**名稱**欄位。  
  
11. 按一下 **[確定]**。  
  
12. 關閉 `WSSAdapterWalkthrough` 網站。  
  
#### <a name="create-an-infopath-form-based-on-the-orderprocessschema-schema-file"></a>根據 OrderProcessSchema 結構描述檔案建立 InfoPath 表單  
  
1.  按一下**啟動**，指向 **所有程式**，指向  **Microsoft Office**，然後按一下  **Microsoft Office InfoPath 2007**。  
  
2.  在**填滿表單**對話方塊中，選取**設計的表單。**  
  
3.  在**設計表單**工作窗格中，選取**新 XML 文件或結構描述**。  
  
4.  在**資料來源精靈**，按一下 **瀏覽**並選取您在上一個程序中建立的結構描述檔案。 例如， `C:\WSSAdapterWalkthrough\OrderProcess\OrderProcess\OrderProcessSchema.xsd`。  
  
5.  按 **[下一步]**，再按一下 **[完成]**。  
  
6.  在**資料來源**工作窗格中，以滑鼠右鍵按一下**PurchaseOrder**節點，然後再按一下**含控制項的區段**。 將在範本上建立表單。  
  
7.  按一下**檔案**，按一下 **儲存**，然後按一下 **儲存**。  
  
8.  在**存** 對話方塊中，輸入`PurchaseOrder.xsn`中**檔案名稱**欄位，，然後按一下**儲存**。  
  
9. 按一下**檔案**，然後按一下 **發行**。  
  
10. 在**發佈精靈**，按一下 **下一步**。  
  
11. 選取**至 Web 伺服器**，然後按一下 **下一步**。  
  
12. 輸入的路徑和檔案名稱，以便您`InfoPathSolutions`文件庫，，然後按一下 **下一步**。 例如， `http://<server_name>/sites/WSSAdapterWalkthrough/InfoPathSolutions/PurchaseOrder.xsn`。  
  
13. 按一下**完成**，然後按一下 **關閉**。  
  
14. 關閉 Microsoft InfoPath。  
  
## <a name="modify-the-sharepoint-document-libraries"></a>修改 SharePoint 文件庫  
 在此程序中，您將更新 PurchaseOrder.xsn 檔案的命名空間屬性並修改 [目的地] 文件庫。 判斷以內容為基礎的路由實例所發佈之文件的訂閱者時，會使用此命名空間做為變數。  
  
#### <a name="update-the-namespace-for-purchaseorderxsn"></a>更新 PurchaseOrder.xsn 的命名空間  
  
1.  開啟 Web 瀏覽器，巡覽至您所建立的網站 URL。 例如， `http://<server_name>/sites/WSSAdapterWalkthrough`。  
  
2.  在左邊，底下**文件**，按一下  `InfoPathSolutions`。  
  
3.  將指標移`PurchaseOrder.xsn`，以滑鼠右鍵按一下，然後按**編輯內容**。  
  
4.  型別`http://OrderProcess.PurchaseOrder`中**命名空間**欄位，，然後按一下**儲存並關閉**。  
  
#### <a name="modify-the-destination-document-library"></a>修改 [目的地] 文件庫  
  
1.  在上方導覽列中，按一下 **文件，並列出**。  
  
2.  在下**文件庫**，按一下 **目的地**。  
  
3.  在左側，按一下 **修改的設定和資料行**。  
  
4.  在下**資料行**，按一下 **加入新資料行**。  
  
5.  在下**名稱和型別**，型別`Partner Name`中**資料行名稱**欄位。  
  
6.  按一下 **[確定]**。  
  
7.  關閉 `WSSAdapterWalkthrough` 網站。  
  
## <a name="modify-the-send-port-from-walkthrough-1"></a>修改源自逐步解說 1 的傳送埠  
 在此程序，您會修改源自逐步解說 1 的傳送埠。 此程序，才能確保這個逐步解說中所處理的文件會正確路由至傳送埠。  
  
#### <a name="modify-the-send-port"></a>修改傳送埠  
  
1.  開啟**BizTalk Server 管理。**  
  
2.  展開**Microsoft[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理**，依序展開**BizTalk 群組**，依序展開**應用程式**，依序展開**BizTalk Application 1**，然後按一下 **傳送埠**節點。  
  
3.  以滑鼠右鍵按一下`SendToDestination`，然後按一下 **屬性**。  
  
4.  在下**傳輸**，按一下 **設定**。  
  
5.  在**Filename**欄位中，輸入`PurchaseOrder2-%XPATH=//pons:PurchaseOrder/pons:PurchaseOrderID%.xml`。  
  
6.  在**命名空間別名**欄位中，輸入`pons="http://OrderProcess.PurchaseOrder"`。  
  
7.  在**範本文件庫**，型別`InfoPathSolutions`。  
  
8.  在**範本命名空間資料行**，型別`Namespace`。  
  
9. 選取`Yes`如**Microsoft Office 整合**屬性。  
  
10. 在下**Windows SharePoint Services 整合**，型別`Partner Name`中**資料行 01**欄位。  
  
11. 型別`%XPATH=//pons:PurchaseOrder/pons:BillTo%`中**資料行 01 值**欄位中，按一下**確定**，然後按一下  **確定**結束**傳送埠屬性**對話方塊。  
  
#### <a name="restart-the-send-port"></a>重新啟動傳送埠  
  
1.  在**BizTalk 管理主控台**，按一下 **傳送埠**節點。  
  
2.  以滑鼠右鍵按一下`SendToDestination`，然後按一下 **取消登錄**。  
  
3.  以滑鼠右鍵按一下`SendToDestination`，然後按一下 **啟動**。  
  
4.  關閉**BizTalk 管理主控台**。  
  
## <a name="send-a-message-through-the-system"></a>透過系統傳送訊息  
 在此程序中，您要建立 InfoPath 表單，並將它上載至 Windows SharePoint Services 網站。 Windows SharePoint Services 配接器會取得該訊息、封存至「封存」文件庫，然後傳送至「目的地」文件庫。 此程序示範如何在文件流經從 Sharepoint 網站， [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，以及 Sharepoint Services 網站使用 Windows Sharepoint Services 配接器。  
  
#### <a name="create-an-infopath-form-to-send-through-the-system"></a>建立 InfoPath 表單以透過系統傳送  
  
1.  開啟 Web 瀏覽器，巡覽至您所建立的網站 URL。 例如， `http://<server_name>/sites/WSSAdapterWalkthrough`。  
  
2.  在左邊，底下**文件**，按一下  `InfoPathSolutions`。  
  
3.  按一下`PurchaseOrder`檔案，以顯示**檔案下載**對話方塊，然後按一下**開啟**。 InfoPath 將載入此表單。  
  
4.  在**採購單識別碼**欄位中，輸入`1002`。  
  
5.  在**帳單寄送地**欄位中，輸入`John Doe`。  
  
6.  在**量**欄位中，輸入`750`。  
  
7.  在**訂單日期**欄位中，輸入`1/2/2005`。  
  
8.  按一下 **[儲存]**。  
  
9. 在**存** 對話方塊中，輸入`http://<server_name>/sites/WSSAdapterWalkthrough/Source`中**檔案名稱**欄位，然後按 enter 鍵。  
  
10. 型別`PurchaseOrder2.xml`中**檔案名稱**欄位，，然後按一下**儲存**。  
  
11. 關閉 Microsoft Office InfoPath。  
  
12. 在 Web 瀏覽器的上方導覽列上，按一下 **文件，並列出**。  
  
13. 在下**文件庫**，按一下 **目的地**。  
  
14. 在 [目的地] 文件庫中，您現在會看見已列出您的訊息。 您也可以在 [封存] 文件庫中找到封存的複本。  
  
15. 在 [目的地] 文件庫中，按一下 `PurchaseOrder1.xml`。 請注意，您可以在 [Microsoft Internet Explorer] 中開啟此 XML 檔案。  
  
16. 在 [目的地] 文件庫中，按一下 `PurchaseOrder2.xml`。 請注意，在 Microsoft Office InfoPath 開啟此 XML 檔案。  
  
> [!NOTE]
>  在 [目的地] 文件庫中，[檔案名稱] 資料行應該包含 [PurchaseOrderID] 欄位的值，而 [夥伴名稱] 資料行應該包含 [付款人] 欄位的值。  
  
## <a name="summary"></a>摘要  
 在此逐步解說中，您已經瞭解如何藉由使用 Windows SharePoint Services 配接器與以內容為基礎的路由 (CBR)，使 Microsoft InfoPath 更緊密整合。  
  
## <a name="next-steps"></a>後續步驟  
 現在您已完成此逐步解說中，執行[逐步解說： 模組 3-從協調流程存取 SharePoint 屬性](../core/walkthrough-module-3-accessing-sharepoint-properties-from-an-orchestration.md)整合，可在您完成這個逐步解說中，工作擴充逐步解說協調流程到專案中，並示範如何從其中存取 SharePoint 屬性內。  
  
## <a name="see-also"></a>另請參閱  
 [什麼是 Windows SharePoint Services 配接器？](../core/what-is-the-windows-sharepoint-services-adapter.md)   
 [Windows SharePoint Services 配接器逐步解說](../core/windows-sharepoint-services-adapter-walkthroughs.md)