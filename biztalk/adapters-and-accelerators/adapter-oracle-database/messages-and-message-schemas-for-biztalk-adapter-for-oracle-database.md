---
title: 訊息與 BizTalk adapter for Oracle 資料庫的訊息結構描述 |Microsoft 文件
description: BizTalk Server 的 Oracle 資料庫配接器使用的訊息和資料類型的 XML 結構
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fee0a531-b1e6-4b99-bb79-45368c401395
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bda5ed06470e051dc1f0bdf4595a1539aab6e6bc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22214302"
---
# <a name="messages-and-message-schemas-for-biztalk-adapter-for-oracle-database"></a><span data-ttu-id="eef92-103">訊息和訊息結構描述，BizTalk adapter for Oracle 資料庫</span><span class="sxs-lookup"><span data-stu-id="eef92-103">Messages and Message Schemas for BizTalk Adapter for Oracle Database</span></span>

## <a name="overview"></a><span data-ttu-id="eef92-104">概觀</span><span class="sxs-lookup"><span data-stu-id="eef92-104">Overview</span></span>
<span data-ttu-id="eef92-105">[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]是[!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]自訂繫結。</span><span class="sxs-lookup"><span data-stu-id="eef92-105">The [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] is a [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] custom binding.</span></span> <span data-ttu-id="eef92-106">它會公開應用程式可以在其上叫用，接著，可以呼叫應用程式上的作業。</span><span class="sxs-lookup"><span data-stu-id="eef92-106">It exposes operations that applications can invoke on it and that it can, in turn, invoke on applications.</span></span> <span data-ttu-id="eef92-107">這些作業會叫用透過通道傳送 SOAP 訊息。</span><span class="sxs-lookup"><span data-stu-id="eef92-107">These operations are invoked by sending SOAP messages over a channel.</span></span> <span data-ttu-id="eef92-108">如果需要回應，它會傳回 SOAP 訊息中透過相同的通道。</span><span class="sxs-lookup"><span data-stu-id="eef92-108">If a response is required, it is returned in a SOAP message over the same channel.</span></span>  
  
 <span data-ttu-id="eef92-109">做為[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]服務[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]會公開其作業和資料類型的中繼資料，以使用標準[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]機制。</span><span class="sxs-lookup"><span data-stu-id="eef92-109">As a [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] service, the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] exposes metadata for its operations and data types by using standard [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] mechanisms.</span></span> <span data-ttu-id="eef92-110">本主題中的各節描述 XML 訊息的結構和資料型別[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]使用。</span><span class="sxs-lookup"><span data-stu-id="eef92-110">The sections in this topic describe the XML structure of the messages and data types that the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="eef92-111">本節內容</span><span class="sxs-lookup"><span data-stu-id="eef92-111">In This Section</span></span>  
  
-   [<span data-ttu-id="eef92-112">基本的 Oracle 資料類型</span><span class="sxs-lookup"><span data-stu-id="eef92-112">Basic Oracle Data Types</span></span>](../../adapters-and-accelerators/adapter-oracle-database/basic-oracle-data-types1.md)  
  
-   [<span data-ttu-id="eef92-113">訊息結構描述基本的插入、 更新、 刪除和選取資料表和檢視表上的作業</span><span class="sxs-lookup"><span data-stu-id="eef92-113">Message Schemas for the Basic Insert, Update, Delete, and Select Operations on Tables and Views</span></span>](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-insert-update-delete-and-select-on-tables-and-views.md)  
  
-   [<span data-ttu-id="eef92-114">特殊 LOB 作業的訊息結構描述</span><span class="sxs-lookup"><span data-stu-id="eef92-114">Message Schemas for Special LOB Operations</span></span>](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-special-lob-operations2.md)  
  
-   [<span data-ttu-id="eef92-115">函數和程序的訊息結構描述</span><span class="sxs-lookup"><span data-stu-id="eef92-115">Message Schemas for Functions and Procedures</span></span>](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-functions-and-procedures.md)  
  
-   [<span data-ttu-id="eef92-116">REF CURSOR 的訊息結構描述</span><span class="sxs-lookup"><span data-stu-id="eef92-116">Message Schemas for REF CURSORS</span></span>](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-ref-cursors.md)  
  
-   [<span data-ttu-id="eef92-117">記錄類型的訊息結構描述</span><span class="sxs-lookup"><span data-stu-id="eef92-117">Message Schemas for RECORD Types</span></span>](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-record-types.md)  
  
-   [<span data-ttu-id="eef92-118">SQLEXECUTE 操作的訊息結構描述</span><span class="sxs-lookup"><span data-stu-id="eef92-118">Message Schemas for the SQLEXECUTE Operation</span></span>](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-the-sqlexecute-operation.md)  
  
-   [<span data-ttu-id="eef92-119">輪詢作業的訊息結構描述</span><span class="sxs-lookup"><span data-stu-id="eef92-119">Message Schemas for the Polling Operations</span></span>](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-the-polling-operations2.md)  
  
-   [<span data-ttu-id="eef92-120">複合作業的訊息結構描述</span><span class="sxs-lookup"><span data-stu-id="eef92-120">Message Schemas for the Composite Operation</span></span>](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-the-composite-operation2.md)  
  
-   [<span data-ttu-id="eef92-121">通知作業的訊息結構描述</span><span class="sxs-lookup"><span data-stu-id="eef92-121">Message Schemas for the Notification Operation</span></span>](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-the-notification-operation1.md)  
  
