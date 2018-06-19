---
title: 步驟 2： 使用 SQL 配接器的 BizTalk Server 管理主控台中設定協調流程 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d6152560-5ff0-4bdc-818c-e906b9642f52
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9b090ae83f0ca36bb4ae95795480d5f0d1661f16
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22223790"
---
# <a name="step-2-configure-the-orchestration-in-biztalk-server-administration-console-using-the-sql-adapter"></a>步驟 2： 使用 SQL 配接器的 BizTalk Server 管理主控台中設定協調流程
![步驟 3 之 2](../../adapters-and-accelerators/adapter-oracle-database/media/step-2of3.gif "Step_2of3")  
  
 **若要完成的時間：** 10 分鐘  
  
 **目標：** 在此步驟中，您可以執行下列工作：  
  
-   建立 WCF 自訂傳送-接收埠以傳送和接收訊息，從 SQL Server 資料庫使用[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。 設定此連接埠使用您在上一個步驟中建立的對應。  
  
-   設定協調流程使用 WCF 自訂連接埠上一個步驟中部署。  
  
## <a name="prerequisites"></a>必要條件  
 您應該部署 BizTalk 協調流程，您要設定 WCF 自訂連接埠中所述[步驟 1： 修改 vPrev 使用 SQL 配接器的 BizTalk 專案](../../adapters-and-accelerators/adapter-sql/step-1-modify-the-vprev-biztalk-project-using-the-sql-adapter.md)。  
  
### <a name="to-create-a-wcf-custom-port"></a>若要建立一個 WCF 自訂連接埠  
  
1.  當您產生結構描述作業的 SQL Server 資料庫使用[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]，繫結檔案也會加入至 BizTalk 專案。 您可以將此繫結檔案匯入到您的 BizTalk 應用程式建立 Wcf-custom 傳送-接收埠。 如需匯入繫結檔案的指示，請參閱[匯入繫結](http://msdn.microsoft.com/library/48de3a04-4ce8-4ba9-91b6-7e125689fd53)。  
  
2.  在您匯入繫結檔案之後，會建立傳送埠**傳送埠**資料夾中的[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。  
  
3.  以滑鼠右鍵按一下 WCF 自訂連接埠，然後按一下**屬性**。  
  
4.  從傳送埠屬性 對話方塊的左窗格中，按一下 **一般** 索引標籤。從右窗格中，按一下**設定**。  
  
5.  在**Wcf-custom 傳輸屬性**對話方塊中，按一下 **認證**索引標籤上，指定的認證來連接到 SQL Server 資料庫，然後按一下**確定**。  
  
6.  從傳送埠屬性] 對話方塊的左窗格中，按一下 [**輸入對應**。 從右窗格中，按一下 下的欄位**對應**資料行中，從下拉式清單選取**ResponseMap**。  
  
     ![設定輸入的對應](../../adapters-and-accelerators/adapter-sql/media/21e5a23c-7319-4324-8f09-52118ebeeea9.gif "21e5a23c-7319-4324-8f09-52118ebeeea9")  
  
7.  從傳送埠屬性] 對話方塊的左窗格中，按一下 [**輸出對應**。 從右窗格中，按一下 下的欄位**對應**資料行中，從下拉式清單選取**RequestMap**。  
  
     ![設定輸出對應](../../adapters-and-accelerators/adapter-sql/media/5b54e09b-8784-4df6-a279-e8aed813114e.gif "5b54e09b-8784-4df6-a279-e8aed813114e")  
  
8.  按一下 **[確定]**。  
  
### <a name="to-configure-the-biztalk-application"></a>若要設定 BizTalk 應用程式  
  
1.  在 BizTalk Server 管理主控台中，展開  **BizTalk 群組**，依序展開**應用程式**，然後展開 協調流程部署所在的 BizTalk 應用程式。  
  
2.  以滑鼠右鍵按一下 BizTalk 應用程式，然後選取**設定**。  
  
3.  從左窗格中，按一下 協調流程設定。 從右窗格中，從**主機**下拉式清單中，選取 BizTalk 主控件執行個體。  
  
4.  在下**繫結**方塊中，將 BizTalk 協調流程的邏輯連接埠對應到實體連接埠中[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。  
  
    1.  選取您將在此置放要求訊息的檔案連接埠。 BizTalk 協調流程會使用要求訊息，並將它傳送給 SQL Server 資料庫。  
  
    2.  選取 BizTalk 協調流程將會卸除包含從 SQL Server 資料庫回應的回應訊息的檔案連接埠。  
  
    3.  選取您稍早在本主題中所建立的 WCF 自訂傳送連接埠。  
  
    4.  按一下 **[確定]**。  
  
## <a name="next-steps"></a>後續步驟  
 您現在已完成的 vPrev BizTalk 專案，以將訊息傳送至使用 WCF 為基礎的 SQL Server 資料庫的 BizTalk 專案移轉[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。 您現在必須測試已移轉的 BizTalk 應用程式傳送至執行 SQL Server 資料庫中，插入作業的要求訊息中所述[步驟 3： 測試移轉應用程式使用 SQL 配接器](../../adapters-and-accelerators/adapter-sql/step-3-test-the-migrated-application-that-uses-the-sql-adapter.md)。  
  
## <a name="see-also"></a>另請參閱  
 [教學課程 1： 移轉至 SQL 配接器的 BizTalk 專案](../../adapters-and-accelerators/adapter-sql/tutorial-1-migrate-biztalk-projects-to-the-sql-adapter.md)