---
title: "交易集結構描述包含一或多個控制區段 ISA，IEA、 GS、 GE |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7589d8f0-c727-47df-afbc-77b0f190f3e2
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ff90a7ea80208f0a69ee8aca5c7593c7b6253c53
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="transaction-set-schema-contains-one-or-more-of-control-segments-isa-iea-gs-ge"></a><span data-ttu-id="9b246-102">交易集結構描述包含一或多個控制區段 ISA IEA、 GS、 GE</span><span class="sxs-lookup"><span data-stu-id="9b246-102">Transaction set schema contains one or more of control segments ISA, IEA, GS, GE</span></span>
## <a name="details"></a><span data-ttu-id="9b246-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="9b246-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9b246-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="9b246-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="9b246-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="9b246-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="9b246-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="9b246-106">Event ID</span></span>|-|  
|<span data-ttu-id="9b246-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="9b246-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="9b246-108">EDI</span><span class="sxs-lookup"><span data-stu-id="9b246-108"> EDI</span></span>|  
|<span data-ttu-id="9b246-109">元件</span><span class="sxs-lookup"><span data-stu-id="9b246-109">Component</span></span>|<span data-ttu-id="9b246-110">EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="9b246-110">EDI Engine</span></span>|  
|<span data-ttu-id="9b246-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="9b246-111">Symbolic Name</span></span>|<span data-ttu-id="9b246-112">SchemaCode114EOtherControlSegmentsPresent</span><span class="sxs-lookup"><span data-stu-id="9b246-112">SchemaCode114EOtherControlSegmentsPresent</span></span>|  
|<span data-ttu-id="9b246-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="9b246-113">Message Text</span></span>|<span data-ttu-id="9b246-114">交易集結構描述包含一或多個控制區段 ISA IEA、 GS、 GE</span><span class="sxs-lookup"><span data-stu-id="9b246-114">Transaction set schema contains one or more of control segments ISA, IEA, GS, GE</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="9b246-115">說明</span><span class="sxs-lookup"><span data-stu-id="9b246-115">Explanation</span></span>  
 <span data-ttu-id="9b246-116">這個錯誤/警告/資訊事件表示接收管線無法處理內送交易集，或傳送管線無法處理外寄交易集，因為交易集的文件結構描述定義至少一個IEA ISA、 GS 或 GE 區段。</span><span class="sxs-lookup"><span data-stu-id="9b246-116">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming transaction set or the send pipeline could not process the outgoing transaction set because the document schema for the transaction set defined at least one ISA, IEA, GS, or GE segment.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="9b246-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="9b246-117">User Action</span></span>  
 <span data-ttu-id="9b246-118">若要解決這個錯誤，解除部署文件結構描述，IEA ISA、 GS 或 GE 區段從移除結構描述，然後再重新部署結構描述。</span><span class="sxs-lookup"><span data-stu-id="9b246-118">To resolve this error, undeploy the document schema, remove the ISA, IEA, GS, or GE segment from the schema, and then redeploy the schema.</span></span>