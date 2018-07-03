---
title: 重複次數多於需要 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fec52b5b-e95f-479e-8922-dcf17dcefee7
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4ac4649ea88756ba63393155ca8910437567fbd1
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37024036"
---
# <a name="repeats-more-than-required"></a><span data-ttu-id="9bd13-102">重複次數多於需要</span><span class="sxs-lookup"><span data-stu-id="9bd13-102">Repeats more than required</span></span>
## <a name="details"></a><span data-ttu-id="9bd13-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="9bd13-103">Details</span></span>  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  <span data-ttu-id="9bd13-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="9bd13-104">Product Name</span></span>   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| <span data-ttu-id="9bd13-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="9bd13-105">Product Version</span></span> |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    <span data-ttu-id="9bd13-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="9bd13-106">Event ID</span></span>     |                                           -                                            |
|  <span data-ttu-id="9bd13-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="9bd13-107">Event Source</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="9bd13-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="9bd13-108"> EDI</span></span> |
|    <span data-ttu-id="9bd13-109">元件</span><span class="sxs-lookup"><span data-stu-id="9bd13-109">Component</span></span>    |                                       <span data-ttu-id="9bd13-110">將 EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="9bd13-110">EDI Engine</span></span>                                       |
|  <span data-ttu-id="9bd13-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="9bd13-111">Symbolic Name</span></span>  |                        <span data-ttu-id="9bd13-112">X12FeRepeatsMoreThanRequiredDescription</span><span class="sxs-lookup"><span data-stu-id="9bd13-112">X12FeRepeatsMoreThanRequiredDescription</span></span>                         |
|  <span data-ttu-id="9bd13-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="9bd13-113">Message Text</span></span>   |                               <span data-ttu-id="9bd13-114">重複次數多於需要</span><span class="sxs-lookup"><span data-stu-id="9bd13-114">Repeats more than required</span></span>                               |
  
## <a name="explanation"></a><span data-ttu-id="9bd13-115">說明</span><span class="sxs-lookup"><span data-stu-id="9bd13-115">Explanation</span></span>  
 <span data-ttu-id="9bd13-116">這個錯誤/警告/資訊事件表示區段中的 X12 交換的是內部或外部迴圈會重複多次的文件結構描述所要求。</span><span class="sxs-lookup"><span data-stu-id="9bd13-116">This Error/Warning/Information event indicates that segments in an X12 interchange that are either inside or outside of a loop repeated more times than required by the document schema.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="9bd13-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="9bd13-117">User Action</span></span>  
 <span data-ttu-id="9bd13-118">若要解決此錯誤，確定交換中迴圈內外的區段重複結構描述中所指定的次數，然後重新傳送交換。</span><span class="sxs-lookup"><span data-stu-id="9bd13-118">To resolve this error, make sure that the segments that are either inside or outside of a loop in the interchange repeat the numbers of times specified in the schema, and then resend the interchange.</span></span>