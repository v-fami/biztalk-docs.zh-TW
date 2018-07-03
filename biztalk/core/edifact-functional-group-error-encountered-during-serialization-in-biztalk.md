---
title: 序列化期間發生的錯誤。 Edifact 功能群組發生下列錯誤 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ed81bc79-d99c-4305-805f-ab38eae91ea0
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0cd5ce1a94a47c5094862decfe1bb1dbb9c1efb0
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36977599"
---
# <a name="error-encountered-during-serialization-the-edifact-functional-group-had-the-following-errors"></a><span data-ttu-id="764aa-103">序列化期間發生的錯誤。</span><span class="sxs-lookup"><span data-stu-id="764aa-103">Error encountered during serialization.</span></span> <span data-ttu-id="764aa-104">Edifact 功能群組發生下列錯誤</span><span class="sxs-lookup"><span data-stu-id="764aa-104">The Edifact functional group had the following errors</span></span>
## <a name="details"></a><span data-ttu-id="764aa-105">詳細資料</span><span class="sxs-lookup"><span data-stu-id="764aa-105">Details</span></span>  
  
|                 |                                                                                                                                                                                     |
|-----------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="764aa-106">產品名稱</span><span class="sxs-lookup"><span data-stu-id="764aa-106">Product Name</span></span>   |                                                 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                                                  |
| <span data-ttu-id="764aa-107">產品版本</span><span class="sxs-lookup"><span data-stu-id="764aa-107">Product Version</span></span> |                                                             [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                                              |
|    <span data-ttu-id="764aa-108">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="764aa-108">Event ID</span></span>     |                                                                                          -                                                                                          |
|  <span data-ttu-id="764aa-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="764aa-109">Event Source</span></span>   |                                               [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="764aa-110"> EDI</span><span class="sxs-lookup"><span data-stu-id="764aa-110"> EDI</span></span>                                                |
|    <span data-ttu-id="764aa-111">元件</span><span class="sxs-lookup"><span data-stu-id="764aa-111">Component</span></span>    |                                                                                     <span data-ttu-id="764aa-112">將 EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="764aa-112">EDI Engine</span></span>                                                                                      |
|  <span data-ttu-id="764aa-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="764aa-113">Symbolic Name</span></span>  |                                                                            <span data-ttu-id="764aa-114">EfactFunctionalGroupSendError</span><span class="sxs-lookup"><span data-stu-id="764aa-114">EfactFunctionalGroupSendError</span></span>                                                                            |
|  <span data-ttu-id="764aa-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="764aa-115">Message Text</span></span>   | <span data-ttu-id="764aa-116">序列化期間發生的錯誤。</span><span class="sxs-lookup"><span data-stu-id="764aa-116">Error encountered during serialization.</span></span> <span data-ttu-id="764aa-117">Edifact 功能群組識別碼 '{0}'，在交換識別碼'{1}'，寄件者識別碼為 '{2}'，接收者識別碼'{3}' 發生下列錯誤：</span><span class="sxs-lookup"><span data-stu-id="764aa-117">The Edifact functional group with id '{0}', in interchange with id '{1}', with sender id '{2}', receiver id '{3}' had the following errors:</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="764aa-118">說明</span><span class="sxs-lookup"><span data-stu-id="764aa-118">Explanation</span></span>  
 <span data-ttu-id="764aa-119">這個錯誤/警告/資訊事件表示 EDI 傳送管線在序列化外寄 EDIFACT 交換內功能群組，因為與群組敘述的錯誤時，會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="764aa-119">This Error/Warning/Information event indicates that the EDI send pipeline encountered an error when serializing a functional group within an outgoing EDIFACT interchange because of the stated errors with the group.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="764aa-120">使用者動作</span><span class="sxs-lookup"><span data-stu-id="764aa-120">User Action</span></span>  
 <span data-ttu-id="764aa-121">若要解決這個錯誤，錯誤訊息中使用的資訊來識別功能群組中的錯誤訊息，然後判斷 文件中的問題解決方法。</span><span class="sxs-lookup"><span data-stu-id="764aa-121">To resolve this error, use the information in the error message to identify the error in the functional group and then determine the problem resolution in the documentation.</span></span>