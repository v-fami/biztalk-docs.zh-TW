---
title: Siebel 配接器中的 SiebelConnectionStringBuilder 類別 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SiebelConnectionStringBuilder, supported properties and methods
- Data Provider for Siebel, SiebelConnectionStringBuilder
- SiebelConnectionStringBuilder
ms.assetid: 4995fce8-7e62-4af9-a731-47b16438067c
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 088748c63983e76e64d32f54b3e999fadd88d23a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22222006"
---
# <a name="siebelconnectionstringbuilder-class-in-the-siebel-adapter"></a><span data-ttu-id="07e10-102">Siebel 配接器中 SiebelConnectionStringBuilder 類別</span><span class="sxs-lookup"><span data-stu-id="07e10-102">SiebelConnectionStringBuilder class in the Siebel adapter</span></span>
<span data-ttu-id="07e10-103">[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]提供`DbConnectionStringBuilder`實作，以啟用 SQL Server Integration Services (SSIS) 和 Visual Studio 總管工具環境所取得的連接屬性[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]和在 GUI 所驅動的表單中顯示PropertyGrid。</span><span class="sxs-lookup"><span data-stu-id="07e10-103">The [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] provides a `DbConnectionStringBuilder` implementation to enable SQL Server Integration Services (SSIS) and Visual Studio explorer tools environments to get the connection properties of the [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] and display them in the form of a GUI driven by the PropertyGrid.</span></span>  
  
 <span data-ttu-id="07e10-104">若要建立 SiebelConnectionStringBuilder，請使用以下方法：</span><span class="sxs-lookup"><span data-stu-id="07e10-104">To create a SiebelConnectionStringBuilder, use the following approach:</span></span>  
  
```  
  
//In this example, factory is an instance of SiebelClientFactory  
SiebelConnectionStringBuilder bldr = (SiebelConnectionStringBuilder)factory.CreateConnectionStringBuilder();  
bldr.ConnectionString = connstr;  
```  
  
 <span data-ttu-id="07e10-105">或只是：</span><span class="sxs-lookup"><span data-stu-id="07e10-105">Or, simply:</span></span>  
  
```  
  
SiebelConnectionStringBuilder bldr = new SiebelConnectionStringBuilder();  
```  
  
 <span data-ttu-id="07e10-106">若要查看索引鍵和值支援一部分`DbConnectionStringBuilder`，請參閱[Siebel 連接字串的資料提供者屬性](../../adapters-and-accelerators/adapter-siebel/data-provider-properties-for-the-siebel-connection-string.md)。</span><span class="sxs-lookup"><span data-stu-id="07e10-106">To see the keys and values supported as part of the `DbConnectionStringBuilder`, see [Data Provider properties for the Siebel Connection String](../../adapters-and-accelerators/adapter-siebel/data-provider-properties-for-the-siebel-connection-string.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07e10-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="07e10-107">See Also</span></span>  
 [<span data-ttu-id="07e10-108">Siebel 配接器以延伸的 ADO.NET 介面</span><span class="sxs-lookup"><span data-stu-id="07e10-108">Extend ADO.NET Interfaces with the Siebel adapter</span></span>](../../adapters-and-accelerators/adapter-siebel/extend-ado-net-interfaces-with-the-siebel-adapter.md)