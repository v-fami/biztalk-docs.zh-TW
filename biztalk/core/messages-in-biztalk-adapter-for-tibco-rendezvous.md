---
title: "BizTalk Adapter for TIBCO Rendezvous 中的訊息 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- passing messages
- TIBCO Rendezvous
- messages
- message passing
- messages, passing
ms.assetid: 12699550-22e7-4a11-a024-2302570970af
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f4bc1eadbefdeb5c59df9a1b999ffdd3e530587a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="messages-in-biztalk-adapter-for-tibco-rendezvous"></a>BizTalk Adapter for TIBCO Rendezvous 中的訊息
BizTalk Adapter for TIBCO Rendezvous 提供 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 與 TIBCO Rendezvous 之間的雙向連線。 此配接器同時使用 TIBCO Rendezvous API 與 BizTalk 配接器架構 API 來提供緊密整合。  
  
## <a name="about-tibco-rendezvous"></a>關於 TIBCO Rendezvous  
 TIBCO Rendezvous 軟體產品可為企業應用程式整合 (EAI) 提供訊息匯流排。 TIBCO 可提供 C、C++、Java、Visual Basic 與 Microsoft .NET Framework 的訊息 API 以在 Microsoft Office Excel 工作表與其他自選的應用程式上接收資料摘要。 如需詳細資訊，請參閱[TIBCO Rendezvous 概念](../core/tibco-rendezvous-concepts.md)。  
  
### <a name="message-passing"></a>訊息傳遞  
 訊息傳遞的基本概念相當簡單：  
  
-   訊息包含單一主旨，這個主旨是由以句點分隔的多個項目所組成。 訊息會傳送至單一 Rendezvous 精靈 (但最後會廣播到其他精靈中)。  
  
-   待命程式會向精靈宣告感興趣之主旨 (使用基本萬用字元功能)， 這時如果兩個精靈彼此「互連」或是事實上為同一個精靈時，就會將具有相符主旨的訊息傳遞給該待命程式。  
  
 必要時，會以此為基礎往上發展重要的「企業」功能 (容錯/可靠或認證選項)：一切都是透過基礎的基本訊息來實作。  
  
 訊息本身可以視為具型別的名稱值欄位或是數字值欄位 (訊息中的這兩種識別機制可互相混合使用以符合特定限制)。 訊息本身可以包含子訊息，其中又可以包含更多子訊息。  
  
 主旨名稱包含一或多個以點字元 (句點) 分隔的元素。 這些元素會實作主旨名稱階層來反映應用程式系統中的資訊結構。 下列字串是有效主旨名稱的範例：  
  
-   RUN.HOME  
  
-   RUN.for.Elected_Office  
  
 BizTalk Adapter for TIBCO Rendezvous 透過 TIBCO Rendezvous SDK 將訊息發佈至 TIBCO Rendezvous 主旨，以及註冊接收 TIBCO Rendezvous 事件。 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 相關類別會裝載在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 電腦中。 另一個處理序 (執行階段代理程式) 會啟動並以 Rendezvous 程式形式運作，兩者之間會使用 .NET Framework 遠端處理來交換訊息。  
  
-   資訊層級、警告層級與錯誤層級的訊息會傳送至 Windows 事件日誌。  
  
-   所有層級 (包括偵錯層級) 的訊息都會傳送至 Windows 追蹤記錄檔。  
  
#### <a name="transmitter"></a>傳輸器  
 BizTalk Adapter for TIBCO Rendezvous 會針對每個傳送埠各啟動一個執行階段代理程式。 TIBCO Rendezvous .NET Framework API 只允許設定全域範圍的字元編碼。 因此，其中一項連接埠組態選項會是字碼頁編號。 透過針對每個字碼頁啟動不同的程序，配接器可以提供更好的全球化支援。  
  
#### <a name="receiver"></a>接收器  
 BizTalk Adapter for TIBCO Rendezvous 會啟動一個執行階段代理程式每個接收位置。  
  
#### <a name="transactions"></a>交易  
 TIBCO Rendezvous 產品非交易式產品。 若要執行交易，需要使用另一個產品 TIBCO Rendezvous TX。 此版本的 BizTalk Adapter for TIBCO Rendezvous 不支援交易。  
  
#### <a name="security"></a>安全性  
 TIBCO Rendezvous 僅支援 TIBCO Rendezvous 程式與精靈之間的驗證。 它不會執行授權或加密。 若要執行授權或加密，需要使用另一個產品 TIBCO Rendezvous DataSecurity。  
  
## <a name="see-also"></a>另請參閱  
 [TIBCO Rendezvous 概念](../core/tibco-rendezvous-concepts.md)   
 [快速入門](../core/getting-started-with-biztalk-adapter-for-tibco-rendezvous.md)