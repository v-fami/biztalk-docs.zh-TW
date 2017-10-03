---
title: "結構描述應該有下列順序 ST 區段...SE |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8f4d1c6a-7d48-413a-9ef5-a0c49773dc16
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2563247dc6fc4c092fe2867c6b4d03239c4be7e1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="schema-should-have-segments-in-the-following-order-st--se"></a><span data-ttu-id="ae51d-102">結構描述應該有下列順序 ST 區段...SE</span><span class="sxs-lookup"><span data-stu-id="ae51d-102">Schema should have segments in the following order ST .... SE</span></span>
## <a name="details"></a><span data-ttu-id="ae51d-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="ae51d-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ae51d-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="ae51d-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="ae51d-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="ae51d-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="ae51d-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="ae51d-106">Event ID</span></span>|-|  
|<span data-ttu-id="ae51d-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="ae51d-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="ae51d-108">EDI</span><span class="sxs-lookup"><span data-stu-id="ae51d-108"> EDI</span></span>|  
|<span data-ttu-id="ae51d-109">元件</span><span class="sxs-lookup"><span data-stu-id="ae51d-109">Component</span></span>|<span data-ttu-id="ae51d-110">EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="ae51d-110">EDI Engine</span></span>|  
|<span data-ttu-id="ae51d-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="ae51d-111">Symbolic Name</span></span>|<span data-ttu-id="ae51d-112">SchemaCode116ETransactionSetSchemaStSeOutOfOrder</span><span class="sxs-lookup"><span data-stu-id="ae51d-112">SchemaCode116ETransactionSetSchemaStSeOutOfOrder</span></span>|  
|<span data-ttu-id="ae51d-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="ae51d-113">Message Text</span></span>|<span data-ttu-id="ae51d-114">結構描述應該有下列順序 ST 區段...SE</span><span class="sxs-lookup"><span data-stu-id="ae51d-114">Schema should have segments in the following order ST .... SE</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="ae51d-115">說明</span><span class="sxs-lookup"><span data-stu-id="ae51d-115">Explanation</span></span>  
 <span data-ttu-id="ae51d-116">這個錯誤/警告/資訊事件表示自訂文件結構描述不正確的因為標頭和結尾未以正確的順序。</span><span class="sxs-lookup"><span data-stu-id="ae51d-116">This Error/Warning/Information event indicates that a custom document schema is invalid because the headers and trailers were not in the correct order.</span></span> <span data-ttu-id="ae51d-117">部署結構描述時，BizTalk Server 會執行這項驗證。</span><span class="sxs-lookup"><span data-stu-id="ae51d-117">BizTalk Server performs this validation when the schema is deployed.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="ae51d-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="ae51d-118">User Action</span></span>  
 <span data-ttu-id="ae51d-119">若要解決這個錯誤，變更的自訂文件結構描述，以便與標頭和結尾的正確順序，然後重新部署結構描述。</span><span class="sxs-lookup"><span data-stu-id="ae51d-119">To resolve this error, change the customized document schema so that the headers and trailers are in the correct order, and then redeploy the schema.</span></span>