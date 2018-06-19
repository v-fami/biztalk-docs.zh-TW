---
title: 主要功能在 Siebel 配接器 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- features, performance-related
- adapter features, new
- features, technology-related
- features, metadata-related
- adapter features, operations-related
- adapter features, performance-related
- features, new
- features, operations-related
- adapter features, metadata-related
ms.assetid: 4612c9ab-810e-4c69-9168-a25c58682e71
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 295ff8b13358109a5d4737fb5f9325b3c9caa0f8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22222126"
---
# <a name="key-features-in-the-siebel-adapter"></a>Siebel 配接器中的主要功能
此區段會列出中的新功能[!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)]。  
  
> [!NOTE]
>  本主題已經使用舊版的[!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)]幫助。  
  
## <a name="new-features-in-the-siebel-adapter"></a>Siebel 配接器的新功能  
 以下是在此版本中引進的新功能[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]。  
  
### <a name="technology-related-features"></a>技術相關功能  
  
|功能|註解|  
|-------------|-------------|  
|支援使用[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]與 Microsoft Office SharePoint Server (MOSS)|您可以使用配接器呈現來自 Siebel 系統到 MOSS 入口網站上的資料。 如需詳細資訊，請參閱[Siebel 配接器使用 Microsoft Office SharePoint Server](https://msdn.microsoft.com/library/dd788017.aspx)。|  
  
### <a name="operations-related-features"></a>與作業相關的功能  
  
|功能|註解|  
|-------------|-------------|  
|支援商務元件上的相關作業|配接器用戶端可以建立關聯，藉由指定搜尋運算式的父記錄和子記錄。 這只適用於多重值的群組 (MVG) 欄位的商務元件。 請注意，搜尋運算式應該篩選父和下層業務元件的完全一筆記錄。|  
|商務元件上的 DISASSOCIATE 作業的支援|藉由指定搜尋運算式的父記錄和子記錄，可以中斷關聯配接器用戶端。 這只適用於多重值的群組 (MVG) 欄位的商務元件。 請注意，搜尋運算式必須篩選父和下層業務元件的完全一筆記錄。|  
|支援多重值連結查詢|配接器用戶端可以查詢藉由指定的父記錄和多重值的欄位名稱與父記錄相關聯之子記錄。 這只適用於多重值的群組 (MVG) 欄位的商務元件。|  
  
### <a name="other-features"></a>其他功能  
  
|功能|註解|  
|-------------|-------------|  
|使用中的配接器的新方法[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]|[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]可用於 BizTalk 作為 WCF 自訂連接埠或 Wcf-siebel 連接埠。 如果您想要使用[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]透過 WCF 自訂連接埠，您不需要新增 WCF 自訂連接埠[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台，因為 WCF 自訂連接埠新增到[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]預設的管理主控台。 不過，如果您想要使用[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]透過 Wcf-siebel 連接埠，您必須先新增 Wcf-siebel 配接器[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。 如需詳細資訊，請參閱[新增 Siebel 配接器至 BizTalk Server 管理主控台](../../adapters-and-accelerators/adapter-siebel/add-the-siebel-adapter-to-biztalk-server-administration-console.md)。|  
  
## <a name="see-also"></a>另請參閱  
 [瞭解 BizTalk Adapter for Siebel eBusiness 應用程式](../../adapters-and-accelerators/adapter-siebel/understand-biztalk-adapter-for-siebel-ebusiness-applications.md)