---
title: "尋找開始元素時找不到結束項目 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f7690744-a795-47cc-bc66-a0314a4cc320
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9dacaa096b15a6f2969ed56b5bac2138876a6095
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="an-end-element-was-found-while-looking-for-start-element"></a><span data-ttu-id="0f335-102">尋找開始元素時找到結尾元素</span><span class="sxs-lookup"><span data-stu-id="0f335-102">An End Element was found while looking for Start Element</span></span>
## <a name="details"></a><span data-ttu-id="0f335-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="0f335-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="0f335-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="0f335-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="0f335-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="0f335-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="0f335-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="0f335-106">Event ID</span></span>|-|  
|<span data-ttu-id="0f335-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="0f335-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="0f335-108">EDI</span><span class="sxs-lookup"><span data-stu-id="0f335-108"> EDI</span></span>|  
|<span data-ttu-id="0f335-109">元件</span><span class="sxs-lookup"><span data-stu-id="0f335-109">Component</span></span>|<span data-ttu-id="0f335-110">EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="0f335-110">EDI Engine</span></span>|  
|<span data-ttu-id="0f335-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="0f335-111">Symbolic Name</span></span>|<span data-ttu-id="0f335-112">EndElementFoundWhenLookingForStartElement</span><span class="sxs-lookup"><span data-stu-id="0f335-112">EndElementFoundWhenLookingForStartElement</span></span>|  
|<span data-ttu-id="0f335-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="0f335-113">Message Text</span></span>|<span data-ttu-id="0f335-114">找到名稱為 {0} EndElement，尋找與名稱 {1}，在深度 {2} StartElement 時</span><span class="sxs-lookup"><span data-stu-id="0f335-114">An EndElement with name {0} was found, while looking for StartElement with name {1}, at depth {2}</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="0f335-115">說明</span><span class="sxs-lookup"><span data-stu-id="0f335-115">Explanation</span></span>  
 <span data-ttu-id="0f335-116">這個錯誤/警告/資訊事件表示，BizTalk Server 無法處理內送 XML 訊息 （之後剖析） 或外寄 XML 訊息 （在之前序列化） 因為 XML 訊息驗證失敗。</span><span class="sxs-lookup"><span data-stu-id="0f335-116">This Error/Warning/Information event indicates that BizTalk Server could not process an incoming XML message (after parsing) or an outgoing XML message (before serialization) because the XML message failed validation.</span></span> <span data-ttu-id="0f335-117">XML 訊息不包含標頭或資料元素的結束標記。</span><span class="sxs-lookup"><span data-stu-id="0f335-117">The XML message did not contain an end tag for a header or data element.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="0f335-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="0f335-118">User Action</span></span>  
 <span data-ttu-id="0f335-119">若要解決這個錯誤，將適當的結束標記或結尾加入 XML 訊息，然後再重新傳送訊息。</span><span class="sxs-lookup"><span data-stu-id="0f335-119">To resolve this error, add the appropriate end tag or trailer to the XML message, and then resend the message.</span></span>