---
title: 無效的控制標準識別項 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3d2b5a54-7f29-49c9-8bcf-a5b4b6d07ad3
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cadbb2ed9458199433b62ecb918668fda8a1def0
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36966231"
---
# <a name="invalid-control-standard-identifier"></a><span data-ttu-id="958e5-102">無效的控制標準識別項</span><span class="sxs-lookup"><span data-stu-id="958e5-102">Invalid Control Standard Identifier</span></span>
## <a name="details"></a><span data-ttu-id="958e5-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="958e5-103">Details</span></span>  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  <span data-ttu-id="958e5-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="958e5-104">Product Name</span></span>   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| <span data-ttu-id="958e5-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="958e5-105">Product Version</span></span> |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    <span data-ttu-id="958e5-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="958e5-106">Event ID</span></span>     |                                           -                                            |
|  <span data-ttu-id="958e5-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="958e5-107">Event Source</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="958e5-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="958e5-108"> EDI</span></span> |
|    <span data-ttu-id="958e5-109">元件</span><span class="sxs-lookup"><span data-stu-id="958e5-109">Component</span></span>    |                                       <span data-ttu-id="958e5-110">將 EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="958e5-110">EDI Engine</span></span>                                       |
|  <span data-ttu-id="958e5-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="958e5-111">Symbolic Name</span></span>  |                   <span data-ttu-id="958e5-112">X12Ta1InvalidControlStandardIdentifierDescription</span><span class="sxs-lookup"><span data-stu-id="958e5-112">X12Ta1InvalidControlStandardIdentifierDescription</span></span>                    |
|  <span data-ttu-id="958e5-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="958e5-113">Message Text</span></span>   |                          <span data-ttu-id="958e5-114">無效的控制標準識別項</span><span class="sxs-lookup"><span data-stu-id="958e5-114">Invalid Control Standard Identifier</span></span>                           |
  
## <a name="explanation"></a><span data-ttu-id="958e5-115">說明</span><span class="sxs-lookup"><span data-stu-id="958e5-115">Explanation</span></span>  
 <span data-ttu-id="958e5-116">這個錯誤/警告/資訊事件表示，接收管線無法處理內送交換因為交換控制標準識別項 （欄位 ISA11） 交換中的值不符合列舉型別中的項目指定由結構描述。</span><span class="sxs-lookup"><span data-stu-id="958e5-116">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming interchange because the value of the interchange control standards identifier (field ISA11) in the interchange did not match an entry in the enumeration specified by the schema.</span></span> <span data-ttu-id="958e5-117">結構描述是 x12serviceschema EdifactServiceSchema BaseArtifacts.dll 中。</span><span class="sxs-lookup"><span data-stu-id="958e5-117">The schema is the X12ServiceSchema or the EdifactServiceSchema in BaseArtifacts.dll.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="958e5-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="958e5-118">User Action</span></span>  
 <span data-ttu-id="958e5-119">若要解決這個錯誤，請確定交換中使用的交換控制標準識別項符合 ISA11 欄位中，列舉型別中的項目，然後重新傳送交換。</span><span class="sxs-lookup"><span data-stu-id="958e5-119">To resolve this error, make sure that the interchange control standards identifier used in the interchange matches an entry in the enumeration for the ISA11 field, and then have the interchange resent.</span></span>