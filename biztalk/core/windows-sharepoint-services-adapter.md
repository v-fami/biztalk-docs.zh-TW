---
title: Windows SharePoint Services 配接器 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Windows SharePoint Services adapters
ms.assetid: cbfc9bf3-912d-4849-ba8c-07a116888bbd
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5a6f1365b11ce93717223ec35e395165e8d0e551
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22289878"
---
# <a name="windows-sharepoint-services-adapter"></a>Windows SharePoint Services 配接器
Microsoft Windows SharePoint Services 的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 配接器為 BizTalk Server 與 Windows SharePoint Services 和 Microsoft Office 提供更緊密的整合。 在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 解決方案中使用 Windows SharePoint Services 配接器，可提供您下列功能：  
  
-   透過 Windows SharePoint Services 輕鬆存取輸入和輸出訊息。  
  
-   使用 Microsoft Office InfoPath 等 Office 應用程式來編輯 XML 訊息的功能。  
  
-   在 XML 訊息與 InfoPath 間進行雙向轉換。  
  
 [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] 配接器包含下列元件：  
  
|||  
|-|-|  
|CSOM[!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)]配接器|使用 [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] Client Side Object Model (CSOM)。 此配接器會在安裝 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 時一併安裝。 不需執行其他安裝步驟。<br /><br /> [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]安裝***自動***安裝 SharePoint 用戶端物件模型可轉散發套件，這也是位於[http://go.microsoft.com/fwlink/p/?LinkId=263482](http://go.microsoft.com/fwlink/p/?LinkId=263482)。|  
|SSOM [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] Web 服務|**已取代**。 使用 [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] Service Side Object Model (SSOM)。<br /><br /> 此 Web 服務安裝於 [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] 電腦上，可以在與 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 相同的電腦或個別電腦上。<br /><br /> 若要安裝 web 服務，請執行[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]上的安裝[!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)]電腦並檢查**Windows SharePoint Services 配接器**。|  
  
 [附錄 b： 安裝 Microsoft SharePoint 配接器](../install-and-config-guides/appendix-b-install-the-microsoft-sharepoint-adapter.md)提供更多有關[!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)]安裝。  
  
> [!NOTE]
>  目前不支援同盟驗證。 只支援使用者名稱和密碼。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [CSOM: SharePoint Services 配接器](../core/csom-sharepoint-services-adapter.md)  
  
-   [SSOM: SharePoint Services 配接器 Web 服務](../core/ssom-sharepoint-services-adapter-web-service.md)  
  
## <a name="see-also"></a>另請參閱  
 [使用配接器](../core/using-adapters.md)   
 [開發 BizTalk Server 應用程式](../core/developing-biztalk-server-applications.md)