---
title: "使用 Web 服務 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Web services
- Web services, about Web services
- orchestrations, Web services
- Web services, orchestrations
ms.assetid: a54261e3-d8ef-4770-8d9a-147685846051
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 236acb42c010effe5c3d45cde1daaf9a7097ede5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="using-web-services"></a>使用 Web 服務
Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 提供了 Web 服務的內建支援。 BizTalk Server 可讓您重複使用及彙總協調流程中的所有現有 Web 服務。 您也可以將協調流程發佈 (公開) 為 Web 服務，以區隔 Web 服務邏輯與商務程序邏輯。  
  
 BizTalk Server 實作了 Web 服務原生配接器的支援。 原生配接器支援提供 Web 服務的擴充性、容錯和追蹤功能，且無須撰寫任何程式碼。 SOAP 配接器的相關資訊，請參閱[SOAP 配接器](../core/soap-adapter.md)。  
  
 在 BizTalk Server 中的 Web 服務支援分為兩類： 使用或呼叫 Web 服務以及發佈或建立 Web 服務。  
  
 使用或發佈 Web 服務之前，您應該先瞭解 ASP.NET 中的 XML Web Service。 XML Web 服務的基本概念的相關資訊，請參閱文章 < XML Web 服務基本概念 >，網址[http://go.microsoft.com/fwlink/?LinkId=193057](http://go.microsoft.com/fwlink/?LinkId=193057)。  
  
 **使用 Web 服務**  
  
 您可以從協調流程內使用 (呼叫) Web 服務。 您可以彙總以完成整個商務程序的單一協調流程數個 Web 服務。  
  
 **發佈 Web 服務**  
  
 您可以使用 [BizTalk Web 服務發佈精靈] 來發佈 Web 服務。 協調流程和傳送配接器可以使用這些已發佈的 Web 服務。  
  
 **使用 SOAP 標頭**  
  
 BizTalk Server 提供已定義的和未知的 SOAP 標頭支援。 BizTalk Server 會為 Web 服務內每個已定義的 SOAP 標頭建立內容屬性。  
  
 **Web 服務標準**  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]應該與任何 Web 服務標準，在傳送和接收合作。 並非所有的標準已經過測試。 一般而言，透過 WCF 支援的標準也支援[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。 標準範例包括：  
  
-   Ws-reliablemessaging  
  
-   WS-Security  
  
-   Ws-secureconversation  
  
-   Ws-trust  
  
-   WS-同盟  
  
-   WS-Addressing  
  
-   WS 原則  
  
-   Ws-metadataexchange  
  
-   Ws-coordination  
  
-   Ws-atomic  
  
## <a name="in-this-section"></a>本節內容  
  
-   [使用 Web 服務](../core/consuming-web-services.md)  
  
-   [發佈 Web 服務](../core/publishing-web-services.md)  
  
-   [使用 SOAP 標頭](../core/using-soap-headers.md)