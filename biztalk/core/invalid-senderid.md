---
title: "無效的 SenderId |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: be8055ab-8aba-49ac-ad33-fb33d4ff3e8b
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 150be7faef15efd033cf87759a8390c09e38e249
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="invalid-senderid"></a><span data-ttu-id="201d2-102">無效的 SenderId</span><span class="sxs-lookup"><span data-stu-id="201d2-102">Invalid SenderId</span></span>
## <a name="details"></a><span data-ttu-id="201d2-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="201d2-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="201d2-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="201d2-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="201d2-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="201d2-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="201d2-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="201d2-106">Event ID</span></span>|-|  
|<span data-ttu-id="201d2-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="201d2-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="201d2-108">EDI</span><span class="sxs-lookup"><span data-stu-id="201d2-108"> EDI</span></span>|  
|<span data-ttu-id="201d2-109">元件</span><span class="sxs-lookup"><span data-stu-id="201d2-109">Component</span></span>|<span data-ttu-id="201d2-110">EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="201d2-110">EDI Engine</span></span>|  
|<span data-ttu-id="201d2-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="201d2-111">Symbolic Name</span></span>|<span data-ttu-id="201d2-112">X12Ta1InvalidSenderIdDescription</span><span class="sxs-lookup"><span data-stu-id="201d2-112">X12Ta1InvalidSenderIdDescription</span></span>|  
|<span data-ttu-id="201d2-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="201d2-113">Message Text</span></span>|<span data-ttu-id="201d2-114">無效的 SenderId</span><span class="sxs-lookup"><span data-stu-id="201d2-114">Invalid SenderId</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="201d2-115">說明</span><span class="sxs-lookup"><span data-stu-id="201d2-115">Explanation</span></span>  
 <span data-ttu-id="201d2-116">這個錯誤/警告/資訊事件表示，接收管線無法處理內送交換的寄件者識別碼在 ISA06 欄位或 [UNB2.1] 欄位中的傳送者識別不符合的資料型別和數字，因為由服務結構描述 (x12serviceschema BaseArtifacts.dll 中的 EdifactServiceSchema) 所建立。</span><span class="sxs-lookup"><span data-stu-id="201d2-116">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming interchange because the Sender ID in the ISA06 field or the Sender Identification in the UNB2.1 field did not conform to the data type and number of digits established by the service schema (X12ServiceSchema or the EdifactServiceSchema in BaseArtifacts.dll).</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="201d2-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="201d2-117">User Action</span></span>  
 <span data-ttu-id="201d2-118">若要解決這個錯誤，請確定 ISA06 欄位是 X12_AN 資料型別，而且 15 字元的長度 （不論有無尾端空白） 或 [UNB2.1] 欄位是 EDIFACT_AN 資料類型，且為介於 1 到 35 個字元之間。</span><span class="sxs-lookup"><span data-stu-id="201d2-118">To resolve this error, make sure that the ISA06 field is of the X12_AN data type and is 15 characters long (with or without trailing spaces) or that the UNB2.1 field is of the EDIFACT_AN data type and is between 1 and 35 characters.</span></span> <span data-ttu-id="201d2-119">重新傳送交換。</span><span class="sxs-lookup"><span data-stu-id="201d2-119">Have the interchange resent.</span></span>