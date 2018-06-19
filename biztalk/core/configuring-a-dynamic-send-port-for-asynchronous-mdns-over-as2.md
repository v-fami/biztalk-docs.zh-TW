---
title: 設定透過 AS2 之非同步 Mdn 的動態傳送埠 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 72646c90-89db-4884-824b-6921bb824f8d
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 754917ed1a089e3182c8543e8a132a9eff73615e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22233446"
---
# <a name="configuring-a-dynamic-send-port-for-asynchronous-mdns-over-as2"></a>設定透過 AS2 之非同步 MDN 的動態傳送埠
若要透過 HTTP/HTTPS 傳送非同步的 EDIINT/AS2 編碼 MDN 訊息，請建立包含下列組態的動態 HTTP 傳送埠：  
  
|位置|屬性|設定|  
|--------------|--------------|-------------|  
|**傳送埠屬性： 一般**|連接埠類型|動態單向|  
|**傳送埠屬性： 一般**|傳送管線|AS2Send|  
|**傳送埠屬性： 篩選**|屬性|EdiIntAS.IsAS2AsynchronousMdn|  
|**傳送埠屬性： 篩選**|運算子|==|  
|**傳送埠屬性： 篩選**|值|True|  
  
 非同步 MDN 應傳送中包含的位址至**回條傳遞選項**收到的 AS2 訊息的標頭。 動態傳送埠會這樣做，然而靜態傳送埠將訊息傳送到**目的地 URL**傳送連接埠定義中。 這個例外狀況是如果**對驗證與 MDN 使用協議設定，而非訊息標頭**屬性設定**驗證**單向協議索引標籤的頁面**協議屬性** 對話方塊。 在此情況下，傳送埠將 MDN 訊息傳送至的 URL 輸入到**回條傳遞選項**協議屬性。 不過，用來執行這項處理的傳送埠仍然必須屬於動態傳送埠，而不能是靜態傳送埠。  
  
 您可以設定這個傳送埠，使 MDN 和 EDI 通知都可傳回。 在這個執行個體中，如果 EDIINT/AS2 編碼訊息已成功透過 HTTP/HTTPS 完成傳輸，但是 EDI 編碼內容的處理作業失敗，這時原始訊息的傳送者將會同時收到 MDN 和 EDI 通知，前者指出 AS2 處理成功，後者則指出 EDI 處理失敗。 系統將會擱置 EDI 編碼內容，並發佈錯誤。  
  
## <a name="functionality"></a>功能  
 傳送埠和管線必須執行下列動作，才能傳送 MDN：  
  
-   根據 `EdiIntAS.IsAS2AsynchronousMdn==True` 屬性進行篩選，以便收取該 MDN。  
  
-   建置 AS2 訊息。 如需此程序的詳細資訊，請參閱[產生外寄 AS2 訊息](../core/generating-an-outgoing-as2-message.md)。  
  
-   中的位址，將 MDN 路由**回條傳遞選項**訊息標頭中的一行。  
  
    > [!NOTE]
    >  如果**對驗證與 MDN 使用協議設定，而非訊息標頭**屬性設定**驗證**單向協議索引標籤的頁面**協議屬性**對話方塊中，傳送埠將 MDN 訊息傳送至的 URL 輸入到**回條傳遞選項**協議屬性，而不以解決**回條傳遞選項**收到的 AS2 訊息的標頭。  
  
## <a name="see-also"></a>另請參閱  
 [設定 AS2 方案的連接埠](../core/configuring-ports-for-an-as2-solution.md)