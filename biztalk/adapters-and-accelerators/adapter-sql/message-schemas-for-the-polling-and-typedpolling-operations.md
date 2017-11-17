---
title: "輪詢和 SQL 配接器在 BizTalk TypedPolling 作業的訊息結構描述 |Microsoft 文件"
description: "輪詢和 TypedPolling 訊息 SQL 配接器在 BizTalk 配接器組件 (BAP) 中使用的結構"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1e900307-2c9c-493b-81c9-67af3e143eeb
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2f18185e4bfaf5502537a68044579b0f7721cd23
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="message-schemas-for-the-polling-and-typedpolling-operations"></a><span data-ttu-id="b08e3-103">輪詢和 TypedPolling 作業的訊息結構描述</span><span class="sxs-lookup"><span data-stu-id="b08e3-103">Message Schemas for the Polling and TypedPolling Operations</span></span>
<span data-ttu-id="b08e3-104">[!INCLUDE[adaptersql](../../includes/adaptersql-md.md)]輪詢和 TypedPolling 介面的輸入來輪詢查詢的結果集傳回至配接器的用戶端操作。</span><span class="sxs-lookup"><span data-stu-id="b08e3-104">The [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)] surfaces the Polling and TypedPolling inbound operations to return the result set of the polling query to an adapter client.</span></span>  
  
 <span data-ttu-id="b08e3-105">設定繫結屬性設定輪詢和 TypedPolling 作業[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b08e3-105">You configure the Polling and TypedPolling operations by setting binding properties in the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span> <span data-ttu-id="b08e3-106">如需有關這些繫結屬性的詳細資訊，請參閱[閱讀 BizTalk Adapter for SQL Server 配接器繫結屬性](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="b08e3-106">For more information about these binding properties, see [Read about the BizTalk Adapter for SQL Server adapter binding properties](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md).</span></span> <span data-ttu-id="b08e3-107">您設定**PollingStatement**內容繫結至指定的 SQL 陳述式 (SELECT 或 EXEC\<預存程序 >) 的輪詢查詢。</span><span class="sxs-lookup"><span data-stu-id="b08e3-107">You set the **PollingStatement** binding property to specify a SQL statement (SELECT or EXEC \<stored procedure>) for the polling query.</span></span> <span data-ttu-id="b08e3-108">為您的程式碼在輪詢作業中，資料和強型別 TypedPolling 作業中的資料，則會傳回此查詢的結果集。</span><span class="sxs-lookup"><span data-stu-id="b08e3-108">The result set of this query is returned as data to your code in the Polling operation, and as strongly-typed data in the TypedPolling operation.</span></span> <span data-ttu-id="b08e3-109">結果集的結構取決於中繼資料配接器可呈現為指定的查詢。</span><span class="sxs-lookup"><span data-stu-id="b08e3-109">The structure of the result set is determined by the metadata that the adapter surfaces for the specified query.</span></span>  
  
## <a name="polling-message-structure"></a><span data-ttu-id="b08e3-110">輪詢訊息結構</span><span class="sxs-lookup"><span data-stu-id="b08e3-110">Polling message structure</span></span> 
  
<span data-ttu-id="b08e3-111">**作業**:`Polling`</span><span class="sxs-lookup"><span data-stu-id="b08e3-111">**Operation**: `Polling`</span></span>

<span data-ttu-id="b08e3-112">**XML 訊息**:</span><span class="sxs-lookup"><span data-stu-id="b08e3-112">**XML Message**:</span></span>  
```xml
<?xml version="1.0" encoding="utf-8" ?>
  <Polling xmlns="http://schemas.microsoft.com/Sql/2008/05/Polling">
    <PolledData>
      <DataSet xmlns="http://schemas.datacontract.org/2004/07/System.Data">
        <any>[Value]</any>
        <any>[Value]</any>
        …
        </DataSet>
    </PolledData>
 </Polling>
```

<span data-ttu-id="b08e3-113">**描述**: SQL Server 傳送到配接器用戶端的傳入的訊息。</span><span class="sxs-lookup"><span data-stu-id="b08e3-113">**Description**: The inbound message that is sent by the SQL Server to the adapter clients.</span></span>  


## <a name="typedpolling-message-structure"></a><span data-ttu-id="b08e3-114">TypedPolling 訊息結構</span><span class="sxs-lookup"><span data-stu-id="b08e3-114">TypedPolling message structure</span></span> 

<span data-ttu-id="b08e3-115">**作業**:`TypedPolling`</span><span class="sxs-lookup"><span data-stu-id="b08e3-115">**Operation**: `TypedPolling`</span></span>

<span data-ttu-id="b08e3-116">**XML 訊息**:</span><span class="sxs-lookup"><span data-stu-id="b08e3-116">**XML Message**:</span></span>  
```xml
<?xml version="1.0" encoding="utf-8" ?>
  <TypedPollingResultSet xmlns="http://schemas.microsoft.com/Sql/2008/05/TypedPolling">
    <COLUMN1>[Value]</Column1>
    <COLUMN2>[Value]</Column2>
    …
  </TypedPollingResultSet>
```

<span data-ttu-id="b08e3-117">**描述**： 強型別輸入的訊息到配接器用戶端傳送的 SQL Server。</span><span class="sxs-lookup"><span data-stu-id="b08e3-117">**Description**: The strongly-typed inbound message that is sent by the SQL Server to the adapter clients.</span></span>
  
## <a name="message-action-for-the-polling-and-typedpolling-operations"></a><span data-ttu-id="b08e3-118">輪詢和 TypedPolling 作業的訊息動作</span><span class="sxs-lookup"><span data-stu-id="b08e3-118">Message Action for the Polling and TypedPolling Operations</span></span>  
 <span data-ttu-id="b08e3-119">訊息動作:</span><span class="sxs-lookup"><span data-stu-id="b08e3-119">The message action for the:</span></span>  
  
-   <span data-ttu-id="b08e3-120">輪詢作業正在 「 輪詢 」。</span><span class="sxs-lookup"><span data-stu-id="b08e3-120">Polling operation is “Polling.”</span></span>  
  
-   <span data-ttu-id="b08e3-121">TypedPolling 作業為"TypedPolling。 」</span><span class="sxs-lookup"><span data-stu-id="b08e3-121">TypedPolling operation is “TypedPolling.”</span></span>  
  
