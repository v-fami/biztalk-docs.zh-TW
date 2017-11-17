---
title: "訊息和訊息結構描述，BizTalk adapter for mySAP Business Suite |Microsoft 文件"
description: "MySAP 配接器的 BizTalk Server 使用的訊息和資料類型的 XML 結構"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 75ea5c27-8297-47bf-bcfd-503870349189
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9db6ec6b0fbea7ce5c8f90158126d52cbc7530ca
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="messages-and-message-schemas-for-biztalk-adapter-for-mysap-business-suite"></a><span data-ttu-id="9c37e-103">訊息和訊息結構描述，BizTalk adapter for mySAP Business Suite</span><span class="sxs-lookup"><span data-stu-id="9c37e-103">Messages and Message Schemas for BizTalk Adapter for mySAP Business Suite</span></span>

## <a name="overview"></a><span data-ttu-id="9c37e-104">概觀</span><span class="sxs-lookup"><span data-stu-id="9c37e-104">Overview</span></span>
<span data-ttu-id="9c37e-105">[!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]是[!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]自訂繫結。</span><span class="sxs-lookup"><span data-stu-id="9c37e-105">The [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] is a [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] custom binding.</span></span> <span data-ttu-id="9c37e-106">它會公開應用程式可以在其上叫用，接著，可以呼叫應用程式上的作業。</span><span class="sxs-lookup"><span data-stu-id="9c37e-106">It exposes operations that applications can invoke on it and that it can, in turn, invoke on applications.</span></span> <span data-ttu-id="9c37e-107">這些作業會叫用透過通道傳送 SOAP 訊息。</span><span class="sxs-lookup"><span data-stu-id="9c37e-107">These operations are invoked by sending SOAP messages over a channel.</span></span> <span data-ttu-id="9c37e-108">如果需要回應，它會傳回 SOAP 訊息中透過相同的通道。</span><span class="sxs-lookup"><span data-stu-id="9c37e-108">If a response is required, it is returned in a SOAP message over the same channel.</span></span>  
  
 <span data-ttu-id="9c37e-109">做為[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]服務[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]會公開其作業和資料類型的中繼資料，以使用標準[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]機制。</span><span class="sxs-lookup"><span data-stu-id="9c37e-109">As a [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] service, the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] exposes metadata for its operations and data types by using standard [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] mechanisms.</span></span> <span data-ttu-id="9c37e-110">本主題中的各節描述 XML 訊息的結構和資料型別[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]使用。</span><span class="sxs-lookup"><span data-stu-id="9c37e-110">The sections in this topic describe the XML structure of the messages and data types that the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9c37e-111">本節內容</span><span class="sxs-lookup"><span data-stu-id="9c37e-111">In This Section</span></span>  
  
-   [<span data-ttu-id="9c37e-112">基本的 SAP 資料類型</span><span class="sxs-lookup"><span data-stu-id="9c37e-112">Basic SAP Data Types</span></span>](../../adapters-and-accelerators/adapter-sap/basic-sap-data-types.md)  
  
-   [<span data-ttu-id="9c37e-113">自訂 Rfc 的資料類型對應</span><span class="sxs-lookup"><span data-stu-id="9c37e-113">Data Type Mapping for Custom RFCs</span></span>](../../adapters-and-accelerators/adapter-sap/data-type-mapping-for-custom-rfcs.md)  
  
-   [<span data-ttu-id="9c37e-114">IDOC 作業的訊息結構描述</span><span class="sxs-lookup"><span data-stu-id="9c37e-114">Message Schemas for IDOC Operations</span></span>](../../adapters-and-accelerators/adapter-sap/message-schemas-for-idoc-operations.md)  
  
-   [<span data-ttu-id="9c37e-115">訊息內容屬性，用於接收 Idoc</span><span class="sxs-lookup"><span data-stu-id="9c37e-115">Message Context Properties for Receiving IDOCs</span></span>](../../adapters-and-accelerators/adapter-sap/message-context-properties-for-receiving-idocs.md)  
  
-   [<span data-ttu-id="9c37e-116">RFC 作業的訊息結構描述</span><span class="sxs-lookup"><span data-stu-id="9c37e-116">Message Schemas for RFC Operations</span></span>](../../adapters-and-accelerators/adapter-sap/message-schemas-for-rfc-operations.md)  
  
-   [<span data-ttu-id="9c37e-117">TRFC 作業的訊息結構描述</span><span class="sxs-lookup"><span data-stu-id="9c37e-117">Message Schemas for tRFC Operations</span></span>](../../adapters-and-accelerators/adapter-sap/message-schemas-for-trfc-operations.md)  
  
-   [<span data-ttu-id="9c37e-118">BAPI 作業的訊息結構描述</span><span class="sxs-lookup"><span data-stu-id="9c37e-118">Message Schemas for BAPI Operations</span></span>](../../adapters-and-accelerators/adapter-sap/message-schemas-for-bapi-operations.md)  
  
-   [<span data-ttu-id="9c37e-119">特殊作業</span><span class="sxs-lookup"><span data-stu-id="9c37e-119">Special Operations</span></span>](../../adapters-and-accelerators/adapter-sap/special-operations.md)  
  
-   [<span data-ttu-id="9c37e-120">訊息版本控制支援</span><span class="sxs-lookup"><span data-stu-id="9c37e-120">Message Versioning Support</span></span>](../../adapters-and-accelerators/adapter-sap/message-versioning-support1.md)  
  
