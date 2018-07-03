---
title: 主要在 Siebel 配接器的功能 |Microsoft Docs
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
ms.openlocfilehash: 4896256555ea6b721d917c992c9c41fd3737f101
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37018325"
---
# <a name="key-features-in-the-siebel-adapter"></a>Siebel 配接器中的主要功能
此區段會列出中的新功能[!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)]。  
  
> [!NOTE]
>  本主題已使用的舊版[!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)]幫助。  
  
## <a name="new-features-in-the-siebel-adapter"></a>Siebel 配接器的新功能  
 以下是此版本中引進的新功能[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]。  
  
### <a name="technology-related-features"></a>技術相關功能  
  
|                                                                    功能                                                                     |                                                                                                               註解                                                                                                               |
|------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 支援使用[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]與 Microsoft Office SharePoint Server (MOSS) | 您可以使用配接器，以呈現來自 Siebel 系統到 MOSS 入口網站上的資料。 如需詳細資訊，請參閱 < [Siebel 配接器使用 Microsoft Office SharePoint Server](https://msdn.microsoft.com/library/dd788017.aspx)。 |
  
### <a name="operations-related-features"></a>作業相關的功能  
  
|功能|註解|  
|-------------|-------------|  
|對商務元件的關聯作業的支援|配接器用戶端可以建立關聯，藉由指定搜尋運算式的父記錄和子記錄。 這是僅適用於多重值的群組 (MVG) 欄位的商務元件。 請注意，搜尋運算式應該篩選父和子商務元件只有一個記錄。|  
|取消關聯作業對商務元件的支援|配接器用戶端可以中斷關聯，藉由指定搜尋運算式的父記錄和子記錄。 這是僅適用於多重值的群組 (MVG) 欄位的商務元件。 請注意，搜尋運算式必須篩選父和子商務元件只有一個記錄。|  
|支援多重值連結查詢|配接器用戶端可以查詢藉由指定的父記錄和多重值的欄位名稱相關聯的父記錄的子記錄。 這是僅適用於多重值的群組 (MVG) 欄位的商務元件。|  
  
### <a name="other-features"></a>其他功能  
  
|                                                        功能                                                        |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  註解                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
|-----------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 使用中的配接器的新方式 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] | [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]可用於 BizTalk 做為 WCF 自訂連接埠或 Wcf-siebel 連接埠。 如果您想要使用[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]透過 WCF 自訂連接埠，您不需要新增的 WCF 自訂連接埠[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台，因為 WCF 自訂連接埠新增至[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台中的，預設值。 不過，如果您想要使用[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]透過 Wcf-siebel 連接埠，您必須先新增 Wcf-siebel 配接器[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。 如需詳細資訊，請參閱 < [Siebel 配接器加入 BizTalk Server 管理主控台](../../adapters-and-accelerators/adapter-siebel/add-the-siebel-adapter-to-biztalk-server-administration-console.md)。 |
  
## <a name="see-also"></a>另請參閱  
 [了解 BizTalk Adapter for Siebel eBusiness Applications](../../adapters-and-accelerators/adapter-siebel/understand-biztalk-adapter-for-siebel-ebusiness-applications.md)