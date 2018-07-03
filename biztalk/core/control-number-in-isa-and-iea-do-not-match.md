---
title: ISA 和 IEA 中的控制編號不相符 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6f9091ea-460b-464b-acd5-8dc0488b61e5
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a1fa574e63444740e85cbdd9bf8ac411c495b24f
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37016226"
---
# <a name="control-number-in-isa-and-iea-do-not-match"></a><span data-ttu-id="04b5f-102">ISA 和 IEA 中的控制編號不相符</span><span class="sxs-lookup"><span data-stu-id="04b5f-102">Control Number in ISA and IEA do not match</span></span>
## <a name="details"></a><span data-ttu-id="04b5f-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="04b5f-103">Details</span></span>  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  <span data-ttu-id="04b5f-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="04b5f-104">Product Name</span></span>   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| <span data-ttu-id="04b5f-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="04b5f-105">Product Version</span></span> |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    <span data-ttu-id="04b5f-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="04b5f-106">Event ID</span></span>     |                                           -                                            |
|  <span data-ttu-id="04b5f-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="04b5f-107">Event Source</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="04b5f-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="04b5f-108"> EDI</span></span> |
|    <span data-ttu-id="04b5f-109">元件</span><span class="sxs-lookup"><span data-stu-id="04b5f-109">Component</span></span>    |                                       <span data-ttu-id="04b5f-110">AS2 引擎</span><span class="sxs-lookup"><span data-stu-id="04b5f-110">AS2 Engine</span></span>                                       |
|  <span data-ttu-id="04b5f-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="04b5f-111">Symbolic Name</span></span>  |                                           -                                            |
|  <span data-ttu-id="04b5f-112">訊息文字</span><span class="sxs-lookup"><span data-stu-id="04b5f-112">Message Text</span></span>   |                       <span data-ttu-id="04b5f-113">ISA 和 IEA 中的控制編號不相符</span><span class="sxs-lookup"><span data-stu-id="04b5f-113">Control Number in ISA and IEA do not match</span></span>                       |
  
## <a name="explanation"></a><span data-ttu-id="04b5f-114">說明</span><span class="sxs-lookup"><span data-stu-id="04b5f-114">Explanation</span></span>  
 <span data-ttu-id="04b5f-115">這個錯誤/警告/資訊事件表示，由於包含在內送交換之 [ISA13] 和 [IEA02] 欄位中的交換控制編號值不同，因此 AS2 接收管線無法處理該交換。</span><span class="sxs-lookup"><span data-stu-id="04b5f-115">This Error/Warning/Information event indicates that the AS2 receive pipeline could not process the incoming interchange because the interchange control numbers contained in the ISA13 and IEA02 fields of the interchange do not have the same value.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="04b5f-116">使用者動作</span><span class="sxs-lookup"><span data-stu-id="04b5f-116">User Action</span></span>  
 <span data-ttu-id="04b5f-117">若要解決這個錯誤，請確定具有相同的值，內含在 ISA13 和 IEA02 欄位，交換的交換控制編號，並就會重新傳送交換。</span><span class="sxs-lookup"><span data-stu-id="04b5f-117">To resolve this error, make sure that the interchange control numbers contained in the ISA13 and IEA02 fields of the interchange have the same value, and then have the interchange resent.</span></span>