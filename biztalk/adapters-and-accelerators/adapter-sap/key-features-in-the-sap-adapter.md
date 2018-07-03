---
title: 主要 SAP 配接器中的功能 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- adapters, deprecated features
- features, technology-related
- adapters, new features
- features, deprecated
- features, metadata-related
- librfc32u.dll
- tRFC server
- features, new
- adapters, new and deprecated features
- queued tRFC client calls
- features, operations-related
- RFC server
ms.assetid: 30e3140c-447f-42ba-a3b0-13ae66e78b0c
caps.latest.revision: 15
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8e85f067b53c8a46238e4de343f240cfc2784885
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36994567"
---
# <a name="key-features-in-the-sap-adapter"></a>SAP 配接器中的主要功能
此區段會列出新功能和已被取代功能[!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]。  
  
> [!NOTE]
>  本主題已使用的舊版[!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]幫助。  
  
## <a name="features-in-the-sap-adapter"></a>SAP 配接器中的功能  
 以下是前一版中引進的功能[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。  
  
### <a name="technology-related-features"></a>技術相關功能  
  
|                                                            功能                                                             |                                                                                                                                                                                                                                                                                              註解                                                                                                                                                                                                                                                                                               |
|--------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 使用[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]與 SQL Server Reporting Services (SSRS)。 | 現在可以使用用戶端程式[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]SAP 後端的資料匯入到 SSRS 專案，並產生資料的報表。 如需有關如何使用[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]ssrs，請參閱[使用 Data Provider for SAP 與 SSRS](../../adapters-and-accelerators/adapter-sap/use-the-data-provider-for-sap-with-ssrs.md)。 如需有關 SSRS 的詳細資訊，請參閱[SQL Server Reporting Services](https://msdn.microsoft.com/library/ms159106.aspx)。 |
|                                     叫用 SAP 系統中定義的查詢支援                                      |                                                                                                                                                           [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]公開的作業，EXECQUERY，可用來執行 SAP 系統中定義的查詢。 如需有關如何使用 EXECQUERY 功能的詳細資訊，請參閱 [針對執行 SAP 查詢的支援                                                                                                                                                            |

](https://msdn.microsoft.com/library/dd788118.aspx).|  
|支援使用[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]與 Microsoft Office SharePoint Server (MOSS) |您可以使用配接器，以呈現到 MOSS 入口網站上之 SAP 系統的資料。 如需詳細資訊，請參閱 <<c0> [ 搭配使用 SharePoint 與 SAP 配接器](../../adapters-and-accelerators/adapter-sap/use-the-sap-adapter-with-sharepoint.md)。 |  
  
### <a name="metadata-related-features"></a>中繼資料相關的功能  
  
|                功能                 |                                                                                                                                                                                                                                                                                                   註解                                                                                                                                                                                                                                                                                                    |
|----------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **DataTypesBehavior**繫結屬性 | [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]隨附[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]提供複雜的繫結屬性**DataTypesBehavior**，可讓 SAP 系統中遇到特殊的值時，控制配接器行為的配接器用戶端。 如需此繫結屬性的詳細討論，請參閱 <<c0> [ 了解 BizTalk Adapter for mySAP Business Suite 繫結屬性](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md)。 |
  
### <a name="operations-related-features"></a>作業相關的功能  
  
|                          功能                          |                                                                                                                                                                                                                                                 註解                                                                                                                                                                                                                                                  |
|-----------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 叫用 RFC 所需的外部程式的支援 | [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]提供繫結屬性**RfcAllowStartProgram**可用來設定要啟用 RFC 用戶端程式庫，來叫用外部程式，如果任何項目，需要特定的 RFC。 如需有關這個繫結屬性的詳細資訊，請參閱[了解 BizTalk Adapter for mySAP Business Suite 繫結屬性](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md)。 |
|    支援的單一呼叫中傳送多個 Idoc    |                                                                                                                                                                                                      SAP 配接器現在支援傳送配接器的單一呼叫中的相同類型的多個 Idoc。                                                                                                                                                                                                      |
  
### <a name="other-features"></a>其他功能  
  
|                                                        功能                                                        |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                註解                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
|-----------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 使用中的配接器的新方式 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] | [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]可用於 BizTalk 做為 WCF 自訂連接埠或 WCF SAP 連接埠。 如果您想要使用[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]透過 WCF 自訂連接埠，您不需要新增的 WCF 自訂連接埠[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台，因為 WCF 自訂連接埠新增至[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台中的，預設值。 不過，如果您想要使用[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]透過 WCF SAP 連接埠，您必須先新增 WCF SAP 配接器[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。 如需詳細資訊，請參閱 < [SAP 配接器加入 BizTalk Server 管理主控台](../../adapters-and-accelerators/adapter-sap/add-the-sap-adapter-to-biztalk-server-administration-console.md)。 |
  
## <a name="deprecated-features-in-the-sap-adapter"></a>SAP 配接器中已被取代的功能  
 下列各節列出的功能，支援在舊版本的配接器，但其目前的版本中不支援[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。  
  
### <a name="enablebusinessobjects-binding-property-deprecated"></a>已被取代的 EnableBusinessObjects 繫結屬性  
 中的這個繫結屬性已被取代[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]隨附[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]。 此繫結屬性用來判斷是否使用時產生中繼資料時，會顯示 BAPI 節點[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]或[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]。  
  
## <a name="see-also"></a>另請參閱  
 [了解 BizTalk Adapter for mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/understand-biztalk-adapter-for-mysap-business-suite.md)