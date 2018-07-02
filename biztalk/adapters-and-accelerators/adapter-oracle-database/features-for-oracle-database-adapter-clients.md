---
title: Oracle 資料庫配接器用戶端的功能 |Microsoft Docs
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
ms.openlocfilehash: ce283c3fd63f72d67e31806e86bf9caa08555dd9
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36976175"
---
# <a name="features-for-oracle-database-adapter-clients"></a>Oracle 資料庫配接器用戶端的功能
除了的主題所討論的功能之外[概觀的 BizTalk 配接器用於 Oracle 資料庫](../../adapters-and-accelerators/adapter-oracle-database/overview-of-biztalk-adapter-for-oracle-database.md)，則[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]也提供適用於配接器用戶端的下列功能：  
  
- **設定使用繫結屬性的配接器支援**。 配接器用戶端可以設定[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]藉由指定特定繫結屬性。 比方說，用戶端可以在其中設定配接器使用 ODP.NET 連接集區，只要**UseOracleConnectionPool**繫結屬性。 如需詳細資訊，請參閱 < [Oracle 資料庫設定的繫結屬性](../../adapters-and-accelerators/adapter-oracle-database/configure-the-binding-properties-for-oracle-database.md)。  
  
- **作業參數的 null 值支援**。 配接器用戶端可以提供輸入 XML 中使用"nil"屬性的作業參數的 null 值。  
  
- **支援在 BizTalk 中的動態連接埠**。 透過 BizTalk [!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)]，則[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]支援動態連接埠，可讓您動態路由的訊息從[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]根據訊息內容屬性。 如需詳細資訊，請參閱 <<c0> [ 設定動態連接埠](../../adapters-and-accelerators/adapter-oracle-database/configure-dynamic-ports-in-the-oracle-database-adapter.md)。  
  
- **對效能計數器支援**。 [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]支援配接器用戶端使用 wcf 效能計數器。 如需有關效能計數器的詳細資訊，請參閱 <<c0> [ 效能計數器](../../core/performance-counters.md)。  
  
## <a name="see-also"></a>另請參閱  
 [BizTalk Adapter for Oracle Database 概觀](../../adapters-and-accelerators/adapter-oracle-database/overview-of-biztalk-adapter-for-oracle-database.md)