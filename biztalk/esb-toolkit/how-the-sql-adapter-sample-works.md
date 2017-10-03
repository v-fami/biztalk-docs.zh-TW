---
title: "SQL 配接器範例的運作方式 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 77811152-cc8e-4090-89eb-e3a402a46e5e
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d4ff56f2f2f88d35290ffd897d107910e206ac98
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-the-sql-adapter-sample-works"></a><span data-ttu-id="e7621-102">SQL 配接器範例的運作方式</span><span class="sxs-lookup"><span data-stu-id="e7621-102">How the SQL Adapter Sample Works</span></span>
<span data-ttu-id="e7621-103">SQL 配接器範例提供使用路由服務和轉換訊息的服務設定的範例雙向的路線。</span><span class="sxs-lookup"><span data-stu-id="e7621-103">The SQL Adapter sample provides a sample two-way itinerary configured with the routing service and a transform messaging service.</span></span>  
  
 <span data-ttu-id="e7621-104">設定路由服務是靜態的解決器，指定應該在執行 SQL 預存程序內名為 InsertProduct 使用 Wcf-custom 配接器提供者的 GlobalBankESB 資料庫路由傳送訊息。</span><span class="sxs-lookup"><span data-stu-id="e7621-104">The routing service is configured with a STATIC resolver, which specifies that the message should be routed to execute a SQL stored procedure within the GlobalBankESB database named InsertProduct using the WCF-Custom adapter provider.</span></span>  
  
 <span data-ttu-id="e7621-105">轉換服務都會指定一個對應，將內送訊息轉換成 InsertProduct 預存程序所接受的格式。</span><span class="sxs-lookup"><span data-stu-id="e7621-105">The transform service specifies a map that converts the incoming message to the format accepted by the InsertProduct stored procedure.</span></span>