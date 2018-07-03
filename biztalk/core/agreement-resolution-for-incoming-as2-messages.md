---
title: 內送 AS2 訊息的協議解析 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 746d01af-de6a-4d5d-9433-b0e1a2b41861
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 25a464025377eae7fd70992359d3be1582fa748a
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37016726"
---
# <a name="agreement-resolution-for-incoming-as2-messages"></a>內送 AS2 訊息的協議解析
當 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 透過 HTTP/HTTPS 傳輸接收 EDIINT/AS2 編碼訊息時，它會嘗試判斷傳送該訊息的交易夥伴商務設定檔。 它會嘗試執行下列步驟 (順序如下所示) 來進行判斷：  
  
1. 比對內的 AS2-From 的值來將傳入訊息中的標頭**AS2-從**中**識別項**頁面中，單向 AS2 協議**協議屬性**  對話方塊。  
  
2. 如果 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 無法判斷協議，它就會嘗試針對內送訊息所設定的 AS2-From 內容屬性與交易夥伴名稱進行比對。  
  
> [!NOTE]
>  AS2-From 標頭只能包含 ASCII 字元，因此，您必須確認您的交易夥伴名稱與 AS2-From 別名也只包含 ASCII 字元。 如果沒有完全相符的項目，BizTalk 將無法根據內送訊息標頭判斷協議。  
  
 只有在判斷協議之後，AS2 接收管線才會處理訊息。 與 EDI 處理不同的是，當 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 無法判斷協議時，沒有可用的後援 AS2 屬性。  
  
 一旦管線判斷出協議，它會檢查的設定**使用協議設定進行驗證並以 MDN 取代訊息標頭**中的屬性**驗證**頁面的單向 AS2中的協議**協議設定** 對話方塊。 如果該屬性為核取狀態，接收管線會使用該協議屬性來處理訊息。 若該屬性已取消核取，接收管線會使用訊息之 AS2 標頭的值來處理訊息。  
  
> [!NOTE]
>  在協議解析期間所判斷出的 AS2 協議可能與 EDI 內容的協議不同。 AS2 和 EDI 不必共用相同的協議，因為 AS2 協議可能代表從多個合作對象路由 EDI 文件的 Clearinghouse。  
  
 如需接收程序的詳細資訊，請參閱 <<c0> [ 處理內送 AS2 訊息](../core/processing-an-incoming-as2-message.md)。  
  
## <a name="see-also"></a>另請參閱  
 [BizTalk Server 如何接收 AS2 訊息](../core/how-biztalk-server-receives-as2-messages.md)