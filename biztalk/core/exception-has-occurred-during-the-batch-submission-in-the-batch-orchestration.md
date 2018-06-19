---
title: 在批次處理協調流程中的批次提交期間發生例外狀況 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c58b2fa9-d036-4e09-a0f8-77a2f983881a
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7a3e61cc7375acf5d9faf0d72ab36127532c66ae
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22245830"
---
# <a name="an-exception-has-occurred-during-the-batch-submission-in-the-batching-orchestration"></a><span data-ttu-id="455d1-102">在批次處理協調流程中的批次提交期間發生例外狀況</span><span class="sxs-lookup"><span data-stu-id="455d1-102">An exception has occurred during the batch submission in the batching orchestration</span></span>
## <a name="details"></a><span data-ttu-id="455d1-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="455d1-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="455d1-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="455d1-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="455d1-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="455d1-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="455d1-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="455d1-106">Event ID</span></span>|-|  
|<span data-ttu-id="455d1-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="455d1-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="455d1-108">EDI</span><span class="sxs-lookup"><span data-stu-id="455d1-108"> EDI</span></span>|  
|<span data-ttu-id="455d1-109">元件</span><span class="sxs-lookup"><span data-stu-id="455d1-109">Component</span></span>|<span data-ttu-id="455d1-110">批次處理引擎</span><span class="sxs-lookup"><span data-stu-id="455d1-110">Batching Engine</span></span>|  
|<span data-ttu-id="455d1-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="455d1-111">Symbolic Name</span></span>|<span data-ttu-id="455d1-112">ExceptionOccured</span><span class="sxs-lookup"><span data-stu-id="455d1-112">ExceptionOccured</span></span>|  
|<span data-ttu-id="455d1-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="455d1-113">Message Text</span></span>|<span data-ttu-id="455d1-114">在批次處理協調流程中的批次提交期間發生例外狀況。</span><span class="sxs-lookup"><span data-stu-id="455d1-114">An exception has occured during the batch submission in the batching Orchestration.</span></span> <span data-ttu-id="455d1-115">批次識別碼 = {0}，ErrorMessage {1}</span><span class="sxs-lookup"><span data-stu-id="455d1-115">Batch Id= {0}, ErrorMessage {1}</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="455d1-116">說明</span><span class="sxs-lookup"><span data-stu-id="455d1-116">Explanation</span></span>  
 <span data-ttu-id="455d1-117">這個錯誤/警告/資訊事件表示，批次處理協調流程無法加入批次項目至批次因為 ErrorMessage 欄位中指定的錯誤情況。</span><span class="sxs-lookup"><span data-stu-id="455d1-117">This Error/Warning/Information event indicates that the batching orchestration could not add a batch element to a batch because of the error condition indicated in the ErrorMessage field.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="455d1-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="455d1-118">User Action</span></span>  
 <span data-ttu-id="455d1-119">若要解決這個錯誤，判斷錯誤狀況是從 ErrorMessage 欄位，解決錯誤，然後再重新提交訊息。</span><span class="sxs-lookup"><span data-stu-id="455d1-119">To resolve this error, determine what the error condition is from the ErrorMessage field, resolve the error, and then resubmit the message.</span></span>