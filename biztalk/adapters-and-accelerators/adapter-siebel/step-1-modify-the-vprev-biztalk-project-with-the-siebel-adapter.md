---
title: 步驟 1： 修改 vPrev BizTalk 專案與 Siebel 配接器 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b7bd95e2-bd51-420f-8156-6f17cc0e91d6
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e03b915abcaef48cf8c31001f6c096e5040a247b
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37004183"
---
# <a name="step-1-modify-the-vprev-biztalk-project-with-the-siebel-adapter"></a>步驟 1： 修改 vPrev BizTalk 專案與 Siebel 配接器
![步驟 3 之 1](../../adapters-and-accelerators/adapter-oracle-database/media/step-1of3.gif "Step_1of3")  
  
 **若要完成的時間：** 10 分鐘  
  
 **目標：** 在此步驟中，您必須進行下列變更以現有的 vPrev BizTalk 專案：  
  
- 產生使用 WCF 為基礎的商務帳戶元件上的插入作業的中繼資料[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]。  
  
- 執行插入作業使用 vPrev Siebel 配接器要求訊息來執行插入作業使用以 WCF 為基礎的要求訊息對應[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]。  
  
- 將使用以 WCF 為基礎所接收的回應訊息對應[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]vPrev Siebel 配接器的回應訊息。  
  
## <a name="prerequisite"></a>必要條件  
  
-   您必須具有 vPrev BizTalk 專案到 Siebel 系統中執行插入作業帳戶商務元件上。  
  
### <a name="to-modify-the-vprev-biztalk-project"></a>若要修改 vPrev BizTalk 專案  
  
1. 產生使用 WCF 為基礎的商務帳戶元件上的插入作業的中繼資料[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]。 您可以使用[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]產生中繼資料。  
  
    如需有關如何產生中繼資料的指示，請參閱 <<c0> [ 取得 Siebel 作業，在 Visual Studio 中的中繼資料](../../adapters-and-accelerators/adapter-siebel/get-metadata-for-siebel-operations-in-visual-studio.md)。 結構描述產生之後，具有類似名稱的檔案*SiebelBindingSchema.xsd*會加入至 BizTalk 專案。 此檔案包含傳送訊息至執行插入作業，使用以 WCF 為基礎的商務帳戶元件上的結構描述[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]。  
  
2. 產生插入作業的中繼資料時，也會建立連接埠繫結檔案。 在下一個步驟中，此繫結檔案將用於建立 Wcf-custom 傳送埠將訊息傳送至 Siebel 系統。 作業的 SOAP 動作也會設定為您要為其產生中繼資料作業中。 比方說，如果您產生插入作業的中繼資料，傳送埠上的 SOAP 動作中的作業名稱會是 「 插入 」。 不過，作業名稱的協調流程的一部分，例如可能不同，您建立邏輯傳送連接埠上"Operation_1"。 如此一來，當您將訊息傳送至 Siebel 系統使用的傳送埠時，您會收到錯誤。 若要避免這個問題，請確定邏輯上的作業名稱的傳送埠協調流程中的產生的中繼資料的作業名稱相同。  
  
    因此，本教學課程中，如果您產生插入作業的中繼資料，因為變更名稱"Insert"的邏輯傳送連接埠作業。  
  
3. 要求訊息中，將使用 vPrev Siebel 配接器，以產生使用 WCF 為基礎的結構描述產生的結構描述的對應[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]。  
  
   1. 將 BizTalk 對應工具加入至 BizTalk 專案中。 以滑鼠右鍵按一下 BizTalk 專案，指向**新增**，然後按一下**新項目**。  
  
       在 **加入新項目**對話方塊中，從左窗格中，選取**對應檔**。 從右窗格中，選取**地圖**。 指定對應名稱，例如**RequestMap.btm**。 按一下 **[加入]**。  
  
   2. 從來源結構描述 窗格中，按一下**開啟來源結構描述**。  
  
   3. 在**BizTalk 型別選擇器**對話方塊方塊中，展開 專案名稱，展開**結構描述**，然後選取 vPrev Siebel 配接器的要求訊息的結構描述。 本教學課程中，選取*Siebel_BussComp_Migration.AccountService_Account_x5d*。 按一下 [確定] 。  
  
   4. 在 **來源結構描述的根節點**對話方塊中，選取*插入*，然後按一下**確定**。  
  
   5. 從目的結構描述 窗格中，按一下**開啟目的結構描述**。  
  
   6. 在**BizTalk 型別選擇器**對話方塊方塊中，展開 專案名稱，展開**結構描述**，然後選取以 WCF 為基礎的要求訊息的結構描述[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]。 本教學課程中，選取*Siebel_BussComp_Migration.SiebelDBBindingSchema*，然後按一下**確定**。  
  
   7. 在 **目標結構描述的根節點**對話方塊中，選取*插入*，然後按一下**確定**。  
  
   8. 對應的結構描述中的下列元素： **Currency_Code**， **Current_Volume**， **Customer_Account_Group**，**位置**，**Main_Phone_Number**，**名稱**， **Party_Name**， **Primary_Address_Id**，  
  
   9. 儲存對應。  
  
4. 回應訊息，將使用 vPrev Siebel 配接器，以產生使用 WCF 為基礎的結構描述產生的結構描述的對應[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]。  
  
   1. 將 BizTalk 對應工具加入至 BizTalk 專案中。 以滑鼠右鍵按一下 BizTalk 專案，指向**新增**，然後按一下**新項目**。  
  
       在 [加入新項目] 對話方塊中，從左窗格中，選取**對應檔**。 從右窗格中，選取**地圖**。 指定對應名稱，例如**ResponseMap.btm**。 按一下 **[加入]**。  
  
   2. 從來源結構描述 窗格中，按一下**開啟來源結構描述**。  
  
   3. 在**BizTalk 型別選擇器**對話方塊方塊中，展開 專案名稱，展開**結構描述**，然後選取以 WCF 為基礎的回應訊息的結構描述[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]。 本教學課程中，選取*Siebel_BussComp_Migration.SiebelDBBindingSchema*。 按一下 [確定] 。  
  
   4. 在 **來源結構描述的根節點**對話方塊方塊中，選取*InsertResponse* ，按一下 **確定**。  
  
   5. 從目的結構描述 窗格中，按一下**開啟目的結構描述**。  
  
   6. 在**BizTalk 型別選擇器**對話方塊方塊中，展開 專案名稱，展開**結構描述**，然後選取 vPrev Siebel 配接器的回應訊息的結構描述。 本教學課程中，選取*Siebel_BussComp_Migration.AccountService_Account_x5d*。 按一下 [確定] 。  
  
   7. 在 **目標結構描述的根節點**對話方塊方塊中，選取*InsertResponse* ，按一下 **確定**。  
  
   8. 地圖**陣列： 字串**來源結構描述中的項目**公開： 字串**與目的結構描述，如下圖所示的項目。  
  
       ![對應的回應訊息，配接器版本之間](../../adapters-and-accelerators/adapter-siebel/media/6352035b-79c0-4850-a8f7-e4f6581c8532.gif "6352035b-79c0-4850-a8f7-e4f6581c8532")  
  
   9. 儲存對應。  
  
5. 儲存並建置 BizTalk 方案。 以滑鼠右鍵按一下方案，然後按一下**建置方案**。  
  
6. 部署該方案。 以滑鼠右鍵按一下方案，然後按一下**部署方案**。  
  
## <a name="next-steps"></a>後續步驟  
 建立 wcf-custom 傳送埠，並將它設定為使用您在此步驟中，建立的對應中所述[步驟 2： 設定協調流程中使用 Oracle 資料庫配接器的 BizTalk Server 管理主控台](../../adapters-and-accelerators/adapter-oracle-database/step-2-configure-an-orchestration-to-use-the-oracle-db-adapter-in-biztalk.md)。  
  
## <a name="see-also"></a>另請參閱  
 [教學課程 2： 移轉 BizTalk 專案中 Siebel](../../adapters-and-accelerators/adapter-siebel/tutorial-2-migrating-biztalk-projects-in-siebel.md)