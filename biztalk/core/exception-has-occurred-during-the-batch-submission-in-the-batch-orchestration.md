---
title: 批次處理協調流程中提交批次期間發生例外狀況 |Microsoft Docs
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
ms.openlocfilehash: 838e9aff43dd260fd4af8e46ca88782c2389dfc7
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36971527"
---
# <a name="an-exception-has-occurred-during-the-batch-submission-in-the-batching-orchestration"></a><span data-ttu-id="817da-102">批次處理協調流程中提交批次期間發生例外狀況</span><span class="sxs-lookup"><span data-stu-id="817da-102">An exception has occurred during the batch submission in the batching orchestration</span></span>
## <a name="details"></a><span data-ttu-id="817da-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="817da-103">Details</span></span>  
  
|                 |                                                                                                                     |
|-----------------|---------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="817da-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="817da-104">Product Name</span></span>   |                 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                  |
| <span data-ttu-id="817da-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="817da-105">Product Version</span></span> |                             [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                              |
|    <span data-ttu-id="817da-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="817da-106">Event ID</span></span>     |                                                          -                                                          |
|  <span data-ttu-id="817da-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="817da-107">Event Source</span></span>   |               [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="817da-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="817da-108"> EDI</span></span>                |
|    <span data-ttu-id="817da-109">元件</span><span class="sxs-lookup"><span data-stu-id="817da-109">Component</span></span>    |                                                   <span data-ttu-id="817da-110">批次引擎</span><span class="sxs-lookup"><span data-stu-id="817da-110">Batching Engine</span></span>                                                   |
|  <span data-ttu-id="817da-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="817da-111">Symbolic Name</span></span>  |                                                  <span data-ttu-id="817da-112">ExceptionOccured</span><span class="sxs-lookup"><span data-stu-id="817da-112">ExceptionOccured</span></span>                                                   |
|  <span data-ttu-id="817da-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="817da-113">Message Text</span></span>   | <span data-ttu-id="817da-114">在批次處理協調流程中提交批次期間發生例外狀況。</span><span class="sxs-lookup"><span data-stu-id="817da-114">An exception has occured during the batch submission in the batching Orchestration.</span></span> <span data-ttu-id="817da-115">批次識別碼 = {0}，ErrorMessage {1}</span><span class="sxs-lookup"><span data-stu-id="817da-115">Batch Id= {0}, ErrorMessage {1}</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="817da-116">說明</span><span class="sxs-lookup"><span data-stu-id="817da-116">Explanation</span></span>  
 <span data-ttu-id="817da-117">這個錯誤/警告/資訊事件表示，批次處理協調流程無法將批次項目加入批次因為 ErrorMessage 欄位中指定的錯誤情況。</span><span class="sxs-lookup"><span data-stu-id="817da-117">This Error/Warning/Information event indicates that the batching orchestration could not add a batch element to a batch because of the error condition indicated in the ErrorMessage field.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="817da-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="817da-118">User Action</span></span>  
 <span data-ttu-id="817da-119">若要解決這個錯誤，判斷錯誤狀況是從 [訊息] 欄位、 解決錯誤，然後重新提交訊息。</span><span class="sxs-lookup"><span data-stu-id="817da-119">To resolve this error, determine what the error condition is from the ErrorMessage field, resolve the error, and then resubmit the message.</span></span>