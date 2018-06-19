---
title: SQL 配接器用戶端的功能 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f638154b-0a09-4f89-9c52-2a62fafec7dc
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d0d1df3a7d5c5748db4b0d3f365d80d84ff1f670
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22222710"
---
# <a name="features-for-sql-adapter-clients"></a>SQL 配接器用戶端的功能
除了所有的主題所討論的功能[概觀的 BizTalk 配接器適用於 SQL Server](../../adapters-and-accelerators/adapter-sql/overview-of-biztalk-adapter-for-sql-server.md)、[!INCLUDE[adaptersql](../../includes/adaptersql-md.md)]也提供可用於配接器用戶端的下列功能：  
  
-   **設定配接器使用的繫結屬性的支援**。 可以設定配接器用戶端[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]藉由指定特定繫結內容。 例如，用戶端可以指定連接集區中允許的特定連接字串的設定連線的數目上限**MaxConnectionPoolSize**繫結屬性。 如需詳細資訊，請參閱[閱讀 BizTalk Adapter for SQL Server 配接器繫結屬性](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md)。  
  
-   **作業參數的 null 值支援**。 配接器用戶端可以使用 XSD 的"nillable"屬性的作業參數提供 null 值。  
  
-   **支援動態連接埠，在 BizTalk**。 透過 BizTalk [!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)]、[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]支援動態連接埠，可讓您動態路由的訊息從[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]根據訊息內容屬性。 如需詳細資訊，請參閱[設定動態連接埠](../../adapters-and-accelerators/adapter-sql/configure-dynamic-ports-in-the-sql-adapter.md)。  
  
-   **對效能計數器支援**。 [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]以供配接器用戶端支援以 WCF 為基礎的效能計數器。 如需有關效能計數器的詳細資訊，請參閱[使用 SQL 配接器的效能計數器](../../adapters-and-accelerators/adapter-sql/use-performance-counters-with-the-sql-adapter.md)。  
  
## <a name="see-also"></a>另請參閱  
 [BizTalk Adapter for SQL Server 的概觀](../../adapters-and-accelerators/adapter-sql/overview-of-biztalk-adapter-for-sql-server.md)