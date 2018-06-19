---
title: 項目具有無效的結構 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bb94843c-cd21-48e3-ba30-aed0518b4d78
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7b825fb0d2f5b4fe985a2024b1c97e21f4308b58
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22278158"
---
# <a name="the-element-has-an-invalid-structure"></a><span data-ttu-id="2d7be-102">項目具有無效的結構</span><span class="sxs-lookup"><span data-stu-id="2d7be-102">The element has an invalid structure</span></span>
## <a name="details"></a><span data-ttu-id="2d7be-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="2d7be-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2d7be-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="2d7be-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="2d7be-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="2d7be-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="2d7be-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="2d7be-106">Event ID</span></span>|-|  
|<span data-ttu-id="2d7be-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="2d7be-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="2d7be-108">EDI</span><span class="sxs-lookup"><span data-stu-id="2d7be-108"> EDI</span></span>|  
|<span data-ttu-id="2d7be-109">元件</span><span class="sxs-lookup"><span data-stu-id="2d7be-109">Component</span></span>|<span data-ttu-id="2d7be-110">EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="2d7be-110">EDI Engine</span></span>|  
|<span data-ttu-id="2d7be-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="2d7be-111">Symbolic Name</span></span>|<span data-ttu-id="2d7be-112">X12NseStructurallyInvalidElementDescription</span><span class="sxs-lookup"><span data-stu-id="2d7be-112">X12NseStructurallyInvalidElementDescription</span></span>|  
|<span data-ttu-id="2d7be-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="2d7be-113">Message Text</span></span>|<span data-ttu-id="2d7be-114">項目 '{0}' 具有無效的結構</span><span class="sxs-lookup"><span data-stu-id="2d7be-114">The element '{0}' has an invalid structure</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="2d7be-115">說明</span><span class="sxs-lookup"><span data-stu-id="2d7be-115">Explanation</span></span>  
 <span data-ttu-id="2d7be-116">這個錯誤/警告/資訊事件表示接收管線無法處理內送的交換，或傳送管線無法處理外寄交換，因為沒有適用於所指定的結構資料元素。結構描述。</span><span class="sxs-lookup"><span data-stu-id="2d7be-116">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming interchange, or the send pipeline could not process the outgoing interchange, because a data element did not have the structure specified by the applicable schema.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="2d7be-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="2d7be-117">User Action</span></span>  
 <span data-ttu-id="2d7be-118">若要解決這個錯誤，在外寄交換中，修正資料元素的結構，或具有寄件者的交換修正內送的交換中的資料元素的結構，使其符合文件結構描述。</span><span class="sxs-lookup"><span data-stu-id="2d7be-118">To resolve this error, fix the structure of the data element in the outgoing interchange, or have the sender of the interchange fix the structure of the data element in the incoming interchange, so that it conforms to the document schema.</span></span>