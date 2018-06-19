---
title: 無效的安全性值 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ee380da7-c05e-4b9b-84ee-f7ffee90eb0e
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e41315400ee2b0eae099439237356b61676b26cb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22257206"
---
# <a name="invalid-security-value"></a><span data-ttu-id="ea6c6-102">無效的安全性值</span><span class="sxs-lookup"><span data-stu-id="ea6c6-102">Invalid Security Value</span></span>
## <a name="details"></a><span data-ttu-id="ea6c6-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="ea6c6-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ea6c6-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="ea6c6-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="ea6c6-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="ea6c6-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="ea6c6-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="ea6c6-106">Event ID</span></span>|-|  
|<span data-ttu-id="ea6c6-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="ea6c6-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="ea6c6-108">EDI</span><span class="sxs-lookup"><span data-stu-id="ea6c6-108"> EDI</span></span>|  
|<span data-ttu-id="ea6c6-109">元件</span><span class="sxs-lookup"><span data-stu-id="ea6c6-109">Component</span></span>|<span data-ttu-id="ea6c6-110">EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="ea6c6-110">EDI Engine</span></span>|  
|<span data-ttu-id="ea6c6-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="ea6c6-111">Symbolic Name</span></span>|<span data-ttu-id="ea6c6-112">X12Ta1InvalidSecurityValueDescription</span><span class="sxs-lookup"><span data-stu-id="ea6c6-112">X12Ta1InvalidSecurityValueDescription</span></span>|  
|<span data-ttu-id="ea6c6-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="ea6c6-113">Message Text</span></span>|<span data-ttu-id="ea6c6-114">無效的安全性值</span><span class="sxs-lookup"><span data-stu-id="ea6c6-114">Invalid Security Value</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="ea6c6-115">說明</span><span class="sxs-lookup"><span data-stu-id="ea6c6-115">Explanation</span></span>  
 <span data-ttu-id="ea6c6-116">這個錯誤/警告/資訊事件表示，接收管線無法處理內送交換因為 ISA04 欄位中的安全性資訊或收件者參考密碼值，在 UNB6.1 欄位中沒有符合的資料類型和服務結構描述 (x12serviceschema BaseArtifacts.dll 中的 EdifactServiceSchema) 所建立的數字的數目。</span><span class="sxs-lookup"><span data-stu-id="ea6c6-116">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming interchange because the Security Information in the ISA04 field or the Recipient Reference Password Value in the UNB6.1 field did not conform to the data type and number of digits established by the service schema (X12ServiceSchema or the EdifactServiceSchema in BaseArtifacts.dll).</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="ea6c6-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="ea6c6-117">User Action</span></span>  
 <span data-ttu-id="ea6c6-118">若要解決這個錯誤，請確定 ISA04 欄位是 X12_AN 資料型別，而且是 10 （含或不含尾端空白） 字元的長度或 UNB6.1 欄位是 EDIFACT_AN 資料型別，並且是介於 1 到 14 個字元之間。</span><span class="sxs-lookup"><span data-stu-id="ea6c6-118">To resolve this error, make sure that the ISA04 field is of the X12_AN data type and is 10 characters long (with or without trailing spaces) or that the UNB6.1 field is of the EDIFACT_AN data type and is between 1 and 14 characters long.</span></span> <span data-ttu-id="ea6c6-119">重新傳送交換。</span><span class="sxs-lookup"><span data-stu-id="ea6c6-119">Have the interchange resent.</span></span>