---
title: 建立 SQL Server 的連線 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 44a03b2c-55b5-49a0-92cc-6f017720d34a
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b7c5f186a28f068f3ffc217ce5f252a1512f03a0
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36978007"
---
# <a name="create-a-connection-to-sql-server"></a>建立 SQL Server 的連線
[!INCLUDE[adaptersql](../../includes/adaptersql-md.md)]是[!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]自訂繫結。 因此，它可讓 SQL Server 資料庫，透過 WCF 端點位址的通訊。 在 WCF 中，端點位址會識別服務的網路位置，而且通常表示做為統一資源識別元 (URI)。 [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]表示此位置做為連線 URI，其中包含屬性的[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]用以連接到 SQL Server 資料庫。 您必須指定 URI 的連接時您：  
  
- 建立通道處理站或通道接聽程式使用 WCF 通道模型，或當您建立使用 WCF 服務模型的 WCF 用戶端或服務主機。  
  
- 建立實體連接埠繫結中的[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]解決方案。  
  
- 使用[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]來產生 WCF 用戶端類別或 WCF 服務模型方案的 WCF 服務介面。  
  
- 使用[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]來擷取訊息的結構描述從[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]BizTalk Server 解決方案。  
  
- 您可以使用 ServiceModel Metadata Utility 工具 (svcutil.exe) 來產生 WCF 用戶端類別或 WCF 服務模型方案的 WCF 服務介面。  
  
  在本節中的主題描述如何之間建立連線[!INCLUDE[adaptersql](../../includes/adaptersql-md.md)]和藉由提供您使用 SQL Server 資料庫：  
  
- 有關連接屬性以及 SQL Server 連接 URI 的結構。  
  
- 示範如何使用指定的連線 URI 的主題連結[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。  
  
- 連接到使用 Windows 驗證的 SQL Server 的相關資訊。  
  
  
  
## <a name="see-also"></a>另請參閱  
[開發 SQL 應用程式](../../adapters-and-accelerators/adapter-sql/develop-your-sql-applications.md)