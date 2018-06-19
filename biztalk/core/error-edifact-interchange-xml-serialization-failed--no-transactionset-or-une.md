---
title: Edifact 交換 Xml 序列化失敗，因為無效的結構、 沒有 transactionSet 或 UNE |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3ce1c219-f2ed-46c1-ae4b-8a4206f7cd01
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f5c6aae4bc3ed16afffadec774eaeac9ed64808d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22241726"
---
# <a name="edifact-interchange-xml-serialization-failed-due-to-invalid-structure-no-transactionset-or-une"></a><span data-ttu-id="35c43-102">Edifact 交換 Xml 序列化失敗，因為無效的結構、 沒有 transactionSet 或 UNE</span><span class="sxs-lookup"><span data-stu-id="35c43-102">Edifact interchange Xml serialization failed due to invalid structure, no transactionSet or UNE</span></span>
## <a name="details"></a><span data-ttu-id="35c43-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="35c43-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="35c43-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="35c43-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="35c43-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="35c43-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="35c43-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="35c43-106">Event ID</span></span>|-|  
|<span data-ttu-id="35c43-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="35c43-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="35c43-108">EDI</span><span class="sxs-lookup"><span data-stu-id="35c43-108"> EDI</span></span>|  
|<span data-ttu-id="35c43-109">元件</span><span class="sxs-lookup"><span data-stu-id="35c43-109">Component</span></span>|<span data-ttu-id="35c43-110">EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="35c43-110">EDI Engine</span></span>|  
|<span data-ttu-id="35c43-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="35c43-111">Symbolic Name</span></span>|<span data-ttu-id="35c43-112">EfactTransactionSetOrUneNotFound</span><span class="sxs-lookup"><span data-stu-id="35c43-112">EfactTransactionSetOrUneNotFound</span></span>|  
|<span data-ttu-id="35c43-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="35c43-113">Message Text</span></span>|<span data-ttu-id="35c43-114">Edifact 交換 Xml 序列化失敗，因為無效的結構。</span><span class="sxs-lookup"><span data-stu-id="35c43-114">Edifact interchange Xml serialization failed due to invalid structure.</span></span> <span data-ttu-id="35c43-115">尋找 TransactionSet 或 UNE，但找不到</span><span class="sxs-lookup"><span data-stu-id="35c43-115">Looking for TransactionSet or UNE, but not found</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="35c43-116">說明</span><span class="sxs-lookup"><span data-stu-id="35c43-116">Explanation</span></span>  
 <span data-ttu-id="35c43-117">這個錯誤/警告/資訊事件表示 EDI 接收管線無法處理內送 EDIFACT 交換，因為第一個區段都不 UNA 或 UNB 區段。</span><span class="sxs-lookup"><span data-stu-id="35c43-117">This Error/Warning/Information event indicates that the EDI receive pipeline could not process the incoming EDIFACT interchange because the first segment was neither a UNA or a UNB segment.</span></span> <span data-ttu-id="35c43-118">UNA 區段是選擇性的。UNB 區段是必要的。</span><span class="sxs-lookup"><span data-stu-id="35c43-118">The UNA segment is optional; the UNB segment is mandatory.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="35c43-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="35c43-119">User Action</span></span>  
 <span data-ttu-id="35c43-120">若要解決這個錯誤，請確認訊息的這類交易設定群組中會是後面接著另一個交易集或 UNE 區段的交換結構的寄件者。</span><span class="sxs-lookup"><span data-stu-id="35c43-120">To resolve this error, ensure that the sender of the interchange structures the message such that a transaction set in a group is either followed by another transaction set or a UNE segment.</span></span> <span data-ttu-id="35c43-121">將傳送者，然後重新傳送交換。</span><span class="sxs-lookup"><span data-stu-id="35c43-121">Have the sender then resend the interchange.</span></span>