---
title: 建立 SAP 系統的連線 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SAP system, connecting to
- connection URI
- URI
- Uniform Resource Identifier
ms.assetid: 25d1eaa7-d02a-4fd0-8adf-83505cdb1ab8
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ef25dddf3d30f584b30aa0f35b8b1c4140d285e2
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36965807"
---
# <a name="create-a-connection-to-the-sap-system"></a>建立 SAP 系統的連線
[!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]是[!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]自訂繫結。 因此，它可讓 SAP 系統，透過 WCF 端點位址的通訊。 在 WCF 中的端點位址會識別服務的網路位置，而且通常表示做為統一資源識別元 (URI)。 [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]表示此位置做為連線 URI，其中包含屬性的[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]用以連接到 SAP 系統。 您必須指定 URI 的連接時您：  
  
- 當您建立通道處理站或通道接聽程式，使用[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]通道模型，或當您建立使用 WCF 用戶端或服務主機[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]服務模型。  
  
- 建立實體連接埠繫結中的[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]解決方案。  
  
- 使用[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]來產生 WCF 用戶端類別或 WCF 服務介面[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]服務模型方案。  
  
- 使用[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]來擷取從訊息結構描述[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]如[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]解決方案。  
  
- 您可以使用 ServiceModel Metadata Utility 工具 (svcutil.exe) 來產生 WCF 用戶端類別或 WCF 服務模型方案的 WCF 服務介面。  
  
  在本節中的主題描述如何之間建立連線[!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]和 SAP 系統，藉由提供您使用：  
  
- 有關連接屬性以及 SAP 連線 URI 的結構。  
  
- 示範如何建立連接所使用的主題連結[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [建立 SAP 系統連線 URI](../../adapters-and-accelerators/adapter-sap/create-the-sap-system-connection-uri.md)