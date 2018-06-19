---
title: Oracle EBS 配接器用戶端功能 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 50256fb7-5f0c-4b32-87e6-98f49da0b360
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2da086390fe049a5333dda40a35e19f46298dda1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22217254"
---
# <a name="features-for-oracle-ebs-adapter-clients"></a>Oracle EBS 配接器用戶端的功能
除了所有的主題所討論的功能[概觀的 BizTalk 配接器 for Oracle E-business Suite](http://msdn.microsoft.com/library/4f18fa2e-4e97-4c28-b38d-fc39ac53789e)、[!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]也提供可用於配接器用戶端的下列功能：  
  
-   **設定配接器使用的繫結屬性的支援**。 可以設定配接器用戶端[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]藉由指定特定繫結內容。 例如，用戶端可以設定配接器使用 ODP.NET 連接集區設定**UseOracleConnectionPool**繫結屬性。 如需詳細資訊，請參閱[了解 BizTalk Adapter for Oracle E-business Suite 繫結屬性](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md)。  
  
-   **作業參數的 null 值支援**。 配接器用戶端可以提供輸入 XML 中使用"nil"屬性的作業參數的 null 值。  
  
-   **支援動態連接埠，在 BizTalk**。 透過 BizTalk [!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)]、[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]支援動態連接埠，可讓您動態路由的訊息從[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]根據訊息內容屬性。 如需詳細資訊，請參閱[SQL 配接器中的 設定動態連接埠](../../adapters-and-accelerators/adapter-sql/configure-dynamic-ports-in-the-sql-adapter.md)。  
  
## <a name="see-also"></a>另請參閱  
[瞭解 BizTalk Adapter for Oracle E-business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/understand-biztalk-adapter-for-oracle-e-business-suite.md)