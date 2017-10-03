---
title: "訊息和訊息結構描述，BizTalk adapter for Oracle E-business Suite |Microsoft 文件"
description: "BizTalk Server 的 Oracle EBS 配接器使用的訊息和資料類型的 XML 結構"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4434b4d4-fbe0-4692-81a5-9883c9a77cf6
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9069e5bf83f323726da7c8b08b9f5cc7ca6ccd85
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="messages-and-message-schemas-for-biztalk-adapter-for-oracle-e-business-suite"></a><span data-ttu-id="57f28-103">訊息和訊息結構描述，BizTalk adapter for Oracle E-business Suite</span><span class="sxs-lookup"><span data-stu-id="57f28-103">Messages and Message Schemas for BizTalk Adapter for Oracle E-Business Suite</span></span>

## <a name="overview"></a><span data-ttu-id="57f28-104">概觀</span><span class="sxs-lookup"><span data-stu-id="57f28-104">Overview</span></span>
<span data-ttu-id="57f28-105">[!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]是[!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]自訂繫結。</span><span class="sxs-lookup"><span data-stu-id="57f28-105">The [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)] is a [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] custom binding.</span></span> <span data-ttu-id="57f28-106">它會公開應用程式可以在其上叫用，接著，可以呼叫應用程式上的作業。</span><span class="sxs-lookup"><span data-stu-id="57f28-106">It exposes operations that applications can invoke on it and that it can, in turn, invoke on applications.</span></span> <span data-ttu-id="57f28-107">這些作業會叫用透過通道傳送 SOAP 訊息。</span><span class="sxs-lookup"><span data-stu-id="57f28-107">These operations are invoked by sending SOAP messages over a channel.</span></span> <span data-ttu-id="57f28-108">如果需要回應，它會傳回 SOAP 訊息中透過相同的通道。</span><span class="sxs-lookup"><span data-stu-id="57f28-108">If a response is required, it is returned in a SOAP message over the same channel.</span></span>  
  
 <span data-ttu-id="57f28-109">做為[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]服務[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]會公開其作業和資料類型的中繼資料，以使用標準[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]機制。</span><span class="sxs-lookup"><span data-stu-id="57f28-109">As a [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] service, the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] exposes metadata for its operations and data types by using standard [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] mechanisms.</span></span> <span data-ttu-id="57f28-110">本主題中的各節描述 XML 訊息的結構和資料型別[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]使用。</span><span class="sxs-lookup"><span data-stu-id="57f28-110">The sections in this topic describe the XML structure of the messages and data types that the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="57f28-111">本節內容</span><span class="sxs-lookup"><span data-stu-id="57f28-111">In This Section</span></span>  
  
-   [<span data-ttu-id="57f28-112">基本的 Oracle 資料類型</span><span class="sxs-lookup"><span data-stu-id="57f28-112">Basic Oracle Data Types</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/basic-oracle-data-types2.md)  
  
-   [<span data-ttu-id="57f28-113">訊息結構描述，插入、 更新、 刪除和選取作業</span><span class="sxs-lookup"><span data-stu-id="57f28-113">Message Schemas for Insert, Update, Delete, and Select Operations</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/message-schemas-for-insert-update-delete-and-select-operations.md)  
  
-   [<span data-ttu-id="57f28-114">訊息結構描述的預存程序、 函數和 PL/SQL 應用程式開發介面</span><span class="sxs-lookup"><span data-stu-id="57f28-114">Message Schemas for Stored Procedures, Functions, and PL/SQL APIs</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/message-schemas-for-stored-procedures-functions-and-pl-sql-apis.md)  
  
-   [<span data-ttu-id="57f28-115">並行程式的訊息結構描述</span><span class="sxs-lookup"><span data-stu-id="57f28-115">Message Schemas for Concurrent Programs</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/message-schemas-for-concurrent-programs.md)  
  
-   [<span data-ttu-id="57f28-116">要求的訊息結構描述</span><span class="sxs-lookup"><span data-stu-id="57f28-116">Message Schemas for Request Sets</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/message-schemas-for-request-sets.md)  
  
-   [<span data-ttu-id="57f28-117">特殊 LOB 作業的訊息結構描述</span><span class="sxs-lookup"><span data-stu-id="57f28-117">Message Schemas for Special LOB Operations</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/message-schemas-for-special-lob-operations1.md)  
  
-   [<span data-ttu-id="57f28-118">輪詢作業的訊息結構描述</span><span class="sxs-lookup"><span data-stu-id="57f28-118">Message Schemas for the Polling Operations</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/message-schemas-for-the-polling-operations1.md)  
  
-   [<span data-ttu-id="57f28-119">通知作業的訊息結構描述</span><span class="sxs-lookup"><span data-stu-id="57f28-119">Message Schemas for the Notification Operation</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/message-schemas-for-the-notification-operation2.md)  
  
-   [<span data-ttu-id="57f28-120">ExecuteNonQuery、 ExecuteReader 和 ExecuteScalar 作業的訊息結構描述</span><span class="sxs-lookup"><span data-stu-id="57f28-120">Message Schemas for the ExecuteNonQuery, ExecuteReader, and ExecuteScalar Operations</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/executenonquery-executereader-and-executescalar-message-schemas.md)  
  
-   [<span data-ttu-id="57f28-121">複合作業的訊息結構描述</span><span class="sxs-lookup"><span data-stu-id="57f28-121">Message Schemas for the Composite Operation</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/message-schemas-for-the-composite-operation1.md)  
  