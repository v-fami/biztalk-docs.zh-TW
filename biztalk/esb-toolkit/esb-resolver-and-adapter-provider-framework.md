---
title: ESB 解析程式和配接器提供者架構 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c82c2247-1f0a-48bd-98c2-9c816f4d68d7
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 900897c4b740f39dbec2f5f513b5e814d1589bf9
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36987023"
---
# <a name="esb-resolver-and-adapter-provider-framework"></a>ESB 解析程式和配接器提供者架構
解析程式和配接器提供者架構可提供完整、 可外掛式架構動態解析端點資訊和 BizTalk Server 對應型別。 它會使用可延伸的元件，可讓開發人員變更以符合他們自己的需求，並擴充機制，以支援替代的解析和路由方法的行為。  
  
 解析程式和配接器提供者架構提供支援通用描述、 探索與整合 (UDDI)、 商務規則引擎 (BRE) 與 XML 路徑語言 (XPath)。 它也會公開開發人員介面 (**IResolveProvider**並**IAdapterProvider**) 以允許建立自訂的解析程式和配接器元件。 解析程式和配接器提供者架構的三個主要元件如下：  
  
- **解析程式。** 這些定義的結構描述中，連接字串，並透過實作**IResolveProvider** .NET Framework 組件中的介面。 這些會載入和快取在執行階段，並支援各種解析度類型和連接字串。  
  
- **配接器提供者。** 這些定義透過實作**IAdapterProvider** .NET Framework 組件中的介面。 這些會依其設定在適當的 BizTalk Server 配接器的解析程式所提供的端點資訊的 BizTalk Server 傳輸類型註冊。  
  
- **路線的管線元件。** 這些剖析解決方法指示的連接字串中或從 ESB 路線 SOAP 標頭，並且會提供端點解析或轉換執行功能使用的解析程式和配接器提供者架構。 元件可動態設定 BizTalk Server 端點屬性，或執行解析的指示從連接字串，或從 ESB 路線 SOAP 標頭為基礎的 BizTalk Server 對應 」 轉換。 這些元件是負責管理、 更新和保存跨處理序和服務界限的路線。 選擇性的解譯器元件可讓您提供的訊息，並實作的原生 BizTalk Server 剖析[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]路由至多個端點，而不需要協調流程服務的功能。  
  
  如需有關動態解析和動態路由的詳細資訊，請參閱 <<c0> [ 使用動態解析和路由](../esb-toolkit/using-dynamic-resolution-and-routing.md)並[使用動態轉換](../esb-toolkit/using-dynamic-transformation.md)。 有關解析度和配接器提供者架構的資訊，請參閱[修改和擴充 BizTalk ESB Toolkit](../esb-toolkit/modifying-and-extending-the-biztalk-esb-toolkit.md)。