---
title: 步驟 1： 叫用 RFC 修改 vPrev BizTalk 專案 |Microsoft 文件
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
ms.openlocfilehash: d1f967a268d8baca3ab12f29bbac4b9eccc3cd75
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22218102"
---
# <a name="step-1-modify-the-vprev-biztalk-project-for-invoking-an-rfc"></a>步驟 1： 叫用 RFC 修改 vPrev BizTalk 專案
![步驟 3 之 1](../../adapters-and-accelerators/adapter-oracle-database/media/step-1of3.gif "Step_1of3")  
  
 **若要完成的時間：** 10 分鐘  
  
 **目標：** 在此步驟中，您必須進行下列變更現有 vPrev BizTalk 專案：  
  
-   產生使用 WCF 型 SD_RFC_CUSTOMER_GET RFC 的中繼資料[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。  
  
-   叫用使用 vPrev SAP 配接器的要求訊息來叫用使用 WCF 為基礎的 RFC RFC 的要求訊息對應[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。  
  
-   使用 WCF 為基礎所接收的回應訊息對應[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]vPrev SAP 配接器的回應訊息。  
  
## <a name="prerequisite"></a>必要條件  
  
-   您必須在 SAP 系統中叫用 SD_RFC_CUSTOMER_GET RFC vPrev BizTalk 專案。  
  
### <a name="to-modify-the-vprev-biztalk-project"></a>若要修改 vPrev BizTalk 專案  
  
1.  產生使用 WCF 型 SD_RFC_CUSTOMER_GET RFC 的中繼資料[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。 您可以使用[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]產生中繼資料。  
  
     如需有關如何產生 rfc 的中繼資料的指示，請參閱[瀏覽、 搜尋和 get 中繼資料中 SAP RFC 作業的](../../adapters-and-accelerators/adapter-sap/browse-search-and-get-metadata-for-rfc-operations-in-sap.md)。 結構描述產生之後，類似於名稱的檔案*SapBindingSchema.xsd*會加入至 BizTalk 專案。 這個檔案包含的結構描述叫用使用 WCF 型 SD_RFC_CUSTOMER_GET [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。  
  
2.  產生 SD_RFC_CUSTOMER_GET RFC 的中繼資料時，也會建立連接埠繫結檔案。 在下一個步驟中，此繫結檔案，將用來建立 Wcf-custom 傳送埠將訊息傳送至 SAP 系統中。 作業的 SOAP 動作也會設為您產生的中繼資料作業。 比方說，如果您的 SD_RFC_CUSTOMER_GET RFC 產生中繼資料，傳送埠上的 SOAP 動作中的作業名稱會"SD_RFC_CUSTOMER_GET"。 不過，作業名稱的協調流程的一部分，例如可能不同，您建立邏輯傳送連接埠上"Operation_1"。 如此一來，當您傳送訊息至 SAP 系統使用的傳送埠時，您會收到錯誤。 若要防止這個情況，請確定在邏輯上的作業名稱的傳送埠協調流程中的產生的中繼資料的作業名稱相同。  
  
     因此，在此教學課程中，產生 SD_RFC_CUSTOMER_GET RFC 的中繼資料，因為變更名稱"SD_RFC_CUSTOMER_GET"的邏輯傳送連接埠作業。  
  
3.  要求訊息時，將使用 vPrev SAP 配接器使用 WCF 為基礎所產生的結構描述產生的結構描述的對應[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。  
  
    1.  將 BizTalk 對應工具加入至 BizTalk 專案。 以滑鼠右鍵按一下 BizTalk 專案，指向**新增**，然後按一下 **新項目**。  
  
         在**加入新項目**對話方塊的左窗格中，選取**對應檔**。 從右窗格中，選取**對應**。 指定對應名稱，例如**RequestMap.btm**。 按一下 **[加入]**。  
  
    2.  從來源結構描述] 窗格中，按一下 [**開啟來源結構描述**。  
  
    3.  在**BizTalk 型別選擇器**對話方塊方塊中，展開 專案名稱，展開**結構描述**，並選取 vPrev SAP 配接器的要求訊息的結構描述。 此教學課程中，選取*SAP_Migration.SD_RFC_CUSTOMER_GET__x32003*，然後按一下 **確定**。  
  
    4.  在**來源結構描述的根節點**對話方塊中，選取*SD_RFC_CUSTOMER_GET_Request*，然後按一下 **確定**。  
  
    5.  從 目的結構描述 窗格中，按一下 **開啟目的結構描述**。  
  
    6.  在**BizTalk 型別選擇器**對話方塊方塊中，展開 專案名稱，展開**結構描述**，並選取以 WCF 為基礎的要求訊息的結構描述[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。 此教學課程中，選取*SAP_Migration.SapBindingSchema*，然後按一下 [確定]。  
  
    7.  在**目標結構描述的根節點**對話方塊中，選取*SD_RFC_CUSTOMER_GET*，然後按一下 **確定**。  
  
         對應的結構描述中的個別項目，如下圖所示。 對應 CUSTOMER_T 項目使用字串左空白位置修剪運算質。 若要這樣做，請從**工具箱**，拖曳**字串左空白位置修剪**運算質放在對應工具格線。 連接**CUSTOMER_T** 」 運算質來源結構描述中的項目。 同樣地，連接**CUSTOMER_T**運算質至目的結構描述中的項目。 下圖說明如何透過運算質對應兩個項目。  
  
         ![對應配接器版本之間的要求訊息](../../adapters-and-accelerators/adapter-sap/media/f12f280d-766f-4647-bced-435354206fb9.gif "f12f280d-766f-4647-bced-435354206fb9")  
  
        > [!NOTE]
        >  字串左空白位置修剪運算質的詳細資訊，請參閱 「 字串左空白位置修剪運算質 」，網址[http://go.microsoft.com/fwlink/?LinkId=105774](http://go.microsoft.com/fwlink/?LinkId=105774)。  
  
    8.  儲存對應。  
  
4.  回應訊息時，將使用 vPrev SAP 配接器使用 WCF 為基礎所產生的結構描述產生的結構描述的對應[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。  
  
    1.  將 BizTalk 對應工具加入至 BizTalk 專案。 以滑鼠右鍵按一下 BizTalk 專案，指向**新增**，然後按一下**新項目**。  
  
         在**加入新項目**對話方塊的左窗格中，選取**對應檔**。 從右窗格中，選取**對應**。 指定對應名稱，例如**ResponseMap.btm**。 按一下 **[加入]**。  
  
    2.  從來源結構描述] 窗格中，按一下 [**開啟來源結構描述**。  
  
    3.  在**BizTalk 型別選擇器**對話方塊方塊中，展開 專案名稱，展開**結構描述**，並選取以 WCF 為基礎的回應訊息的結構描述[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。 此教學課程中，選取*SAP_Migration.SapBindingSchema*，然後按一下 **確定**。  
  
    4.  在**來源結構描述的根節點**對話方塊中，選取*SD_RFC_CUSTOMER_GETResponse*，然後按一下 **確定**。  
  
    5.  從 目的結構描述 窗格中，按一下 **開啟目的結構描述**。  
  
    6.  在**BizTalk 型別選擇器**對話方塊方塊中，展開 專案名稱，展開**結構描述**，並選取 vPrev SAP 配接器的回應訊息的結構描述。 此教學課程中，選取*SAP_Migration.SD_RFC_CUSTOMER_GET__x32003*，然後按一下 **確定**。  
  
    7.  在**目標結構描述的根節點**對話方塊中，選取*SD_RFC_CUSTOMER_GET_Response*，然後按一下 **確定**。  
  
    8.  對應的結構描述中的個別項目，如下圖所示。  
  
         ![對應配接器版本之間的回應訊息](../../adapters-and-accelerators/adapter-sap/media/d8dddaba-d978-4159-bcc6-6a6bfee36564.gif "d8dddaba-d978-4159-bcc6-6a6bfee36564")  
  
    9. 儲存對應。  
  
5.  儲存並建置 BizTalk 方案。 以滑鼠右鍵按一下方案，然後按一下**建置方案**。  
  
6.  部署該方案。 以滑鼠右鍵按一下方案，然後按一下**部署方案**。  
  
## <a name="next-steps"></a>後續步驟  
 建立 Wcf-custom 傳送埠，並將它設定為使用您在此步驟中，建立的對應中所述[步驟 2： 在 BizTalk Server 管理主控台中設定協調流程](../../adapters-and-accelerators/adapter-sap/step-2-configure-the-orchestration-in-biztalk-server-administration-console1.md)。  
  
## <a name="see-also"></a>另請參閱  
 [教學課程 2： 移轉 SAP RFC BizTalk 專案](../../adapters-and-accelerators/adapter-sap/tutorial-2-migrating-an-sap-rfc-biztalk-project.md)