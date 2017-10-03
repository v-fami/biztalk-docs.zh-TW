---
title: "使用 WCF 服務 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF services
- Windows Communication Foundation (WCF)
ms.assetid: 34fe5e4c-6a92-4627-b2aa-e8b58a708320
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 29b984bcda798796565113739c6088af6d569f7c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="using-wcf-services"></a>使用 WCF 服務
Microsoft[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]提供內建支援的 Windows Communication Foundation (WCF)。 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]可讓您重複使用和彙總所有現有的 WCF 服務協調流程中。 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]也實作 WCF 服務中原生配接器的支援。 原生配接器支援為 WCF 服務提供擴充性、容錯和追蹤功能，您無須撰寫任何程式碼。 WCF 配接器的相關資訊，請參閱[WCF 配接器](../core/wcf-adapters.md)。  
  
 WCF 服務中的支援[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]分為兩類： 發行或建立 WCF 服務，或呼叫或取用 WCF 服務。  
  
 **發佈 WCF 服務**  
  
 您可以使用 WCF 配接器將協調流程和結構描述發佈 (公開) 為 WCF 服務，以區隔 WCF 服務邏輯與商務程序邏輯。 針對外掛式 WCF 配接器，您可以使用 BizTalk WCF 服務發佈精靈建立由 Internet Information Services (IIS) 中執行的 Web 應用程式主控的外掛式 WCF 接收位置。 針對內建 WCF 配接器，您可以使用 BizTalk WCF 服務發佈精靈發佈任何 WCF 位置的服務中繼資料。  發佈中繼資料可允許使用 svcutil.exe 公用程式建立用戶端程式碼。  
  
 **使用 WCF 服務**  
  
 您可以使用 BizTalk WCF 服務使用精靈產生 BizTalk 成品 (例如 BizTalk 協調流程和類型)，使其根據 WCF 服務的中繼資料文件來使用 WCF 服務。 中繼資料可讓傳送埠以用戶端身分存取外部服務。 使用中繼資料純粹是為了描述端點位址、繫結與合約。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [發佈 WCF 服務](../core/publishing-wcf-services.md)  
  
-   [使用 WCF 服務](../core/consuming-wcf-services.md)  
  
-   [指定訊息本文為 WCF 配接器](../core/specifying-the-message-body-for-the-wcf-adapters.md)  
  
-   [WCF 配接器逐步解說](../core/wcf-adapter-walkthroughs.md)