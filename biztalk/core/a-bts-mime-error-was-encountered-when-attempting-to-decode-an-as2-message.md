---
title: "嘗試將 AS2 訊息解碼時發生 BTS MIME 錯誤 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 65cb5ece-78e4-4b83-b126-4d8c588b2c61
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 096696f4420150cdd53f8fe561460d243c1bb018
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
---
# <a name="a-bts-mime-error-was-encountered-when-attempting-to-decode-an-as2-message"></a><span data-ttu-id="99586-102">嘗試將 AS2 訊息解碼時發生 BTS MIME 錯誤</span><span class="sxs-lookup"><span data-stu-id="99586-102">A BTS MIME error was encountered when attempting to decode an AS2 message</span></span>
## <a name="details"></a><span data-ttu-id="99586-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="99586-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="99586-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="99586-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="99586-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="99586-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="99586-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="99586-106">Event ID</span></span>|-|  
|<span data-ttu-id="99586-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="99586-107">Event Source</span></span>|<span data-ttu-id="99586-108">BizTalk Server EDI</span><span class="sxs-lookup"><span data-stu-id="99586-108">BizTalk Server EDI</span></span>|  
|<span data-ttu-id="99586-109">元件</span><span class="sxs-lookup"><span data-stu-id="99586-109">Component</span></span>|<span data-ttu-id="99586-110">AS2 引擎</span><span class="sxs-lookup"><span data-stu-id="99586-110">AS2 Engine</span></span>|  
|<span data-ttu-id="99586-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="99586-111">Symbolic Name</span></span>|-|  
|<span data-ttu-id="99586-112">訊息文字</span><span class="sxs-lookup"><span data-stu-id="99586-112">Message Text</span></span>|<span data-ttu-id="99586-113">嘗試將 AS2 訊息解碼時發生 BTS MIME 錯誤。</span><span class="sxs-lookup"><span data-stu-id="99586-113">A BTS MIME error was encountered when attempting to decode an AS2 message.</span></span>  <span data-ttu-id="99586-114">AS2-從: {0}，AS2-以： {1}，MessageId: {2}，錯誤： {3}</span><span class="sxs-lookup"><span data-stu-id="99586-114">AS2-From: {0}, AS2-To: {1}, MessageId: {2}, Error: {3}</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="99586-115">說明</span><span class="sxs-lookup"><span data-stu-id="99586-115">Explanation</span></span>  
 <span data-ttu-id="99586-116">當使用 BizTalk MIME 元件處理某些部分的MIME 處理時會發生此錯誤。</span><span class="sxs-lookup"><span data-stu-id="99586-116">This error is encountered when using the BizTalk MIME component to handle part of the MIME processing.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="99586-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="99586-117">User Action</span></span>  
 <span data-ttu-id="99586-118">完整的錯誤訊息提供 MIME 元件發生之問題的資訊。</span><span class="sxs-lookup"><span data-stu-id="99586-118">The full error message provides the information about the problem encountered by the MIME component.</span></span> <span data-ttu-id="99586-119">請參閱 BTS MIME 錯誤資訊以便診斷問題 （這是因為 AS2 元件會使用 BizTalk MIME 元件部分的 MIME 處理）。</span><span class="sxs-lookup"><span data-stu-id="99586-119">Refer to the BTS MIME error information for diagnosis of the problem (this is because the AS2 components use the BizTalk MIME components for part of the MIME processing).</span></span>