---
title: 逐步解說： 部署的原則 |Microsoft 文件
ms.custom: ''
ms.date: 2016-04-05
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 205760e2-9cd4-496f-93cd-0f93bc5d3231
caps.latest.revision: 25
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0d235fa0f6882ecd9e180aabd26999b1d7f73390
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25975908"
---
# <a name="walkthrough-deploying-the-policy"></a>逐步解說： 部署原則
本逐步解說提供逐步指示部署**ProcessPurchaseOrder**原則中的下列三種方式：  
  
-   使用商務規則引擎部署精靈，匯出和匯入原則。  
  
-   使用 BizTalk Server 管理主控台，匯出原則至 XML 檔案，以及從 XML 檔案匯入原則。  
  
-   使用 BizTalk Server 管理主控台，將原則匯出為 MSI 檔案的一部分，以及匯入 MSI 檔案。  
  
## <a name="prerequisites"></a>必要條件  
 您必須先完成[逐步解說： 追蹤原則執行](../core/walkthrough-tracking-policy-execution.md)逐步解說，然後再執行本逐步解說。  
  
## <a name="overview-of-this-walkthrough"></a>此逐步解說的概觀  
 本主題包含下列三個逐步解說：  
  
1.  第一個逐步解說包含部署程序**ProcessPurchaseOrder**原則使用商務規則引擎部署精靈。 下表描述此逐步解說中的程序。  
  
    |程序標題|程序說明|  
    |---------------------|---------------------------|  
    |使用商務規則引擎部署精靈匯出 POVocabulary 1.0 和 1.1|提供逐步指示，匯出 1.0 和 1.1 版**POVocabulary**詞彙至 XML 檔案使用商務規則引擎部署精靈。|  
    |若要使用商務規則引擎部署精靈匯出 ProcessPurchaseOrder 1.3|提供逐步指示，匯出 1.3 版**ProcessPurchaseOrder**原則至 XML 檔案使用商務規則引擎部署精靈。|  
    |若要刪除 ProcessPurchaseOrder 和 POVocabulary|提供逐步指示，刪除**ProcessPurchaseOrder**原則和**POVocabulary**詞彙，以便您可以測試匯入 XML 檔案來重新建立它們。|  
    |若要從 XML 匯入以重新建立 POVocabulary 1.0 和 1.1|提供逐步指示，匯入的詞彙 XML 檔案來重新建立第一個程序所建立**POVocabulary**詞彙。|  
    |若要確認 POVocabulary 1.0 和 1.1 已重新建立|提供逐步指示，使用 「 商務規則編輯器 」 來驗證該 1.0 和 1.1 版**POVocabulary**重新建立。|  
    |若要從 XML 匯入以重新建立 ProcessPurchaseOrder 1.3|提供逐步指示，匯入原則 XML 檔來重新建立 1.3 版的第二個程序所建立**ProcessPurchaseOrder**原則。|  
    |若要確認 ProcessPurchaseOrder 1.3 已重新建立|提供逐步指示，使用 「 商務規則編輯器 」 以確認 1.3 版的**ProcessPurchaseOrder**原則都會重新建立。|  
  
2.  第二個逐步解說包含部署程序**ProcessPurchaseOrder**使用 XML 檔案的原則匯出從 BizTalk Server 管理主控台下表描述在此程序逐步解說。  
  
    |程序標題|程序說明|  
    |---------------------|---------------------------|  
    |若要匯出 ProcessPurchaseOrder 1.3 原則和 POVocabulary 詞彙至 XML 檔案|提供逐步指示，請使用 BizTalk Server 管理主控台匯出**ProcessPurchaseOrder**原則和**POVocabulary**詞彙至 XML 檔案。|  
    |若要刪除 ProcessPurchaseOrder 原則|提供逐步指示，刪除**ProcessPurchaseOrder**原則**RuleTestApp**和 「 規則引擎 」 資料庫。|  
    |若要匯入 XML 檔案以重新建立 ProcessPurchaseOrder 原則|提供逐步指示，匯入 XML 檔案中重新建立的第一個程序匯出**ProcessPurchaseOrder**原則。|  
    |若要新增 ProcessPurchaseOrder 原則至 RuleTestApp 應用程式|提供逐步指示，加入**ProcessPurchaseOrder**原則**RuleTestApp**應用程式。|  
  
3.  第三個逐步解說包含部署程序**ProcessPurchaseOrder**從 BizTalk Server 管理主控台匯出的原則使用 MSI 檔案。 下表描述此逐步解說中的程序。  
  
    |程序標題|程序的相關逐步指示|  
    |---------------------|---------------------------------------------------|  
    |若要匯出 RuleTestApp 應用程式至 MSI 檔案|提供逐步指示，匯出**RuleTestApp**應用程式至 MSI 檔案，以便稍後用來重新建立應用程式。|  
    |若要刪除 RuleTestApp 應用程式|提供逐步指示，刪除**RuleTestApp**應用程式，以便您可以測試使用 MSI 檔案重建應用程式。|  
    |若要確認 ProcessPurchaseOrder 原則和 POVocabulary 詞彙已刪除|提供逐步指示，使用 「 商務規則編輯器 」 可讓您確認**ProcessPurchaseOrder**原則和 POVocabulary 詞彙已刪除。|  
    |若要匯入 MSI 檔案以重新建立 RuleTestApp 應用程式|提供使用 BizTalk Server 管理主控台匯入 MSI 檔案的逐步指示來重新建立**RuleTestApp**應用程式。|  
    |若要確認 ProcessPurchaseOrder 原則已新增至 RuleTestApp|提供逐步指示，使用 BizTalk Server 管理主控台，確認**ProcessPurchaseOrder**原則新增至**RuleTestApp**應用程式。|  
    |若要確認 ProcessPurchaseOrder 原則和 POVocabulary 詞彙已重新建立|提供逐步指示，使用 「 商務規則編輯器 」 可讓您確認**ProcessPurchaseOrder**原則和**POVocabulary**詞彙時都會重新建立。|  
    |測試方案|提供測試方案的逐步指示。|  
  
## <a name="procedures-for-deploying-the-processpurchaseorder-policy-by-using-the-business-rules-engine-deployment-wizard"></a>使用商務規則引擎部署精靈部署 ProcessPurchaseOrder 原則的程序  
  
#### <a name="to-export-povocabulary-10-and-11-by-using-the-business-rules-engine-deployment-wizard"></a>使用商務規則引擎部署精靈匯出 POVocabulary 1.0 和 1.1  
  
1.  在**啟動**功能表中，開啟**商務規則引擎部署精靈**。  
  
    > [!NOTE]
    >  在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。 若要這樣做，應用程式，以滑鼠右鍵按一下，然後選取**系統管理員身分執行**。  
  
2.  按一下 **[下一步]**。  
  
3.  在**部署工作**頁面上，選取**匯出原則/詞彙至檔案從資料庫**，然後按一下 **下一步**。  
  
4.  在**原則存放區**頁面上，按一下**下一步**。  
  
5.  在**匯出原則/詞彙**頁面上，按一下**詞彙**。  
  
6.  選取**POVocabulary.1.0**從下拉式清單中，為**原則/詞彙**中，輸入或瀏覽以指定 XML 輸出檔名稱做為**C:\BRE-walkthroughs\POVocabulary10.xml**，然後按一下 **下一步**。  
  
7.  在**準備**頁面上，按一下**下一步**。  
  
8.  在**匯出原則/詞彙**頁面上，按一下**下一步。**  
  
9. 選取**再次執行此精靈**，然後按一下 **完成**。  
  
     因為您選取**再次執行此精靈**，精靈的第一個畫面會再次出現。  
  
10. 重複步驟 2 至 6。  
  
11. 選取**POVocabulary.1.1**從下拉式清單中，為**原則/詞彙**中，輸入或瀏覽以指定 XML 輸出檔名稱做為**C:\BRE-walkthroughs\POVocabulary11.xml**，然後按一下 **下一步**。  
  
12. 重複步驟 8 和 9。  
  
13. 按一下 **[完成]**。  
  
    > [!NOTE]
    >  您需要匯出 1.0 和 1.1 版**POVocabulary**因為**ProcessPurchaseOrder** 1.3 相依於這兩個版本**POVocabulary**。 **允許的項目數目上限**從 1.1 版詞彙使用定義。 **要求數量**和**Request Status**定義所使用的 1.0 版。  
  
#### <a name="to-export-processpurchaseorder-13-by-using-the-business-rule-engine-deployment-wizard"></a>若要使用商務規則引擎部署精靈匯出 ProcessPurchaseOrder 1.3  
  
1.  在**啟動**功能表中，開啟**商務規則引擎部署精靈**。  
  
    > [!NOTE]
    >  在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。 若要這樣做，應用程式，以滑鼠右鍵按一下，然後選取**系統管理員身分執行**。  
  
2.  在**歡迎使用規則引擎部署精靈**頁面上，按一下**下一步**。  
  
3.  選取**匯出原則/詞彙至檔案從資料庫**，然後按一下 **下一步**。  
  
4.  在**原則存放區**頁面上，按一下**下一步**。  
  
5.  確認**原則**選取選項。  
  
6.  選取**ProcessPurchaseOrder.1.3**從下拉式清單中，為**原則/詞彙**。  
  
7.  輸入或瀏覽以指定**C:\BRE-walkthroughs\ProcessPOPolicy13.xml**做為 XML 輸出檔案名稱。  
  
8.  按一下**下一步**三次，然後按一下 **完成**。  
  
#### <a name="to-delete-processpurchaseorder-and-povocabulary"></a>若要刪除 ProcessPurchaseOrder 和 POVocabulary  
  
1.  在**啟動**功能表中，開啟**商務規則編輯器 」**。 如果您有商務規則編輯器已開啟，請按 F5 或按一下**重新載入**上**檔案**重新整理的功能表。  
  
    > [!NOTE]
    >  在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。 若要這樣做，應用程式，以滑鼠右鍵按一下，然後選取**系統管理員身分執行**。  
  
2.  在 原則總管 視窗中，依序展開**原則**，依序展開**ProcessPurchaseOrder**，以滑鼠右鍵按一下**1.0 版**，然後按一下 **刪除**. 如果**刪除**是停用，以滑鼠右鍵按一下**1.0 版**，然後按一下 **解除部署**。  
  
    > [!NOTE]
    >  已部署的原則版本無法加以刪除。 您必須先解除原則的部署，才能刪除原則版本。  
  
3.  按一下**是**確認訊息方塊中。  
  
4.  重複步驟 2 和 3 以刪除**1.1 版**。  
  
5.  重複步驟 2 和 3 以刪除**1.2 版**。  
  
6.  以滑鼠右鍵按一下**1.3 版-部署**，然後按一下 **解除部署**。 如果**解除部署**選項已停用、 略過此步驟。  
  
7.  在 事實總管 視窗中，依序展開**詞彙**，以滑鼠右鍵按一下**POVocabulary**，然後按一下 **刪除**。  
  
#### <a name="to-import-from-xml-to-re-create-povocabulary-10-and-11"></a>若要從 XML 匯入以重新建立 POVocabulary 1.0 和 1.1  
  
1.  在**啟動**功能表中，開啟**商務規則引擎部署精靈**。  
  
    > [!NOTE]
    >  在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。 若要這樣做，應用程式，以滑鼠右鍵按一下，然後選取**系統管理員身分執行**。  
  
2.  在**歡迎使用規則引擎部署精靈**，按一下 **下一步**。  
  
3.  在**部署工作**頁面上，選取**匯入並發佈原則/詞彙至資料庫，從檔案**，然後按一下 **下一步**。  
  
4.  在**原則存放區**頁面上，按一下**下一步**。  
  
5.  瀏覽並選取**POVocabulary10.xml**您在第一個程序中建立的檔案。  
  
6.  按一下**開啟**或按兩下**POVocabulary10.xml**。  
  
7.  按一下**下一步**商務規則引擎部署精靈 」 中。  
  
8.  按一下 **[下一步]**。  
  
9. 按一下 **[下一步]**。  
  
10. 選取**再次執行此精靈**，然後按一下 **完成**。  
  
11. 重複步驟 2 至 9 以匯入**POVocabulary11.xml**。  
  
12. 按一下 **[完成]**。  
  
#### <a name="to-verify-that-povocabulary-10-and-11-are-re-created"></a>若要確認 POVocabulary 1.0 和 1.1 已重新建立  
  
1.  在**啟動**功能表中，開啟**商務規則編輯器 」**。 如果您有已經開啟它，請按 F5 或按一下**重新載入**上**檔案**重新整理的功能表。  
  
    > [!NOTE]
    >  在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。 若要這樣做，應用程式，以滑鼠右鍵按一下，然後選取**系統管理員身分執行**。  
  
2.  在 事實總管 視窗中，按一下**詞彙** 索引標籤。  
  
3.  展開**詞彙**，而且您應該會看到**POVocabulary**。  
  
4.  展開**POVocabulary**，而且您應該會看到**1.0 版**和**1.1 版**。  
  
#### <a name="to-import-from-xml-to-re-create-processpurchaseorder-13"></a>若要從 XML 匯入以重新建立 ProcessPurchaseOrder 1.3  
  
1.  在**啟動**功能表中，開啟**商務規則引擎部署精靈**。  
  
    > [!NOTE]
    >  在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。 若要這樣做，應用程式，以滑鼠右鍵按一下，然後選取**系統管理員身分執行**。  
  
2.  在**歡迎使用規則引擎部署精靈**，按一下 **下一步**。  
  
3.  在**部署工作**頁面上，選取**匯入並發佈原則/詞彙至資料庫，從檔案的 fileto 資料庫**，然後按一下 **下一步**。  
  
4.  在**原則存放區**頁面上，按一下**下一步**。  
  
5.  瀏覽並選取**ProcessPOPolicy13.xml**您稍早在本逐步解說中建立的檔案。  
  
6.  按一下**開啟**或按兩下**ProcessPOPolicy13.xml**。  
  
7.  按一下**下一步**商務規則引擎部署精靈 」 中。  
  
8.  按一下 **[下一步]**。  
  
9. 按 **[下一步]**，再按一下 **[完成]**。  
  
#### <a name="to-verify-that-processpurchaseorder-13-is-re-created"></a>若要確認 ProcessPurchaseOrder 1.3 已重新建立  
  
1.  在**啟動**功能表中，開啟**商務規則編輯器 」**。 如果您有已經開啟它，請按 F5 或按一下**重新載入**上**檔案**重新整理的功能表。  
  
    > [!NOTE]
    >  在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。 若要這樣做，應用程式，以滑鼠右鍵按一下，然後選取**系統管理員身分執行**。  
  
2.  在 [原則總管] 視窗中，依序展開**原則**和您應該會看到**ProcessPurchaseOrder**。  
  
3.  展開**ProcessPurchaseOrder**和您應該會看到**1.3 版-已發佈**。  
  
## <a name="procedures-for-deploying-the-policy-by-using-an-xml-file-exported-from-the-biztalk-server-administration-console"></a>使用由 BizTalk Server 管理主控台匯出的 XML 檔案以部署原則的程序  
  
#### <a name="to-export-the-processpurchaseorder-13-policy-and-the-povocabulary-vocabulary-to-an-xml-file"></a>若要匯出 ProcessPurchaseOrder 1.3 原則和 POVocabulary 詞彙至 XML 檔案  
  
1.  在**啟動**功能表中，開啟[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]。 如果您已經開啟此工具，請按 F5 重新整理。  
  
2.  展開**主控台根目錄**，依序展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，依序展開**BizTalk 群組**，依序展開**應用程式**，然後展開**RuleTestApp**.  
  
3.  按一下**原則**，並確定您看到 ProcessPurchaseOrder 1.3 原則清單中的。  
  
4.  以滑鼠右鍵按一下**ProcessPurchaseOrder**，然後按一下 **匯出**。  
  
5.  在**匯出原則**對話方塊方塊中，請確定**ProcessPurchaseOrder**原則和**POVocabulary**已選取。  
  
    > [!NOTE]
    >  您可以匯出至 XML 檔案的應用程式中的所有原則，以滑鼠右鍵按一下**RuleTest** ，然後按一下 **都匯出**上**原則**功能表。 這樣就可以將此應用程式使用的所有原則和詞彙匯出至單一 XML 檔案。  
  
    > [!NOTE]
    >  您可以匯出至 XML 檔案的所有應用程式中的所有原則，以滑鼠右鍵按一下**應用程式**節點，然後按一下**都匯出**上**原則**功能表。 這樣就可以將所有應用程式使用的所有原則和詞彙匯出至單一 XML 檔案。  
  
6.  指定輸出 XML 檔案名稱 (**C:\BRE-Walkthroughs\ProcessPOFromAdmin.xml**)，然後按一下 **確定**。  
  
#### <a name="to-delete-the-processpurchaseorder-policy"></a>若要刪除 ProcessPurchaseOrder 原則  
  
1.  在 BizTalk Server 管理，以滑鼠右鍵按一下**ProcessPurchaseOrder**在清單中，然後按一下**移除**。  
  
2.  按一下**是**中**移除原則**訊息方塊。  
  
    > [!NOTE]
    >  如果原則處於已部署狀態，您無法將它移除。 以滑鼠右鍵按一下**ProcessPurchaseOrder**，然後按一下 **解除部署**解除部署原則。 **移除**解除部署原則時，目前使用功能表項目。  
  
    > [!NOTE]
    >  詞彙**ProcessPurchaseOrder**原則而定，在此情況下**POVocabulary**，也會一併刪除。  
  
    > [!NOTE]
    >  當您從應用程式移除原則時，也會從規則引擎資料庫刪除它所依存的原則和詞彙，而不只是從應用程式刪除。  
  
#### <a name="to-import-the-xml-file-to-re-create-the-processpurchaseorder-policy"></a>若要匯入 XML 檔案以重新建立 ProcessPurchaseOrder 原則  
  
1.  在 BizTalk Server 管理，依序展開**主控台根目錄**，依序展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，然後展開**BizTalk 群組**。  
  
2.  以滑鼠右鍵按一下**應用程式**，指向 **匯入**，然後按一下 **原則**。  
  
3.  瀏覽，然後按兩下 XML 檔案 (**C:\BRE-Walkthroughs\ProcessPOFromAdmin.xml**) 在第一個程序中所建立。  
  
4.  展開**\<所有成品\>** 下**應用程式**。  
  
5.  按一下**原則**，而且您應該會看見 1.3 版**ProcessPurchaseOrder**原則清單中的。  
  
6.  按 F5 重新整理檢視。 **ProcessPurchaseOrder**原則應該處於**未發行**狀態。  
  
#### <a name="to-add-the-processpurchaseorder-policy-to-the-ruletestapp-application"></a>若要新增 ProcessPurchaseOrder 原則至 RuleTestApp 應用程式  
  
1.  在 BizTalk Server 管理，以滑鼠右鍵按一下**ProcessPurchaseOrder**原則，然後再按一下**發行**。  
  
    > [!NOTE]
    >  只有已發佈的原則才可以加入至 BizTalk 應用程式。  
  
2.  在**應用程式**] 節點，展開 [ **RuleTestApp**。  
  
3.  按一下**原則**中**RuleTestApp**。  
  
4.  以滑鼠右鍵按一下右邊清單中，指向**新增**，然後按一下 **原則**。  
  
5.  展開**ProcessPurchaseOrder**節點中，選取的核取方塊 **（已發佈） 1.3 版**，然後按一下 **確定**。 執行個體時提供 SQL Server 登入。  
  
6.  以滑鼠右鍵按一下**ProcessPurchaseOrder**，然後按一下 **部署**。 如果您沒有看到**ProcessPurchaseOrder**在清單中，按下 F5 以重新整理檢視。  
  
7.  按一下**是**確認訊息方塊中。  
  
## <a name="procedures-for-deploying-the-policy-by-using-an-msi-file"></a>使用 MSI 檔案部署原則的程序  
  
#### <a name="to-export-the-ruletestapp-application-to-an-msi-file"></a>若要匯出 RuleTestApp 應用程式至 MSI 檔案  
  
1.  在**啟動**功能表中，開啟**BizTalk Server 管理**。 如果您已經開啟此工具，請按 F5 重新整理。  
  
2.  展開**主控台根目錄**，依序展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，依序展開**BizTalk 群組**，然後展開**應用程式**。  
  
3.  以滑鼠右鍵按一下**RuleTestApp**，指向 **匯出**，然後按一下  **MSI 檔案**。  
  
4.  在**歡迎使用匯出 MSI 檔案精靈**頁面上，按一下**下一步**。  
  
5.  在**選取資源**頁面上，檢閱所有的預設選項，然後按**下一步**。  
  
6.  在**指定 IIS 主控件**頁面上，按一下**下一步**。  
  
7.  在**相依性**頁面上，按一下**下一步**。  
  
8.  在**目的地**頁面上，指定的目錄和名稱為 MSI **C:\BRE-Walkthroughs\RuleTestApp.msi**。  
  
9. 按一下 **[匯出]**。  
  
10. 在**摘要**頁面上，按一下**完成**。  
  
    > [!NOTE]
    >  當您匯出 RuleTestApp 應用程式時，應用程式使用的原則和詞彙也會匯出至 MSI 檔案。 稍後匯入 MSI 檔案時，便會重新建立所有的詞彙、原則和應用程式。  
  
#### <a name="to-delete-the-ruletestapp-application"></a>若要刪除 RuleTestApp 應用程式  
  
1.  在 BizTalk Server 管理，以滑鼠右鍵按一下**RuleTestApp**，並檢查**刪除**功能表是啟用或停用。  
  
2.  如果**刪除**是停用，以滑鼠右鍵按一下**RuleTestApp**，按一下 **停止**，選取**完全停止-終止執行個體**，然後按一下  **停止**。  
  
3.  以滑鼠右鍵按一下**RuleTestApp**，然後按一下 **刪除**。  
  
4.  按一下**是**確認刪除。  
  
    > [!NOTE]
    >  當您刪除應用程式時，也會從規則引擎資料庫刪除應用程式中的所有原則及相依詞彙。  
  
#### <a name="to-verify-that-the-processpurchaseorder-policy-and-povocabulary-vocabulary-are-deleted"></a>若要確認 ProcessPurchaseOrder 原則和 POVocabulary 詞彙已刪除  
  
1.  在**啟動**功能表中，開啟**商務規則編輯器 」**。 如果已開啟 [商務規則編輯器]，請按下 F5 重新整理。  
  
    > [!NOTE]
    >  在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。 若要這樣做，應用程式，以滑鼠右鍵按一下，然後選取**系統管理員身分執行**。  
  
2.  在 [原則總管] 視窗中，依序展開**原則**，並確定 ProcessPurchaseOrder 原則不存在。  
  
3.  在 [事實總管] 視窗中，依序展開**詞彙**，並確定 POVocabulary 不存在。  
  
#### <a name="to-import-the-msi-file-to-re-create-the-ruletestapp-application"></a>若要匯入 MSI 檔案以重新建立 RuleTestApp 應用程式  
  
1.  在**啟動**功能表中，開啟**BizTalk Server 管理**。 如果已經開啟 BizTalk Server 管理主控台，請按 F5 重新整理它。  
  
2.  展開**主控台根目錄**，依序展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，然後展開**BizTalk 群組**。  
  
3.  以滑鼠右鍵按一下**應用程式**，指向 **匯入**，然後按一下  **MSI 檔案**。  
  
4.  在**歡迎使用匯入精靈**頁面上，瀏覽並選取您稍早匯出的 MSI 檔案 (RuleTestApp.msi)**要匯入 MSI 檔案**設定。  
  
5.  按一下 **[下一步]**。  
  
6.  在**應用程式設定**頁面上，按一下**下一步**。  
  
7.  在**應用程式目標環境設定**頁面上，按一下**下一步**。  
  
8.  在**匯入摘要**頁面上，按一下**匯入**。  
  
9. 在**匯入成功**頁面上，按一下**完成**。 您應該會看到**RuleTestApp**下方會建立應用程式**應用程式**BizTalk Server 管理主控台中。  
  
#### <a name="to-verify-that-the-processpurchaseorder-policy-is-added-to-ruletestapp"></a>若要確認 ProcessPurchaseOrder 原則已新增至 RuleTestApp  
  
1.  展開**RuleTestApp** BizTalk Server 管理主控台中。  
  
2.  選取**原則**和您應該會看到**ProcessPurchaseOrder**在右窗格的清單中。  
  
#### <a name="to-verify-that-the-processpurchaseorder-policy-and-povocabulary-vocabulary-are-re-created"></a>若要確認 ProcessPurchaseOrder 原則和 POVocabulary 詞彙已重新建立  
  
1.  在**啟動**功能表中，開啟**商務規則編輯器 」**。 如果您已經開啟它，請按 F5 重新整理。  
  
    > [!NOTE]
    >  在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。 若要這樣做，應用程式，以滑鼠右鍵按一下，然後選取**系統管理員身分執行**。  
  
2.  在 [原則總管] 視窗中，依序展開**原則**，並確定**ProcessPurchaseOrder**存在。  
  
3.  在 [事實總管] 視窗中，依序展開**詞彙**，並確定**POVocabulary**存在。  
  
#### <a name="to-test-the-solution"></a>測試方案  
  
1.  在**啟動**功能表中，開啟**BizTalk Server 管理**。 如果已經開啟 BizTalk Server 管理主控台，請按 F5 重新整理它。  
  
2.  展開**主控台根目錄**，依序展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，依序展開**BizTalk 群組**，然後展開**應用程式**。  
  
3.  以滑鼠右鍵按一下**RuleTestApp**，然後按一下 **啟動**。  
  
4.  按一下 **[啟動]**。  
  
5.  複製**SamplePO.xml**您在建立[逐步解說： 測試原則](../core/walkthrough-testing-the-policy.md)協調流程的輸入目錄。  
  
6.  您應該會在協調流程的輸出目錄中看到輸出檔案。 開啟輸出 XML 檔案，並請注意，值**狀態**欄位設定為**Approved**。  
  
7.  重複步驟 3 和 4 **SamplePO2.xml**，並注意值**狀態**輸出文件中的欄位會與輸入文件中的相同 (**XYZ**)。  
  
## <a name="comments"></a>註解  
  
-   它是**非常重要**請記得，當您從應用程式移除原則時，您除了移除應用程式和原則之間的關聯; 也從規則中刪除的原則和其相關聯的詞彙引擎 」 資料庫。  
  
-   當您啟動應用程式時，它會依預設自動部署原則。 同樣地，當您停止應用程式並選取**完全停止-終止執行個體**，相關聯的原則會自動解除部署。 當您選取**部分停止-擱置正在執行的執行個體**，相關聯的原則解除部署自動。  
  
-   在執行任何作業之前，應該重新整理「商務規則編輯器」和「BizTalk Server 管理主控台」中的檢視，確定您看到的是最新資訊。  
  
-   如果您建立新的版本，其舊版是 BizTalk 應用程式相關聯的原則，您應手動將新版本的原則加入至應用程式。 您不應該移除舊版本的原則，除非您真的要將它從規則引擎資料庫刪除。  
  
-   您可以在匯入前，將兩個或更多的 BRL 檔案 (商務規則語言 XML 檔案) 合併到單一的 BRL 檔案中。 下列程式碼顯示三個 BRL 檔案。 第一個 BRL 檔案包含**POVocabulary**詞彙。 第二個 BRL 檔案包含**ProcessPurchaseOrder**原則。 第三個 BRL 檔案同時包含**POVocabulary**詞彙和**ProcessPurchaseOrder**原則。 第三個 BRE 檔案是藉由執行下列步驟所建立：  
  
    1.  建立新的檔案使用的任何檔案編輯器，並將它儲存為 XML 檔案 (例如： POPolicyVocabulary.xml)。  
  
    2.  從包含詞彙的第一個 BRL 檔案複製整個 XML 內容。  
  
    3.  複製規則集區塊 (以開始\<ruleset\>標記，且結尾為\</ruleset\>標記) 從第二個 BRL 檔案。  
  
    4.  儲存新檔案。 您可以匯入這個單一 XML 檔案，以建立**POVocabulary**詞彙和**ProcessPurchaseOrder**原則。  
  
    > [!NOTE]
    >  在合併的 BRL 檔案中，詞彙和規則集節點的列出順序並不重要。 您可以讓規則集節點列在詞彙節點前頭。  
  
    ```  
    <?xml version="1.0" encoding="utf-8"?>  
    <brl  
    xmlns="http://schemas.microsoft.com/businessruleslanguage/2002">  
      <vocabulary id="e588676a-ba01-4f37-b59d-91f7e1eb1f1a" name="POVocabulary" uri="" description="">  
           ……   
      </vocabulary>  
    </brl>  
  
    <?xml version="1.0" encoding="utf-8"?>  
    <brl  
    xmlns="http://schemas.microsoft.com/businessruleslanguage/2002">  
      <ruleset name="ProcessPurchaseOrder">  
         ……  
      </ruleset>  
    </brl>  
  
    <brl  
    xmlns="http://schemas.microsoft.com/businessruleslanguage/2002">  
      <vocabulary id="e588676a-ba01-4f37-b59d-91f7e1eb1f1a" name="POVocabulary" uri="" description="">  
           ……   
      </vocabulary>  
      <ruleset name="ProcessPurchaseOrder">  
         ……  
      </ruleset>  
    </brl>  
    ```