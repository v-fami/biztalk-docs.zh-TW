---
title: 使用.NET Framework Data Provider for Siebel eBusiness 應用程式 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ADO.NET programming, performing operations
- Data Provider for Siebel, overview
ms.assetid: 97fe4f95-c9ae-42f1-a159-1b0e98607b31
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5acb8f96add3dcde48456751d82dc2a8e00ffe43
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22222238"
---
# <a name="use-the-net-framework-data-provider-for-siebel-ebusiness-applications"></a><span data-ttu-id="c62e3-102">使用.NET Framework Data Provider for Siebel eBusiness 應用程式</span><span class="sxs-lookup"><span data-stu-id="c62e3-102">Use the .NET Framework Data Provider for Siebel eBusiness Applications</span></span>
<span data-ttu-id="c62e3-103">本節提供使用指示[!INCLUDE[adoprovidersiebellong](../../includes/adoprovidersiebellong-md.md)] ([!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)])。</span><span class="sxs-lookup"><span data-stu-id="c62e3-103">This section provides instructions on using the [!INCLUDE[adoprovidersiebellong](../../includes/adoprovidersiebellong-md.md)] ([!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]).</span></span> <span data-ttu-id="c62e3-104">本節提供有關的資訊：</span><span class="sxs-lookup"><span data-stu-id="c62e3-104">This section provides information about:</span></span>  
  
-   <span data-ttu-id="c62e3-105">若要連接至 Siebel 系統使用的 ADO.NET 用戶端連接字串。</span><span class="sxs-lookup"><span data-stu-id="c62e3-105">The connection string to connect to a Siebel system using an ADO.NET client.</span></span>  
  
-   <span data-ttu-id="c62e3-106">SELECT 和 EXEC 陳述式的語法。</span><span class="sxs-lookup"><span data-stu-id="c62e3-106">The syntax for SELECT and EXEC statements.</span></span>  
  
-   <span data-ttu-id="c62e3-107">使用[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]與 SSIS。</span><span class="sxs-lookup"><span data-stu-id="c62e3-107">Using the [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] with SSIS.</span></span>  
  
-   <span data-ttu-id="c62e3-108">ADO.NET 介面[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]擴充。</span><span class="sxs-lookup"><span data-stu-id="c62e3-108">The ADO.NET interfaces that the [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] extends.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c62e3-109">本節內容</span><span class="sxs-lookup"><span data-stu-id="c62e3-109">In This Section</span></span>  
  
-   [<span data-ttu-id="c62e3-110">Siebel 配接器以延伸的 ADO.NET 介面</span><span class="sxs-lookup"><span data-stu-id="c62e3-110">Extend ADO.NET Interfaces with the Siebel adapter</span></span>](../../adapters-and-accelerators/adapter-siebel/extend-ado-net-interfaces-with-the-siebel-adapter.md)  
  
-   [<span data-ttu-id="c62e3-111">Siebel 連接字串的資料提供者內容</span><span class="sxs-lookup"><span data-stu-id="c62e3-111">Data Provider properties for the Siebel Connection String</span></span>](../../adapters-and-accelerators/adapter-siebel/data-provider-properties-for-the-siebel-connection-string.md)  
  
-   [<span data-ttu-id="c62e3-112">Siebel 中的 SELECT 陳述式的語法</span><span class="sxs-lookup"><span data-stu-id="c62e3-112">Syntax for a SELECT Statement in Siebel</span></span>](../../adapters-and-accelerators/adapter-siebel/syntax-for-a-select-statement-in-siebel.md)  
  
-   [<span data-ttu-id="c62e3-113">Siebel 中 EXEC 陳述式語法</span><span class="sxs-lookup"><span data-stu-id="c62e3-113">Syntax for an EXEC Statement in Siebel</span></span>](../../adapters-and-accelerators/adapter-siebel/syntax-for-an-exec-statement-in-siebel.md)  
  
-   [<span data-ttu-id="c62e3-114">Siebel 商務元件上執行 SELECT 查詢</span><span class="sxs-lookup"><span data-stu-id="c62e3-114">Run a SELECT Query on Business Components with Siebel</span></span>](../../adapters-and-accelerators/adapter-siebel/run-a-select-query-on-business-components-with-siebel.md)  
  
-   [<span data-ttu-id="c62e3-115">執行與 Siebel 商務服務上的執行作業</span><span class="sxs-lookup"><span data-stu-id="c62e3-115">Run an EXECUTE Operation on Business Services with Siebel</span></span>](../../adapters-and-accelerators/adapter-siebel/run-an-execute-operation-on-business-services-with-siebel.md)  
  
-   [<span data-ttu-id="c62e3-116">Siebel 與 SSIS 中使用資料提供者</span><span class="sxs-lookup"><span data-stu-id="c62e3-116">Use the Data Provider for Siebel with SSIS</span></span>](../../adapters-and-accelerators/adapter-siebel/use-the-data-provider-for-siebel-with-ssis.md)