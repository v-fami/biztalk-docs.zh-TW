---
title: Oracle 資料庫配接器用戶端功能 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- data streaming, support for
- binding properties
- adapter, features
- adapters, configuring
- message versioning, support for
- XML data streaming
- performance counters, support for
- dynamic ports in BizTalk, support for
- data streaming
ms.assetid: 63b52573-80a5-4206-95c3-478b86718fee
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b120c948ef3d9821af0a79e91fd718e3a1f33137
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22214318"
---
# <a name="features-for-oracle-database-adapter-clients"></a>Oracle 資料庫配接器用戶端的功能
除了所有的主題所討論的功能[概觀的 BizTalk 配接器的 Oracle 資料庫](../../adapters-and-accelerators/adapter-oracle-database/overview-of-biztalk-adapter-for-oracle-database.md)、[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]也提供可用於配接器用戶端的下列功能：  
  
-   **設定配接器使用的繫結屬性的支援**。 可以設定配接器用戶端[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]藉由指定特定繫結內容。 例如，用戶端可以設定配接器使用 ODP.NET 連接集區設定**UseOracleConnectionPool**繫結屬性。 如需詳細資訊，請參閱[Oracle 資料庫的設定繫結屬性](../../adapters-and-accelerators/adapter-oracle-database/configure-the-binding-properties-for-oracle-database.md)。  
  
-   **作業參數的 null 值支援**。 配接器用戶端可以提供輸入 XML 中使用"nil"屬性的作業參數的 null 值。  
  
-   **支援動態連接埠，在 BizTalk**。 透過 BizTalk [!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)]、[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]支援動態連接埠，可讓您動態路由的訊息從[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]根據訊息內容屬性。 如需詳細資訊，請參閱[設定動態連接埠](../../adapters-and-accelerators/adapter-oracle-database/configure-dynamic-ports-in-the-oracle-database-adapter.md)。  
  
-   **對效能計數器支援**。 [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]以供配接器用戶端支援以 WCF 為基礎的效能計數器。 如需有關效能計數器的詳細資訊，請參閱[效能計數器](../../core/performance-counters.md)。  
  
## <a name="see-also"></a>另請參閱  
 [BizTalk Adapter for Oracle 資料庫的概觀](../../adapters-and-accelerators/adapter-oracle-database/overview-of-biztalk-adapter-for-oracle-database.md)