---
title: "訊息和訊息結構描述，BizTalk adapter for Siebel eBusiness Application |Microsoft 文件"
description: "Siebel 配接器在 BizTalk 配接器組件 (BAP) 中使用的訊息和資料類型的 XML 結構"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6b4da884-89b0-4ab1-a728-c5569088a993
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 294662793fc8103813b582d1b0d84db4447b0e7e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="messages-and-message-schemas-for-biztalk-adapter-for-siebel-ebusiness-applications"></a><span data-ttu-id="47828-103">訊息和訊息結構描述，BizTalk adapter for Siebel eBusiness 應用程式</span><span class="sxs-lookup"><span data-stu-id="47828-103">Messages and Message Schemas for BizTalk Adapter for Siebel eBusiness Applications</span></span>

## <a name="overview"></a><span data-ttu-id="47828-104">概觀</span><span class="sxs-lookup"><span data-stu-id="47828-104">Overview</span></span>
<span data-ttu-id="47828-105">[!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)]是[!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]自訂繫結。</span><span class="sxs-lookup"><span data-stu-id="47828-105">The [!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)] is a [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] custom binding.</span></span> <span data-ttu-id="47828-106">它會公開 Siebel 系統的叫用應用程式的作業。</span><span class="sxs-lookup"><span data-stu-id="47828-106">It exposes operations that applications can invoke on a Siebel system.</span></span> <span data-ttu-id="47828-107">這些作業會叫用透過通道傳送 SOAP 訊息。</span><span class="sxs-lookup"><span data-stu-id="47828-107">These operations are invoked by sending SOAP messages over a channel.</span></span> <span data-ttu-id="47828-108">如果需要回應，它會傳回 SOAP 訊息中透過相同的通道。</span><span class="sxs-lookup"><span data-stu-id="47828-108">If a response is required, it is returned in a SOAP message over the same channel.</span></span>  
  
 <span data-ttu-id="47828-109">做為[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]服務[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]會公開其作業和資料類型的中繼資料，以使用標準[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]機制。</span><span class="sxs-lookup"><span data-stu-id="47828-109">As a [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] service, the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] exposes metadata for its operations and data types by using standard [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] mechanisms.</span></span> <span data-ttu-id="47828-110">本主題中的各節描述 XML 訊息的結構和資料型別[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]使用。</span><span class="sxs-lookup"><span data-stu-id="47828-110">The sections in this topic describe the XML structure of the messages and data types that the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="47828-111">本節內容</span><span class="sxs-lookup"><span data-stu-id="47828-111">In This Section</span></span>  
  
-   [<span data-ttu-id="47828-112">基本的 Siebel 資料型別</span><span class="sxs-lookup"><span data-stu-id="47828-112">Basic Siebel Data Types</span></span>](basic-siebel-data-types.md)  
  
-   [<span data-ttu-id="47828-113">商務元件操作的訊息結構描述</span><span class="sxs-lookup"><span data-stu-id="47828-113">Message Schemas for Business Component Operations</span></span>](message-schemas-for-business-component-operations.md)  
  
-   [<span data-ttu-id="47828-114">商務服務作業的訊息結構描述</span><span class="sxs-lookup"><span data-stu-id="47828-114">Message Schemas for Business Service Operations</span></span>](message-schemas-for-business-service-operations.md)  
  
-   [<span data-ttu-id="47828-115">挑選清單作業的訊息結構描述</span><span class="sxs-lookup"><span data-stu-id="47828-115">Message Schema for Picklist Operations</span></span>](message-schema-for-picklist-operations.md)  
  
-   [<span data-ttu-id="47828-116">訊息版本控制支援</span><span class="sxs-lookup"><span data-stu-id="47828-116">Message Versioning Support</span></span>](message-versioning-support2.md)  
  
