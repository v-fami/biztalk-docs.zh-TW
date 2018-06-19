---
title: 建立 BizTalk Server 協調流程 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 16c637ae-f94f-40f8-8ce7-73a7b7df9f8f
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d6223ab8d8aa3c8d1c20559a88257dd0dccaa22e
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
ms.locfileid: "26008978"
---
# <a name="create-a-biztalk-server-orchestration"></a>建立 BizTalk Server 協調流程
> [!NOTE]
>  本教學課程僅適用於 BizTalk Server。  
  
 建立一個 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 協調流程，在部署時，接收 JSON 訂單訊息，並將其轉換為 XML 發票，再傳送出 JSON 發票。  
  
## <a name="define-message-and-message-types"></a>定義訊息及訊息類型  
 此方案適用於兩個基本訊息，也就是訂單及發票。 我們已經使用 JSON 結構描述精靈從 JSON 訊息產生了訂單結構描述。 本教學課程提供的範例已具備發票訊息的結構描述。 我們使用這些結構描述在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 應用程式中建立訊息類型。  
  
1.  在 BizTalk 專案中新增協調流程，並開啟協調流程檢視。  
  
2.  在協調流程檢視中，以滑鼠右鍵按一下**訊息**，然後按一下 **新訊息**。  
  
3.  以滑鼠右鍵按一下新建立的訊息，然後選取**屬性 視窗**。  
  
4.  在**屬性**窗格**Message_1**，執行下列動作：  
  
    |使用|動作|  
    |--------------|----------------|  
    |識別碼|輸入 `PurchaseOrder`|  
    |訊息類型|從下拉式清單中，展開 **結構描述**，然後選取*BTSJSO。PO*，其中*BTSJSO*是您的 BizTalk 專案的名稱。|  
  
5.  重覆上述步驟為發票訊息建立新的訊息類型。 在**屬性**窗格新訊息中，執行下列動作：  
  
    |使用|動作|  
    |--------------|----------------|  
    |識別碼|輸入 `InvoiceMsg`|  
    |訊息類型|從下拉式清單中，展開 **結構描述**，然後選取*BTSJSO。發票*。|  
  
## <a name="set-up-the-orchestration"></a>設定協調流程  
 在這個步驟中，您會新增訊息圖形以及連接埠來建立協調流程。  
  
### <a name="add-message-shapes"></a>新增訊息圖形  
 從 [方案總管] 中開啟協調流程檔案，並新增下列訊息圖形。  
  
-   新增 「 接收 」 圖形，將其名稱設**ReceivePO**，訊息類型來**PurchaseOrder**。  
  
-   新增 「 傳送 」 圖形，將其名稱設**SendInvoice**，訊息類型來**InvoiceMsg**。  
  
-   新增 [建構訊息圖形，並設定**建構的訊息**屬性建構訊息] 圖形的**InvoiceMsg**。  
  
-   在建構訊息圖形中，新增轉換圖形。 按兩下 「 轉換 」 圖形和**轉換組態**對話方塊中，選取**現有對應**選項，然後再選取**BTSJSO。Testmap**對應。 此對應為範例的一部分。 在對話方塊中，設定**來源**至**PurchaseOrder**並設定**目的地**至**InvoiceMsg**。 按一下 **[確定]**。  
  
### <a name="add-ports"></a>新增連接埠  
 在協調流程中新增兩個連接埠，一個供接收訊息用，另一個供傳送訊息用。 使用連接埠的下列屬性。  
  
|通訊埠|屬性|  
|----------|----------------|  
|MessageIn|-設定**識別碼**至*ReceiveJSONPO*<br />-設定**通訊模式**至*單向*<br />-設定**通訊方向**至*接收*|  
|ResponseOut|-設定**識別碼**至*SendJSONInvoice*<br />-設定**通訊模式**至*單向*<br />-設定**通訊方向**至*傳送*|  
  
 連接連接埠和訊息圖形，如以下螢幕擷取畫面所示，再儲存專案的變更。  
  
 ![處理 JSON 訊息的協調流程](../core/media/btsjson-orchestration.png "BTSJSON_Orchestration")  
  
## <a name="see-also"></a>請參閱  
 [使用 BizTalk Server 處理 JSON 訊息](../core/processing-json-messages-using-biztalk-server.md)