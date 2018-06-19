---
title: Edifact 交換應該包含 TransactionSetGroup 或 FunctionalGroup Xml 標記 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 34318133-211f-422d-acdf-b841ece5d2b0
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: adb93582daf235a7f1f0633231e536f3c5b14ab0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22240102"
---
# <a name="edifact-interchange-should-have-contained-transactionsetgroup-or-functionalgroup-xml-tags"></a><span data-ttu-id="d0321-102">Edifact 交換應該包含 TransactionSetGroup 或 FunctionalGroup Xml 標記</span><span class="sxs-lookup"><span data-stu-id="d0321-102">Edifact interchange should have contained TransactionSetGroup or FunctionalGroup Xml tags</span></span>
## <a name="details"></a><span data-ttu-id="d0321-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="d0321-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d0321-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="d0321-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="d0321-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="d0321-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="d0321-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="d0321-106">Event ID</span></span>|-|  
|<span data-ttu-id="d0321-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="d0321-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="d0321-108">EDI</span><span class="sxs-lookup"><span data-stu-id="d0321-108"> EDI</span></span>|  
|<span data-ttu-id="d0321-109">元件</span><span class="sxs-lookup"><span data-stu-id="d0321-109">Component</span></span>|<span data-ttu-id="d0321-110">EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="d0321-110">EDI Engine</span></span>|  
|<span data-ttu-id="d0321-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="d0321-111">Symbolic Name</span></span>|-|  
|<span data-ttu-id="d0321-112">訊息文字</span><span class="sxs-lookup"><span data-stu-id="d0321-112">Message Text</span></span>|<span data-ttu-id="d0321-113">Edifact 交換應該包含 TransactionSetGroup 或 FunctionalGroup Xml 標記</span><span class="sxs-lookup"><span data-stu-id="d0321-113">Edifact interchange should have contained TransactionSetGroup or FunctionalGroup Xml tags</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="d0321-114">說明</span><span class="sxs-lookup"><span data-stu-id="d0321-114">Explanation</span></span>  
 <span data-ttu-id="d0321-115">這個錯誤/警告/資訊事件表示傳送管線無法處理已保留，因為 TransactionSetGroup 或 FunctionalGroup 標記未包含在交換 XML 檔案中的 EDIFACT 批次交換。</span><span class="sxs-lookup"><span data-stu-id="d0321-115">This Error/Warning/Information event indicates that the send pipeline could not process an EDIFACT batched interchange that was preserved because the TransactionSetGroup or FunctionalGroup tags were not included in the interchange XML file.</span></span>  
  
 <span data-ttu-id="d0321-116">BizTalk 會處理批次的交換時，會保留，交易集的群組或一組群組的交換 XML 檔案中指定的 XML 標記。</span><span class="sxs-lookup"><span data-stu-id="d0321-116">When BizTalk processes a batched interchange that is preserved, a group of transaction sets or a group of groups in the interchange's XML file are given an XML tag.</span></span> <span data-ttu-id="d0321-117">交易集的群組會擁有 TransactionSetGroup 標記。</span><span class="sxs-lookup"><span data-stu-id="d0321-117">A group of transaction sets is given the TransactionSetGroup tag.</span></span> <span data-ttu-id="d0321-118">一組群組會指定 FunctionalGroup 標記。</span><span class="sxs-lookup"><span data-stu-id="d0321-118">A group of groups is given the FunctionalGroup tag.</span></span> <span data-ttu-id="d0321-119">如果您設定保留批次使用 接收管線和通道傳輸的傳送管線，就會發生這個錯誤狀況。</span><span class="sxs-lookup"><span data-stu-id="d0321-119">This error condition occurs if you set up a preserved batch using a receive pipeline and a passthrough transmit send pipeline.</span></span> <span data-ttu-id="d0321-120">標記會設定由接收管線，並已移除的傳送管線。</span><span class="sxs-lookup"><span data-stu-id="d0321-120">The tags are set by the receive pipeline and stripped out by the send pipeline.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="d0321-121">使用者動作</span><span class="sxs-lookup"><span data-stu-id="d0321-121">User Action</span></span>  
 <span data-ttu-id="d0321-122">若要解決這個錯誤，請確認保留批次所產生的 XML 檔案有 TransactionSetGroup 標記 （適用於具有多個交易集的群組） 及/或 （適用於多個群組） 的 FunctionalGroup 標記語式正確的 XML 結構。</span><span class="sxs-lookup"><span data-stu-id="d0321-122">To resolve this error, ensure that the XML file generated for the preserved batch has a well-formed XML structure with the TransactionSetGroup tag (for a group with multiple transaction sets) and/or the FunctionalGroup tag (for multiple groups).</span></span>