---
title: SQL 配接器用戶端的功能 |Microsoft Docs
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
ms.openlocfilehash: e2bcf55950995d5d9b64f0c0e1cca55ad628f4e9
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36977095"
---
# <a name="features-for-sql-adapter-clients"></a>SQL 配接器用戶端的功能
除了的主題所討論的功能之外[概觀的 BizTalk 配接器適用於 SQL Server](../../adapters-and-accelerators/adapter-sql/overview-of-biztalk-adapter-for-sql-server.md)，則[!INCLUDE[adaptersql](../../includes/adaptersql-md.md)]也提供適用於配接器用戶端的下列功能：  
  
- **設定使用繫結屬性的配接器支援**。 配接器用戶端可以設定[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]藉由指定特定繫結屬性。 例如，用戶端可以指定的連接集區中允許特定連接字串設定的連線數目上限**MaxConnectionPoolSize**繫結屬性。 如需詳細資訊，請參閱 <<c0> [ 了解 BizTalk Adapter for SQL Server 配接器繫結屬性](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md)。  
  
- **作業參數的 null 值支援**。 配接器用戶端可以使用 XSD 的"nillable"屬性的作業參數提供 null 值。  
  
- **支援在 BizTalk 中的動態連接埠**。 透過 BizTalk [!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)]，則[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]支援動態連接埠，可讓您動態路由的訊息從[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]根據訊息內容屬性。 如需詳細資訊，請參閱 <<c0> [ 設定動態連接埠](../../adapters-and-accelerators/adapter-sql/configure-dynamic-ports-in-the-sql-adapter.md)。  
  
- **對效能計數器支援**。 [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]支援配接器用戶端使用 wcf 效能計數器。 如需有關效能計數器的詳細資訊，請參閱 <<c0> [ 使用 SQL 配接器的效能計數器](../../adapters-and-accelerators/adapter-sql/use-performance-counters-with-the-sql-adapter.md)。  
  
## <a name="see-also"></a>另請參閱  
 [BizTalk Adapter for SQL Server 概觀](../../adapters-and-accelerators/adapter-sql/overview-of-biztalk-adapter-for-sql-server.md)