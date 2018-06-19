---
title: 步驟 1： 修改 vPrev 使用 SQL 配接器的 BizTalk 專案 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 25ad959b-2818-47b8-9a09-3681abb75887
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8f0eb02594251fa5ab1c209c1d2655056cf489df
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22226422"
---
# <a name="step-1-modify-the-vprev-biztalk-project-using-the-sql-adapter"></a>步驟 1： 修改 vPrev 使用 SQL 配接器的 BizTalk 專案
![步驟 3 之 1](../../adapters-and-accelerators/adapter-oracle-database/media/step-1of3.gif "Step_1of3")  
  
 **若要完成的時間：** 10 分鐘  
  
 **目標：** 在此步驟中，您必須進行下列變更現有 vPrev BizTalk 專案：  
  
-   產生使用 WCF 為基礎的客戶資料表的 Insert 作業的中繼資料[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。  
  
-   執行使用 vPrev SQL 配接器的要求訊息來執行插入作業使用以 WCF 為基礎的插入作業的要求訊息對應[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。  
  
-   使用 WCF 為基礎所接收的回應訊息對應[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]使用 vPrev SQL 配接器接收的回應訊息。  
  
## <a name="prerequisites"></a>必要條件  
 您必須執行 SQL Server 資料庫中的客戶資料表上的 Insert 作業 vPrev BizTalk 專案。  
  
### <a name="to-modify-the-vprev-biztalk-project"></a>若要修改 vPrev BizTalk 專案  
  
1.  產生使用 WCF 為基礎的客戶資料表的 Insert 作業的中繼資料[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。 您可以使用[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]產生中繼資料。  
  
     如需有關如何產生中繼資料的指示，請參閱[取得中繼資料，使用 SQL 配接器的 Visual Studio 中的 SQL Server 作業的](../../adapters-and-accelerators/adapter-sql/get-metadata-for-sql-server-operations-in-visual-studio-using-the-sql-adapter.md)。 結構描述產生之後，類似於名稱的檔案*TableOperation.dbo.Customer.xsd*會加入至 BizTalk 專案。 這個檔案包含傳送訊息，以執行插入作業客戶資料表上的使用以 WCF 為基礎的 SQL Server 資料庫中的結構描述[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。  
  
2.  產生插入作業的中繼資料時，也會建立連接埠繫結檔案。 在下一個步驟中，此繫結檔案，將用來建立 Wcf-custom 傳送埠將訊息傳送至 SQL Server 資料庫中。 作業的 SOAP 動作也會設為您產生的中繼資料作業。 比方說，如果您產生插入作業的中繼資料，傳送埠上的 SOAP 動作中的作業名稱就是 「 插入 」。 不過，作業名稱的協調流程的一部分，例如可能不同，您建立邏輯傳送連接埠上"Operation_1"。 如此一來，當您傳送訊息至 SQL Server 資料庫使用的傳送埠時，您會收到錯誤。 若要防止這個情況，請確定在邏輯上的作業名稱的傳送埠協調流程中的產生的中繼資料的作業名稱相同。  
  
     因此，本教學課程中，如果您產生插入作業的中繼資料，因為變更 「 插入 」 的邏輯傳送連接埠作業名稱。  
  
3.  要求訊息時，將使用 vPrev SQL 資料庫配接器，以產生使用 WCF 為基礎的結構描述產生的結構描述的對應[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。  
  
    1.  將 BizTalk 對應工具加入至 BizTalk 專案。 以滑鼠右鍵按一下 BizTalk 專案，指向**新增**，然後按一下 **新項目**。  
  
         在**加入新項目**對話方塊的左窗格中，選取**對應檔**。 從右窗格中，選取**對應**。 指定對應名稱，例如**RequestMap.btm**。 按一下 **[加入]**。  
  
    2.  從來源結構描述] 窗格中，按一下 [**開啟來源結構描述**。  
  
    3.  在**BizTalk 型別選擇器**對話方塊方塊中，展開 專案名稱，展開**結構描述**，然後選取 vPrev SQL 配接器的要求訊息的結構描述。 此教學課程中，選取*New_Migration.InsertCustomerService*，然後按一下 **確定**。  
  
    4.  在**來源結構描述的根節點**對話方塊中，選取*插入*，然後按一下 **確定**。  
  
    5.  從 目的結構描述 窗格中，按一下 **開啟目的結構描述**。  
  
    6.  在**BizTalk 型別選擇器**對話方塊方塊中，展開 專案名稱，展開**結構描述**，然後選取 以 WCF 為基礎的要求訊息的結構描述[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。 此教學課程中，選取*New_Migration.TableOperation.dbo.Customer*，然後按一下 **確定**。  
  
    7.  在**目標結構描述的根節點**對話方塊中，選取*插入*，然後按一下 **確定**。  
  
    8.  對應的結構描述中的個別項目，如下圖所示。  
  
         ![對應要求結構描述](../../adapters-and-accelerators/adapter-sql/media/850bbf52-fc3e-42c5-b879-51c6e39a502d.gif "850bbf52-fc3e-42c5-b879-51c6e39a502d")  
  
    9. 儲存對應。  
  
4.  回應訊息時，將使用 vPrev SQL 配接器，以產生使用 WCF 為基礎的結構描述產生的結構描述的對應[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。  
  
    1.  將 BizTalk 對應工具加入至 BizTalk 專案。 以滑鼠右鍵按一下 BizTalk 專案，指向**新增**，然後按一下**新項目**。  
  
         在**加入新項目**對話方塊的左窗格中，選取**對應檔**。 從右窗格中，選取**對應**。 指定對應名稱，例如**ResponseMap.btm**，然後按一下 **新增**。  
  
    2.  從來源結構描述] 窗格中，按一下 [**開啟來源結構描述**。  
  
    3.  在**BizTalk 型別選擇器**對話方塊方塊中，展開 專案名稱，展開**結構描述**，然後選取 以 WCF 為基礎的回應訊息的結構描述[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。 此教學課程中，選取*New_Migration.TableOperation.dbo.Customer*，然後按一下 **確定**。  
  
    4.  在**來源結構描述的根節點**對話方塊中，選取*InsertResponse*，然後按一下 **確定**。  
  
    5.  從 目的結構描述 窗格中，按一下 **開啟目的結構描述**。  
  
    6.  在**BizTalk 型別選擇器**對話方塊方塊中，展開 專案名稱，展開**結構描述**，然後選取 vPrev 的回應訊息的結構描述[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。 此教學課程中，選取*New_Migration.InsertCustomerService*，然後按一下 **確定**。  
  
    7.  在**目標結構描述的根節點**對話方塊中，選取*InsertResponse*，然後按一下 **確定**。  
  
    8.  您會發現一些不同的回應結構描述之間的兩個配接器所產生。 這些差異解釋如下：  
  
        -   使用 WCF 型[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]，如果您插入一筆記錄插入資料表，包含主索引鍵 （也是識別欄位） 的回應插入作業會傳回插入的資料列的識別欄位的值。 因此，不符合以 WCF 為基礎的回應訊息的結構描述[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]包含額外*InsertResult*項目。 這個項目包含陣列，其中包含插入的資料列的識別欄位。  
  
        -   使用 vPrev [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]，如果您將記錄插入資料表時，配接器只會傳回空白的 「 成功 」 項目做為回應訊息的一部分。  
  
         因此，將結構描述對應的方式，以 WCF 為基礎的回應[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]包含識別欄位的值 「 複製 」 做為 「 成功 」 的項目，這是來自 vPrev 的回應訊息的一部分的一部分[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。 您可以將兩個結構描述的元素複製到另一個使用大量複製運算質。  
  
         若要使用大量複製運算質從**工具箱**、 大量複製運算質拖放在對應工具格線。 連接**InsertResult** 」 運算質來源結構描述中的項目。 同樣地，連接**成功**運算質至目的結構描述中的項目。 下圖說明如何透過運算質對應兩個項目。  
  
         ![對應回應結構描述](../../adapters-and-accelerators/adapter-sql/media/c4a347ae-8d2d-4357-b18d-37f36bef17c7.gif "c4a347ae-8d2d-4357-b18d-37f36bef17c7")  
  
        > [!NOTE]
        >  如需有關大量複製運算質的詳細資訊，請參閱[http://go.microsoft.com/fwlink/?LinkId=119749](http://go.microsoft.com/fwlink/?LinkId=119749)。  
  
    9. 儲存對應。  
  
5.  儲存並建置 BizTalk 方案。 以滑鼠右鍵按一下方案，然後按一下**建置方案**。  
  
6.  部署該方案。 以滑鼠右鍵按一下方案，然後按一下**部署方案**。  
  
## <a name="next-steps"></a>後續步驟  
 建立 wcf-custom 傳送埠，並將它設定為使用您在此步驟中，建立的對應中所述[步驟 2： 使用 SQL 配接器的 BizTalk Server 管理主控台中設定協調流程](../../adapters-and-accelerators/adapter-sql/step-2-configure-the-orchestration-to-use-the-sql-adapter-in-biztalk-server.md)。  
  
## <a name="see-also"></a>另請參閱  
 [教學課程 1： 移轉至 SQL 配接器的 BizTalk 專案](../../adapters-and-accelerators/adapter-sql/tutorial-1-migrate-biztalk-projects-to-the-sql-adapter.md)