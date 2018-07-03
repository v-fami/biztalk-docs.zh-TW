---
title: 無效的 AS2-To 標頭接收 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 56cd16b3-511b-4716-8806-817f174f0b0e
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a0bc9fd8043205920f69aec2ca7efbfcc9478724
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37010351"
---
# <a name="invalid-as2-to-header-received"></a><span data-ttu-id="34cb5-102">無效的 AS2-To 標頭接收</span><span class="sxs-lookup"><span data-stu-id="34cb5-102">Invalid AS2-To header received</span></span>
## <a name="details"></a><span data-ttu-id="34cb5-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="34cb5-103">Details</span></span>  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  <span data-ttu-id="34cb5-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="34cb5-104">Product Name</span></span>   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| <span data-ttu-id="34cb5-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="34cb5-105">Product Version</span></span> |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    <span data-ttu-id="34cb5-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="34cb5-106">Event ID</span></span>     |                                           -                                            |
|  <span data-ttu-id="34cb5-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="34cb5-107">Event Source</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="34cb5-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="34cb5-108"> EDI</span></span> |
|    <span data-ttu-id="34cb5-109">元件</span><span class="sxs-lookup"><span data-stu-id="34cb5-109">Component</span></span>    |                                       <span data-ttu-id="34cb5-110">AS2 引擎</span><span class="sxs-lookup"><span data-stu-id="34cb5-110">AS2 Engine</span></span>                                       |
|  <span data-ttu-id="34cb5-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="34cb5-111">Symbolic Name</span></span>  |                          <span data-ttu-id="34cb5-112">InvalidAS2ToNameHeaderReceivedError</span><span class="sxs-lookup"><span data-stu-id="34cb5-112">InvalidAS2ToNameHeaderReceivedError</span></span>                           |
|  <span data-ttu-id="34cb5-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="34cb5-113">Message Text</span></span>   |                      <span data-ttu-id="34cb5-114">收到無效的 AS2-To 標頭。</span><span class="sxs-lookup"><span data-stu-id="34cb5-114">Invalid AS2-To header received.</span></span>  <span data-ttu-id="34cb5-115">值： {0}</span><span class="sxs-lookup"><span data-stu-id="34cb5-115">Value: {0}</span></span>                       |
  
## <a name="explanation"></a><span data-ttu-id="34cb5-116">說明</span><span class="sxs-lookup"><span data-stu-id="34cb5-116">Explanation</span></span>  
 <span data-ttu-id="34cb5-117">這個錯誤/警告/資訊事件表示，接收管線無法處理內送交換，因為值的 AS2-To 標頭訊息中不符合 AS2 RFC 4130 中的規格。</span><span class="sxs-lookup"><span data-stu-id="34cb5-117">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming interchange because the value of the AS2-To header in the message did not conform to the specifications in AS2 RFC 4130.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="34cb5-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="34cb5-118">User Action</span></span>  
 <span data-ttu-id="34cb5-119">若要解決這個錯誤，請確定值，在 AS2-To 標頭的訊息符合 AS2 RFC 4130 第 6.2 節的規格。</span><span class="sxs-lookup"><span data-stu-id="34cb5-119">To resolve this error, make sure that the value in the AS2-To header of the message conforms to the specifications in section 6.2 of AS2 RFC 4130.</span></span>