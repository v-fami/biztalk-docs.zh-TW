---
title: （適用於 Azure) 的步驟 2： 建立 EDI 協議 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a8003697-4955-45c0-ba0b-e7c293a050a2
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bc2db7361aef663c70c7227febfea5fc08dc699a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22280070"
---
# <a name="step-2-for-azure-create-an-edi-agreement"></a>（適用於 Azure) 的步驟 2： 建立 EDI 協議
在本主題中，您將建立使用 Azure BizTalk 入口網站可做為夥伴的一部分[!INCLUDE[appfabricintegration](../includes/appfabricintegration-md.md)]。 您也會建立兩個夥伴 （Northwind 和 Contoso） 來處理的 X12 銷售訂單訊息傳送至 Northwind 的 contoso 之間的協議。  
  
### <a name="to-create-partners"></a>若要建立夥伴  
  
1.  使用您的 Microsoft 帳戶，登入入口網站， [http://go.microsoft.com/fwlink/p/?LinkId=235056](http://go.microsoft.com/fwlink/p/?LinkId=235056)。  
  
2.  建立 Northwind 的合作夥伴。 請依照下列步驟[夥伴和設定檔](http://msdn.microsoft.com/library/windowsazure/hh689791)建立夥伴。  
  
    > [!IMPORTANT]
    >  將標示為受管理夥伴此夥伴。  
  
3.  重複步驟，建立 contoso 交易夥伴。 ***不這麼做***標示為受管理夥伴此夥伴。  
  
### <a name="to-create-an-agreement"></a>建立協議  
  
1.  在入口網站的首頁上，按一下**協議**。  
  
2.  在**協議**頁面上，按一下**X12**索引標籤上，如果您已不在該索引標籤上。然後按一下 **建立協議**。  
  
3.  在**新協議**頁面上，輸入下列詳細資料：  
  
    |||  
    |-|-|  
    |**欄位**|**說明**|  
    |名稱|輸入協議的名稱。 此教學課程中，將名稱指定為`DemoAgreement`。<br /><br /> **注意：** 這是必要欄位。 協議的名稱必須是唯一的。|  
    |Description|輸入附註或針對協議的描述。|  
    |夥伴 1 設定檔 (managed)|選取受管理的夥伴協議。 受管理的夥伴是由服務提供者管理，而且合約部署期間為該合作夥伴部署管線。 企業夥伴未標示為受管理夥伴時，服務提供者所管理的夥伴一般是設定為受管理夥伴。<br /><br /> **注意：** 此教學課程中，受管理的夥伴是**Northwind**。<br /><br /> **注意：** 的預設設定檔會顯示在 [設定檔] 欄位。 選擇所需的設定檔已設定為夥伴。|  
    |2 的夥伴設定檔|選取的夥伴協議 （使用者不受管理的夥伴）。<br /><br /> **注意：** 的預設設定檔會顯示在 [設定檔] 欄位。 選擇所需的設定檔已設定為夥伴。|  
  
     **身分識別**  
  
    |**欄位**|**說明**|  
    |---------------|---------------------|  
    |1 合作夥伴 ID 限定詞|提供驗證限定詞，來為交易夥伴提供唯一的商務識別。 此教學課程中，選取**ZZ 使用者相互定義**。|  
    |值|輸入`Northwind`。|  
    |2 合作夥伴 ID 限定詞|提供驗證限定詞，來為交易夥伴提供唯一的商務識別。 此教學課程中，選取**ZZ 使用者相互定義**。|  
    |值|輸入`Contoso`。|  
  
     **追蹤**  
  
    |**欄位**|**說明**|  
    |---------------|---------------------|  
    |追蹤傳送端訊息屬性|勾選這 EDI 訊息傳送到夥伴時儲存訊息屬性。 一旦儲存之後，您可以查詢此資料，即可**追蹤**從在 Azure BizTalk 入口網站的左窗格。<br /><br /> 啟用時，您可以藉由檢查也儲存訊息主體**追蹤傳送端訊息內文**。|  
    |追蹤接收端訊息屬性|勾選這從夥伴接收 EDI 訊息時儲存訊息屬性。 一旦儲存之後，您可以查詢此資料，即可**追蹤**從在 Azure BizTalk 入口網站的左窗格。<br /><br /> 啟用時，您可以藉由檢查也儲存訊息主體**追蹤接收端訊息內文**。|  
  
4.  按一下 **[繼續]**。  
  
     按一下**繼續**加入兩個新的索引標籤，一個用於接收設定，而另一個用於傳送設定。 每個索引標籤是一個用於接收訊息，另一個用於傳送訊息的兩個夥伴之間的單向協議。  
  
5.  指定的接收設定。  
  
    1.  在**傳輸**頁面上，設定**傳輸類型**為 HTTP。  
  
         **端點**欄位會顯示 URL，Contoso 必須將 X12 銷售訂單訊息。  
  
    2.  在**通訊協定**頁面上，指定下列值。  
  
        1.  如有需要，請為 ISA1、 ISA2、 ISA3 和 ISA4 中指定值。  
  
        2.  在下**通知**，選取**預期 TA1**和**997 預期**如果您想要接收的回應中產生技術性和功能性通知訊息。  
  
        3.  在下**結構描述**，按一下 **上傳**按鈕，然後上傳**X12 840 結構描述**(從您下載[http://go.microsoft.com/fwlink/p/?LinkId = 235057](http://go.microsoft.com/fwlink/p/?LinkId=235057)) 和**SalesOrder**結構描述 (您在建立[建立 EDI 專案中的結構描述](../core/step-1-for-azure-create-the-edi-project.md#BKMK_CreateSchema))。  
  
             設定下列屬性下的**結構描述**> 一節。  
  
            |||  
            |-|-|  
            |Version|00401|  
            |交易類型 (ST1)|840|  
            |結構描述|/ X12_00401_840.xsd|  
  
    3.  在**轉換**頁面上上, 傳您在建立轉換[建立 EDI 專案中的轉換](../core/step-1-for-azure-create-the-edi-project.md#BKMK_CreateTrfm)。  
  
         在下**選擇您想要當做此協議的一部分執行的對應**，選擇 **/X12_00401_840.xsd**如**結構描述**和 **/EDI840TOSALESORDER。TRFM**如**轉換檔名稱**。  
  
    4.  在**路由**頁面上，選取**路由至服務匯流排佇列**並提供的佇列傳送訊息的相對位址。 此教學課程中，指定相對位址，表示為`queueordersedi`使的完整 URL `https://<namespace>.servicebus.appfabriclabs.com/queueordersedi`。  
  
        > [!NOTE]
        >  此教學課程未涵蓋失敗的訊息的傳送目標端點您的案例中訊息暫停設定所指定。 不過，才能順利部署協議，您必須提供值，此設定。 您可以輸入非空白值。  
  
6.  指定傳送設定。  
  
    > [!NOTE]
    >  對於此教學課程中所述的案例，您不需要任何協議的傳送端設定。 不過，協議無法部署而不指定傳送設定 中，即使它們是空的值。 此外，在**傳送設定**索引標籤上，您不需要提供的任何空值**輸入 URI**，**轉換**，和**批次處理**。  
  
    1.  上**通訊協定**頁面的 **結構描述**，按一下**上傳**按鈕，然後上傳結構描述 x12 840 訊息。  
  
         設定**版本**至**00401**，**交易類型**至**840**，和**結構描述**至**X12_00401_840**。  
  
    2.  在**傳輸**頁面上，指定在回應訊息或通知會傳送至夥伴的端點。 您必須指定的端點，每個已成功處理的訊息，以及取得因處理失敗而擱置的訊息。  
  
7.  按一下**部署協議**部署合約。 協議現在部署於 URL 中原先顯示**傳輸**頁面**接收設定** 索引標籤。  
  
## <a name="see-also"></a>另請參閱  
 [教學課程 4： 建立使用 BizTalk Server 2013 的混合式應用程式](../core/tutorial-4-creating-a-hybrid-application-using-biztalk-server-2013.md)