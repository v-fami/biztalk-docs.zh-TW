---
title: 在 GS 和 GE 的群組控制編號不相符 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e2419f61-2717-4347-a4be-54362330c7e3
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f162bdcfd76d25a37e196c37c25cbb970fb27155
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36993631"
---
# <a name="group-control-number-in-gs-and-ge-do-not-match"></a><span data-ttu-id="73a80-102">GS 和 GE 的群組控制編號不相符</span><span class="sxs-lookup"><span data-stu-id="73a80-102">Group control number in GS and GE do not match</span></span>
## <a name="details"></a><span data-ttu-id="73a80-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="73a80-103">Details</span></span>  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  <span data-ttu-id="73a80-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="73a80-104">Product Name</span></span>   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| <span data-ttu-id="73a80-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="73a80-105">Product Version</span></span> |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    <span data-ttu-id="73a80-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="73a80-106">Event ID</span></span>     |                                           -                                            |
|  <span data-ttu-id="73a80-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="73a80-107">Event Source</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="73a80-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="73a80-108"> EDI</span></span> |
|    <span data-ttu-id="73a80-109">元件</span><span class="sxs-lookup"><span data-stu-id="73a80-109">Component</span></span>    |                                       <span data-ttu-id="73a80-110">將 EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="73a80-110">EDI Engine</span></span>                                       |
|  <span data-ttu-id="73a80-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="73a80-111">Symbolic Name</span></span>  |                         <span data-ttu-id="73a80-112">X12FaControlNumberMismatchDescription</span><span class="sxs-lookup"><span data-stu-id="73a80-112">X12FaControlNumberMismatchDescription</span></span>                          |
|  <span data-ttu-id="73a80-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="73a80-113">Message Text</span></span>   |                     <span data-ttu-id="73a80-114">GS 和 GE 的群組控制編號不相符</span><span class="sxs-lookup"><span data-stu-id="73a80-114">Group control number in GS and GE do not match</span></span>                     |
  
## <a name="explanation"></a><span data-ttu-id="73a80-115">說明</span><span class="sxs-lookup"><span data-stu-id="73a80-115">Explanation</span></span>  
 <span data-ttu-id="73a80-116">這個錯誤/警告/資訊事件表示接收管線無法處理內送 X12 交換，因為 GS06 和 GE02 交換的欄位中包含的控制編號並沒有相同的值。</span><span class="sxs-lookup"><span data-stu-id="73a80-116">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming X12 interchange because the control numbers contained in the GS06 and GE02 fields of the  interchange do not have the same value.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="73a80-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="73a80-117">User Action</span></span>  
 <span data-ttu-id="73a80-118">若要解決這個錯誤，請確定群組控制編號的交換 GS06 和 GE02 欄位中包含有相同的值，並就會重新傳送交換。</span><span class="sxs-lookup"><span data-stu-id="73a80-118">To resolve this error, make sure that the group control numbers contained in the GS06 and GE02 fields of the interchange have the same value, and then have the interchange resent.</span></span>