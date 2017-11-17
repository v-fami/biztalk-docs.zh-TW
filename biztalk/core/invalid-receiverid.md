---
title: "無效的 ReceiverId |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: feabf940-c49b-4f4a-8906-230dc8fb1b30
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d397c75efe1172f87def3dee92e20f4d0d7ef4d1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="invalid-receiverid"></a><span data-ttu-id="dcd5a-102">無效的 ReceiverId</span><span class="sxs-lookup"><span data-stu-id="dcd5a-102">Invalid ReceiverId</span></span>
## <a name="details"></a><span data-ttu-id="dcd5a-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="dcd5a-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="dcd5a-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="dcd5a-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="dcd5a-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="dcd5a-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="dcd5a-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="dcd5a-106">Event ID</span></span>|-|  
|<span data-ttu-id="dcd5a-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="dcd5a-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="dcd5a-108">EDI</span><span class="sxs-lookup"><span data-stu-id="dcd5a-108"> EDI</span></span>|  
|<span data-ttu-id="dcd5a-109">元件</span><span class="sxs-lookup"><span data-stu-id="dcd5a-109">Component</span></span>|<span data-ttu-id="dcd5a-110">EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="dcd5a-110">EDI Engine</span></span>|  
|<span data-ttu-id="dcd5a-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="dcd5a-111">Symbolic Name</span></span>|<span data-ttu-id="dcd5a-112">X12Ta1InvalidReceiverIdDescription</span><span class="sxs-lookup"><span data-stu-id="dcd5a-112">X12Ta1InvalidReceiverIdDescription</span></span>|  
|<span data-ttu-id="dcd5a-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="dcd5a-113">Message Text</span></span>|<span data-ttu-id="dcd5a-114">無效的 ReceiverId</span><span class="sxs-lookup"><span data-stu-id="dcd5a-114">Invalid ReceiverId</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="dcd5a-115">說明</span><span class="sxs-lookup"><span data-stu-id="dcd5a-115">Explanation</span></span>  
 <span data-ttu-id="dcd5a-116">這個錯誤/警告/資訊事件表示，接收管線無法處理內送交換的接收者識別碼 ISA08 欄位中或在 [UNB3.1] 欄位的收件者識別不符合的資料型別和數字，因為由服務結構描述 (x12serviceschema BaseArtifacts.dll 中的 EdifactServiceSchema) 所建立。</span><span class="sxs-lookup"><span data-stu-id="dcd5a-116">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming interchange because the Receiver ID in the ISA08 field or the Recipient Identification in the UNB3.1 field did not conform to the data type and number of digits established by the service schema (X12ServiceSchema or the EdifactServiceSchema in BaseArtifacts.dll).</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="dcd5a-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="dcd5a-117">User Action</span></span>  
 <span data-ttu-id="dcd5a-118">若要解決這個錯誤，請確定 ISA08 欄位是 X12_AN 資料型別，而且 15 字元的長度 （不論有無尾端空白） 或 [UNB3.1] 欄位是 EDIFACT_AN 資料類型，且為介於 1 到 35 個字元之間。</span><span class="sxs-lookup"><span data-stu-id="dcd5a-118">To resolve this error, make sure that the ISA08 field is of the X12_AN data type and is 15 characters long (with or without trailing spaces) or that the UNB3.1 field is of the EDIFACT_AN data type and is between 1 and 35 characters.</span></span> <span data-ttu-id="dcd5a-119">重新傳送交換。</span><span class="sxs-lookup"><span data-stu-id="dcd5a-119">Have the interchange resent.</span></span>