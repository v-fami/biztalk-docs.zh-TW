---
title: 步驟 1： 修改 vPrev BizTalk 專案的叫用 RFC |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- migration, modifying previous version of BizTalk project for invoking an RFC
- migration
ms.assetid: 2d4a6cd7-d216-4e0f-8f82-41e044cd325b
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2e2624ede6d2710db2d82311c2f452f8be372aa2
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36969647"
---
# <a name="step-1-modify-the-vprev-biztalk-project-for-invoking-an-rfc"></a>步驟 1： 修改 vPrev BizTalk 專案的叫用 RFC
![步驟 3 之 1](../../adapters-and-accelerators/adapter-oracle-database/media/step-1of3.gif "Step_1of3")  
  
 **若要完成的時間：** 10 分鐘  
  
 **目標：** 在此步驟中，您必須進行下列變更以現有的 vPrev BizTalk 專案：  
  
- 產生中繼資料的使用以 WCF 為基礎的 SD_RFC_CUSTOMER_GET RFC [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。  
  
- 將叫用 RFC 使用 vPrev SAP 配接器的要求訊息來叫用 RFC 使用以 WCF 為基礎的要求訊息對應[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。  
  
- 將使用以 WCF 為基礎所接收的回應訊息對應[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]vPrev SAP 配接器的回應訊息。  
  
## <a name="prerequisite"></a>必要條件  
  
-   您必須叫用 SD_RFC_CUSTOMER_GET RFC，SAP 系統中的 vPrev BizTalk 專案。  
  
### <a name="to-modify-the-vprev-biztalk-project"></a>若要修改 vPrev BizTalk 專案  
  
1. 產生中繼資料的使用以 WCF 為基礎的 SD_RFC_CUSTOMER_GET RFC [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。 您可以使用[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]產生中繼資料。  
  
    如需如何產生 Rfc 的中繼資料的指示，請參閱 <<c0> [ 瀏覽、 搜尋及取得中繼資料，在 SAP 中的 RFC 作業的](../../adapters-and-accelerators/adapter-sap/browse-search-and-get-metadata-for-rfc-operations-in-sap.md)。 結構描述產生之後，具有類似名稱的檔案*SapBindingSchema.xsd*會加入至 BizTalk 專案。 此檔案包含的結構描述來叫用使用以 WCF 為基礎的 SD_RFC_CUSTOMER_GET [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。  
  
2. 產生的 SD_RFC_CUSTOMER_GET RFC 的中繼資料時，也會建立連接埠繫結檔案。 在下一個步驟中，此繫結檔案將用於建立 Wcf-custom 傳送埠將訊息傳送至 SAP 系統。 作業的 SOAP 動作也會設定為您要為其產生中繼資料作業中。 比方說，如果您產生 SD_RFC_CUSTOMER_GET rfc 的中繼資料，傳送埠上的 SOAP 動作中的作業名稱會 「 SD_RFC_CUSTOMER_GET"。 不過，作業名稱的協調流程的一部分，例如可能不同，您建立邏輯傳送連接埠上"Operation_1"。 如此一來，當您將訊息傳送到 SAP 系統使用的傳送埠時，您會收到錯誤。 若要避免這個問題，請確定邏輯上的作業名稱的傳送埠協調流程中的產生的中繼資料的作業名稱相同。  
  
    因此，在本教學課程中，由於您會產生 SD_RFC_CUSTOMER_GET RFC 的中繼資料，變更 「 SD_RFC_CUSTOMER_GET"的邏輯傳送連接埠作業的名稱。  
  
3. 要求訊息中，將使用 vPrev SAP 配接器，以產生使用 WCF 為基礎的結構描述產生的結構描述的對應[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。  
  
   1. 將 BizTalk 對應工具加入至 BizTalk 專案中。 以滑鼠右鍵按一下 BizTalk 專案，指向**新增**，然後按一下**新項目**。  
  
       在 **加入新項目**對話方塊中，從左窗格中，選取**對應檔**。 從右窗格中，選取**地圖**。 指定對應名稱，例如**RequestMap.btm**。 按一下 **[加入]**。  
  
   2. 從來源結構描述 窗格中，按一下**開啟來源結構描述**。  
  
   3. 在**BizTalk 型別選擇器**對話方塊方塊中，展開 專案名稱，展開**結構描述**，然後選取 vPrev SAP 配接器的要求訊息的結構描述。 本教學課程中，選取*SAP_Migration.SD_RFC_CUSTOMER_GET__x32003*，然後按一下**確定**。  
  
   4. 在 **來源結構描述的根節點**對話方塊中，選取*SD_RFC_CUSTOMER_GET_Request*，然後按一下**確定**。  
  
   5. 從目的結構描述 窗格中，按一下**開啟目的結構描述**。  
  
   6. 在**BizTalk 型別選擇器**對話方塊方塊中，展開 專案名稱，展開**結構描述**，然後選取以 WCF 為基礎的要求訊息的結構描述[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。 本教學課程中，選取*SAP_Migration.SapBindingSchema*，然後按一下 [確定]。  
  
   7. 在 **目標結構描述的根節點**對話方塊中，選取*SD_RFC_CUSTOMER_GET*，然後按一下**確定**。  
  
       對應在這兩個結構描述中的個別項目，如下圖所示。 對應使用 「 字串左空白位置修剪 」 運算質的 CUSTOMER_T 項目。 若要這樣做，請從**工具箱**，拖曳**字串左空白位置修剪**運算質放在對應工具格線。 連接**CUSTOMER_T**運算質將來源結構描述中的項目。 同樣地，連接**CUSTOMER_T**運算質至目的結構描述中的項目。 下圖說明兩個項目透過運算質的對應方式。  
  
       ![對應配接器版本之間的要求訊息](../../adapters-and-accelerators/adapter-sap/media/f12f280d-766f-4647-bced-435354206fb9.gif "f12f280d-766f-4647-bced-435354206fb9")  
  
      > [!NOTE]
      >  「 字串左空白位置修剪 」 運算質的詳細資訊，請參閱 「 字串左空白位置修剪運算質 」，網址[ http://go.microsoft.com/fwlink/?LinkId=105774 ](http://go.microsoft.com/fwlink/?LinkId=105774)。  
  
   8. 儲存對應。  
  
4. 回應訊息，將使用 vPrev SAP 配接器，以產生使用 WCF 為基礎的結構描述產生的結構描述的對應[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。  
  
   1. 將 BizTalk 對應工具加入至 BizTalk 專案中。 以滑鼠右鍵按一下 BizTalk 專案，指向**新增**，然後按一下**新項目**。  
  
       在 **加入新項目**對話方塊中，從左窗格中，選取**對應檔**。 從右窗格中，選取**地圖**。 指定對應名稱，例如**ResponseMap.btm**。 按一下 **[加入]**。  
  
   2. 從來源結構描述 窗格中，按一下**開啟來源結構描述**。  
  
   3. 在**BizTalk 型別選擇器**對話方塊方塊中，展開 專案名稱，展開**結構描述**，然後選取以 WCF 為基礎的回應訊息的結構描述[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。 本教學課程中，選取*SAP_Migration.SapBindingSchema*，然後按一下**確定**。  
  
   4. 在 **來源結構描述的根節點**對話方塊中，選取*SD_RFC_CUSTOMER_GETResponse*，然後按一下**確定**。  
  
   5. 從目的結構描述 窗格中，按一下**開啟目的結構描述**。  
  
   6. 在**BizTalk 型別選擇器**對話方塊方塊中，展開 專案名稱，展開**結構描述**，然後選取 vPrev SAP 配接器的回應訊息的結構描述。 本教學課程中，選取*SAP_Migration.SD_RFC_CUSTOMER_GET__x32003*，然後按一下**確定**。  
  
   7. 在 **目標結構描述的根節點**對話方塊中，選取*SD_RFC_CUSTOMER_GET_Response*，然後按一下**確定**。  
  
   8. 對應在這兩個結構描述中的個別項目，如下圖所示。  
  
       ![對應的回應訊息，配接器版本之間](../../adapters-and-accelerators/adapter-sap/media/d8dddaba-d978-4159-bcc6-6a6bfee36564.gif "d8dddaba-d978-4159-bcc6-6a6bfee36564")  
  
   9. 儲存對應。  
  
5. 儲存並建置 BizTalk 方案。 以滑鼠右鍵按一下方案，然後按一下**建置方案**。  
  
6. 部署該方案。 以滑鼠右鍵按一下方案，然後按一下**部署方案**。  
  
## <a name="next-steps"></a>後續步驟  
 建立 Wcf-custom 傳送埠，並將它設定為使用您在此步驟中，建立的對應中所述[步驟 2： 在 BizTalk Server 管理主控台設定協調流程](../../adapters-and-accelerators/adapter-sap/step-2-configure-the-orchestration-in-biztalk-server-administration-console1.md)。  
  
## <a name="see-also"></a>另請參閱  
 [教學課程 2：移轉 SAP RFC BizTalk 專案](../../adapters-and-accelerators/adapter-sap/tutorial-2-migrating-an-sap-rfc-biztalk-project.md)