---
title: "Siebel 配接器中的 SiebelClientFactory 類別 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SiebelClientFactory
- Data Provider for Siebel, SiebelClientFactory
- SiebelClientFactory, supported properties and methods
ms.assetid: f3a807d3-a030-47d8-b145-e18075ec353c
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 50e47b22c1d5a2575b0da3fae432acd79886e2c3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="siebelclientfactory-class-in-the-siebel-adapter"></a>Siebel 配接器中 SiebelClientFactory 類別
ADO.NET 用戶端會存取[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]使用泛型的 ADO.NET 類別和介面。 若要啟用這項功能，[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]繼承**System.Data.Common.DbProviderFactory**類別。 用戶端，也會耗用用戶端，如下所示：  
  
```  
  
DbProviderFactory factory = DbProviderFactories.GetFactory("Microsoft.Data.SiebelClient");  
DbConnection connection = factory.CreateConnection();  
```  
  
 另一個方法是，如下所示：  
  
```  
SiebelClientFactory factory = SiebelClientFactory.Instance;  
DbConnection connection = factory.CreateConnection();  
```  
  
 SiebelClientFactory 存在 Microsoft.Data.SiebelClient 命名空間中。  
  
## <a name="supported-members"></a>支援的成員  
 **SiebelClientFactory**擴充**System.Data.CommonDbProviderFactory**。  下表提供之成員的說明， **SiebelClientFactory**會覆寫。  
  
|名稱|Description|  
|----------|-----------------|  
|**執行個體**|這是成員變數。  它提供 SiebelClientFactory 的單一執行個體。|  
|**CreateCommand()**|建立 SiebelCommand 的執行個體。|  
|**CreateConnection()**|建立 SiebelConnection 的執行個體。|  
|**CreateConnectionStringBuilder()**|建立 SiebelConnectionStringBuilder 的執行個體。|  
|**Createparameter （)**|建立 SiebelParameter 的執行個體。|  
  
## <a name="see-also"></a>另請參閱  
 [Siebel 配接器以延伸的 ADO.NET 介面](../../adapters-and-accelerators/adapter-siebel/extend-ado-net-interfaces-with-the-siebel-adapter.md)