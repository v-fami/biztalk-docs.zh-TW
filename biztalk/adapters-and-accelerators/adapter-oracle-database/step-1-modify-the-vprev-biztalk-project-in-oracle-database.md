---
title: 步驟 1： 修改 vPrev BizTalk 專案中 Oracle 資料庫 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6e3e22ac-126b-46ec-a6dc-3421ad721392
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d5d55a5535d1f3f2234198d08393a314b1a304e5
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37010567"
---
# <a name="step-1-modify-the-vprev-biztalk-project-in-oracle-database"></a>步驟 1： 修改 vPrev BizTalk 專案中 Oracle 資料庫
![步驟 3 之 1](../../adapters-and-accelerators/adapter-oracle-database/media/step-1of3.gif "Step_1of3")  
  
 **若要完成的時間：** 10 分鐘  
  
 **目標：** 在此步驟中，您必須進行下列變更以現有的 vPrev BizTalk 專案：  
  
- 產生 SCOTT 的 Insert 作業的中繼資料。使用以 WCF 為基礎的 CUSTOMER 資料表[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。  
  
- 執行插入作業使用 vPrev Oracle 資料庫配接器的要求訊息來執行 Insert 作業使用以 WCF 為基礎的要求訊息對應[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。  
  
- 將使用以 WCF 為基礎所接收的回應訊息對應[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]vPrev Oracle 資料庫配接器的回應訊息。  
  
## <a name="prerequisites"></a>必要條件  
  
-   您必須執行插入作業上 SCOTT vPrev BizTalk 專案。Oracle 資料庫中的 CUSTOMER 資料表。  
  
## <a name="modify-the-vprev-biztalk-project"></a>修改 vPrev BizTalk 專案  
  
1. 產生 SCOTT 的 Insert 作業的中繼資料。使用以 WCF 為基礎的 CUSTOMER 資料表[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。 您可以使用[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]產生中繼資料。  
  
    如需有關如何產生中繼資料的指示，請參閱 <<c0> [ 取得 Visual Studio 中的 Oracle 資料庫作業的中繼資料](../../adapters-and-accelerators/adapter-oracle-database/get-metadata-for-oracle-database-operations-in-visual-studio.md)。 結構描述產生之後，具有類似名稱的檔案*OracleDBBindingSchema.xsd*會加入至 BizTalk 專案。 此檔案包含傳送訊息至執行插入作業在 SCOTT 的結構描述。使用 WCF 型 Oracle 資料庫中的 CUSTOMER 資料表[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。  
  
2. 產生插入作業的中繼資料時，也會建立連接埠繫結檔案。 在下一個步驟中，此繫結檔案將用於建立 Wcf-custom 傳送埠將訊息傳送至 Oracle 資料庫。 作業的 SOAP 動作也會設定為您要為其產生中繼資料作業中。 比方說，如果您產生插入作業的中繼資料，傳送埠上的 SOAP 動作中的作業名稱會是 「 插入 」。 不過，作業名稱的協調流程的一部分，例如可能不同，您建立邏輯傳送連接埠上"Operation_1"。 如此一來，當您將訊息傳送到 Oracle 資料庫使用的傳送埠時，您會收到錯誤。 若要避免這個問題，請確定邏輯上的作業名稱的傳送埠協調流程中的產生的中繼資料的作業名稱相同。  
  
    因此，本教學課程中，如果您產生插入作業的中繼資料，因為變更名稱"Insert"的邏輯傳送連接埠作業。  
  
3. 要求訊息中，將使用 vPrev Oracle 資料庫配接器，以產生使用 WCF 為基礎的結構描述產生的結構描述的對應[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。  
  
   1. 將 BizTalk 對應工具加入至 BizTalk 專案中。 以滑鼠右鍵按一下 BizTalk 專案，指向**新增**，然後按一下**新項目**。  
  
       在 **加入新項目**對話方塊中，從左窗格中，選取**對應檔**。 從右窗格中，選取**地圖**。 指定對應名稱，例如**RequestMap.btm**。 按一下 **[加入]**。  
  
   2. 從來源結構描述 窗格中，按一下**開啟來源結構描述**。  
  
   3. 在**BizTalk 型別選擇器**對話方塊方塊中，展開 專案名稱，展開**結構描述**，然後選取 vPrev Oracle 資料庫配接器的要求訊息的結構描述。 本教學課程中，選取*Oracle_Migration.CUSTOMERService_CUSTOMER_x5d*。 按一下 [確定] 。  
  
   4. 在 **來源結構描述的根節點**對話方塊中，選取*插入*，按一下  **確定**。  
  
   5. 從目的結構描述 窗格中，按一下**開啟目的結構描述**。  
  
   6. 在**BizTalk 型別選擇器**對話方塊方塊中，展開 專案名稱，展開**結構描述**，然後選取以 WCF 為基礎的要求訊息的結構描述[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。 本教學課程中，選取*Oracle_Migration.OracleDBBindingSchema*。 按一下 [確定] 。  
  
   7. 在 **目標結構描述的根節點**對話方塊方塊中，選取*插入*，按一下 **確定**。  
  
   8. 對應在這兩個結構描述中的個別項目，如下圖所示。  
  
       ![對應到 Oracle 資料庫所傳送的要求](../../adapters-and-accelerators/adapter-oracle-database/media/4cb59338-40d1-4eb1-bd89-b5a3183959e1.gif "4cb59338-40d1-4eb1-bd89-b5a3183959e1")  
  
   9. 儲存對應。  
  
4. 回應訊息，將使用 vPrev Oracle 資料庫配接器，以產生使用 WCF 為基礎的結構描述產生的結構描述的對應[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。  
  
   1. 將 BizTalk 對應工具加入至 BizTalk 專案中。 以滑鼠右鍵按一下 BizTalk 專案，指向**新增**，然後按一下**新項目**。  
  
       在 **加入新項目**對話方塊中，從左窗格中，選取**對應檔**。 從右窗格中，選取**地圖**。 指定對應名稱，例如**ResponseMap.btm**。 按一下 **[加入]**。  
  
   2. 從來源結構描述 窗格中，按一下**開啟來源結構描述**。  
  
   3. 在**BizTalk 型別選擇器**對話方塊方塊中，展開 專案名稱，展開**結構描述**，然後選取以 WCF 為基礎的回應訊息的結構描述[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。 本教學課程中，選取*Oracle_Migration.OracleDBBindingSchema*。 按一下 [確定] 。  
  
   4. 在 **來源結構描述的根節點**對話方塊方塊中，選取*InsertResponse* ，按一下 **確定**。  
  
   5. 從目的結構描述 窗格中，按一下**開啟目的結構描述**。  
  
   6. 在**BizTalk 型別選擇器**對話方塊方塊中，展開 專案名稱，展開**結構描述**，然後選取 vPrev Oracle 資料庫配接器的回應訊息的結構描述。 本教學課程中，選取*Oracle_Migration.CUSTOMERService_CUSTOMER_x5d*。 按一下 [確定] 。  
  
   7. 在 **目標結構描述的根節點**對話方塊中，選取*InsertResponse*，然後按一下**確定**。  
  
   8. 您會發現，符合以 WCF 為基礎的回應訊息的結構描述[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]包含額外*InsertResult*項目。 您必須從結構描述與對應中移除這*InsertResponse*這兩個結構描述中的項目。  
  
       若要這樣做，請從**工具箱**，拖曳**字串左空白位置修剪**運算質放在對應工具格線。 連接**InsertResponse**運算質將來源結構描述中的項目。 同樣地，連接**InsertResponse**運算質至目的結構描述中的項目。 下圖說明兩個項目透過運算質的對應方式。  
  
       ![對應從 Oracle 資料庫接收的回應](../../adapters-and-accelerators/adapter-oracle-database/media/7fe18f5b-100f-4fe2-ac92-c111629d7fe9.gif "7fe18f5b-100f-4fe2-ac92-c111629d7fe9")  
  
      > [!NOTE]
      >  如需詳細資訊，請參閱 <<c0>  **字串左空白位置修剪運算質** [!INCLUDE[ui-guidance-developers-reference](../../includes/ui-guidance-developers-reference.md)]。
  
   9. 儲存對應。  
  
5. 儲存並建置 BizTalk 方案。 以滑鼠右鍵按一下方案，然後按一下**建置方案**。  
  
6. 部署該方案。 以滑鼠右鍵按一下方案，然後按一下**部署方案**。  
  
## <a name="next-steps"></a>後續步驟  
 建立 wcf-custom 傳送埠，並將它設定為使用您在此步驟中，建立的對應中所述[步驟 2： 使用 SQL 配接器的 Biztalk Server 管理主控台中設定協調流程](../../adapters-and-accelerators/adapter-sql/step-2-configure-the-orchestration-to-use-the-sql-adapter-in-biztalk-server.md)。  
  
## <a name="see-also"></a>另請參閱  
 [教學課程： 移轉 BizTalk 專案](https://msdn.microsoft.com/library/dd788186(v=bts.80).aspx)