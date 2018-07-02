---
title: 此項目具有無效的結構 |Microsoft Docs
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
ms.openlocfilehash: b626343ed00add57d6deab4b349a75b4df2164a1
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36987696"
---
# <a name="the-element-has-an-invalid-structure"></a><span data-ttu-id="e434f-102">此項目具有無效的結構</span><span class="sxs-lookup"><span data-stu-id="e434f-102">The element has an invalid structure</span></span>
## <a name="details"></a><span data-ttu-id="e434f-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="e434f-103">Details</span></span>  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  <span data-ttu-id="e434f-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="e434f-104">Product Name</span></span>   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| <span data-ttu-id="e434f-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="e434f-105">Product Version</span></span> |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    <span data-ttu-id="e434f-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="e434f-106">Event ID</span></span>     |                                           -                                            |
|  <span data-ttu-id="e434f-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="e434f-107">Event Source</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="e434f-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="e434f-108"> EDI</span></span> |
|    <span data-ttu-id="e434f-109">元件</span><span class="sxs-lookup"><span data-stu-id="e434f-109">Component</span></span>    |                                       <span data-ttu-id="e434f-110">將 EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="e434f-110">EDI Engine</span></span>                                       |
|  <span data-ttu-id="e434f-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="e434f-111">Symbolic Name</span></span>  |                      <span data-ttu-id="e434f-112">X12NseStructurallyInvalidElementDescription</span><span class="sxs-lookup"><span data-stu-id="e434f-112">X12NseStructurallyInvalidElementDescription</span></span>                       |
|  <span data-ttu-id="e434f-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="e434f-113">Message Text</span></span>   |                       <span data-ttu-id="e434f-114">項目 '{0}' 有無效的結構</span><span class="sxs-lookup"><span data-stu-id="e434f-114">The element '{0}' has an invalid structure</span></span>                       |
  
## <a name="explanation"></a><span data-ttu-id="e434f-115">說明</span><span class="sxs-lookup"><span data-stu-id="e434f-115">Explanation</span></span>  
 <span data-ttu-id="e434f-116">這個錯誤/警告/資訊事件表示接收管線無法處理內送的交換，或傳送管線無法處理外寄交換中，因為資料元素沒有適用於所指定的結構結構描述。</span><span class="sxs-lookup"><span data-stu-id="e434f-116">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming interchange, or the send pipeline could not process the outgoing interchange, because a data element did not have the structure specified by the applicable schema.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="e434f-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="e434f-117">User Action</span></span>  
 <span data-ttu-id="e434f-118">若要解決這個錯誤，在外寄交換中，修正資料元素的結構，或讓傳送者交換修正程式的資料中的項目內送交換中，結構，使其符合文件結構描述。</span><span class="sxs-lookup"><span data-stu-id="e434f-118">To resolve this error, fix the structure of the data element in the outgoing interchange, or have the sender of the interchange fix the structure of the data element in the incoming interchange, so that it conforms to the document schema.</span></span>