---
title: 尋找開始項目時，找到結束項目 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f7690744-a795-47cc-bc66-a0314a4cc320
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2e200f4ffd8d822a5c2bb1a0bad74a60e84a408a
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36992429"
---
# <a name="an-end-element-was-found-while-looking-for-start-element"></a><span data-ttu-id="c88c3-102">尋找開始元素時找到結尾元素</span><span class="sxs-lookup"><span data-stu-id="c88c3-102">An End Element was found while looking for Start Element</span></span>
## <a name="details"></a><span data-ttu-id="c88c3-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="c88c3-103">Details</span></span>  
  
|                 |                                                                                                   |
|-----------------|---------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="c88c3-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="c88c3-104">Product Name</span></span>   |        [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]         |
| <span data-ttu-id="c88c3-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="c88c3-105">Product Version</span></span> |                    [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                     |
|    <span data-ttu-id="c88c3-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="c88c3-106">Event ID</span></span>     |                                                 -                                                 |
|  <span data-ttu-id="c88c3-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="c88c3-107">Event Source</span></span>   |      [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="c88c3-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="c88c3-108"> EDI</span></span>       |
|    <span data-ttu-id="c88c3-109">元件</span><span class="sxs-lookup"><span data-stu-id="c88c3-109">Component</span></span>    |                                            <span data-ttu-id="c88c3-110">將 EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="c88c3-110">EDI Engine</span></span>                                             |
|  <span data-ttu-id="c88c3-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="c88c3-111">Symbolic Name</span></span>  |                             <span data-ttu-id="c88c3-112">EndElementFoundWhenLookingForStartElement</span><span class="sxs-lookup"><span data-stu-id="c88c3-112">EndElementFoundWhenLookingForStartElement</span></span>                             |
|  <span data-ttu-id="c88c3-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="c88c3-113">Message Text</span></span>   | <span data-ttu-id="c88c3-114">名稱的 EndElement{0}找不到，以名稱尋找 StartElement 時{1}，深度 {2}</span><span class="sxs-lookup"><span data-stu-id="c88c3-114">An EndElement with name {0} was found, while looking for StartElement with name {1}, at depth {2}</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="c88c3-115">說明</span><span class="sxs-lookup"><span data-stu-id="c88c3-115">Explanation</span></span>  
 <span data-ttu-id="c88c3-116">這個錯誤/警告/資訊事件表示，BizTalk Server 無法處理內送 XML 訊息 （之後剖析） 或外寄 XML 訊息 （在之前序列化） 因為 XML 訊息驗證失敗。</span><span class="sxs-lookup"><span data-stu-id="c88c3-116">This Error/Warning/Information event indicates that BizTalk Server could not process an incoming XML message (after parsing) or an outgoing XML message (before serialization) because the XML message failed validation.</span></span> <span data-ttu-id="c88c3-117">XML 訊息不包含標頭或資料元素結束標記。</span><span class="sxs-lookup"><span data-stu-id="c88c3-117">The XML message did not contain an end tag for a header or data element.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="c88c3-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="c88c3-118">User Action</span></span>  
 <span data-ttu-id="c88c3-119">若要解決這個錯誤，XML 訊息，並加入適當的結束標記或結尾，並再重新傳送訊息。</span><span class="sxs-lookup"><span data-stu-id="c88c3-119">To resolve this error, add the appropriate end tag or trailer to the XML message, and then resend the message.</span></span>