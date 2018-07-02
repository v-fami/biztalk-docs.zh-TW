---
title: 無效的 SenderId |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: be8055ab-8aba-49ac-ad33-fb33d4ff3e8b
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7517adcd214f789c8af37d4abce2478e6da20507
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36976535"
---
# <a name="invalid-senderid"></a><span data-ttu-id="534a4-102">無效的 SenderId</span><span class="sxs-lookup"><span data-stu-id="534a4-102">Invalid SenderId</span></span>
## <a name="details"></a><span data-ttu-id="534a4-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="534a4-103">Details</span></span>  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  <span data-ttu-id="534a4-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="534a4-104">Product Name</span></span>   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| <span data-ttu-id="534a4-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="534a4-105">Product Version</span></span> |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    <span data-ttu-id="534a4-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="534a4-106">Event ID</span></span>     |                                           -                                            |
|  <span data-ttu-id="534a4-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="534a4-107">Event Source</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="534a4-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="534a4-108"> EDI</span></span> |
|    <span data-ttu-id="534a4-109">元件</span><span class="sxs-lookup"><span data-stu-id="534a4-109">Component</span></span>    |                                       <span data-ttu-id="534a4-110">將 EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="534a4-110">EDI Engine</span></span>                                       |
|  <span data-ttu-id="534a4-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="534a4-111">Symbolic Name</span></span>  |                            <span data-ttu-id="534a4-112">X12Ta1InvalidSenderIdDescription</span><span class="sxs-lookup"><span data-stu-id="534a4-112">X12Ta1InvalidSenderIdDescription</span></span>                            |
|  <span data-ttu-id="534a4-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="534a4-113">Message Text</span></span>   |                                    <span data-ttu-id="534a4-114">無效的 SenderId</span><span class="sxs-lookup"><span data-stu-id="534a4-114">Invalid SenderId</span></span>                                    |
  
## <a name="explanation"></a><span data-ttu-id="534a4-115">說明</span><span class="sxs-lookup"><span data-stu-id="534a4-115">Explanation</span></span>  
 <span data-ttu-id="534a4-116">這個錯誤/警告/資訊事件表示，接收管線無法處理內送交換因為 ISA06 欄位中的寄件者識別碼或 [UNB2.1] 欄位中的傳送者識別不符合的資料型別和數字的數目建立服務結構描述 (x12serviceschema BaseArtifacts.dll 中的 EdifactServiceSchema)。</span><span class="sxs-lookup"><span data-stu-id="534a4-116">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming interchange because the Sender ID in the ISA06 field or the Sender Identification in the UNB2.1 field did not conform to the data type and number of digits established by the service schema (X12ServiceSchema or the EdifactServiceSchema in BaseArtifacts.dll).</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="534a4-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="534a4-117">User Action</span></span>  
 <span data-ttu-id="534a4-118">若要解決這個錯誤，請確定 ISA06 欄位是 X12_AN 資料類型，而且是 15 個字元長度 （不論有無結尾的空格） 或 [UNB2.1] 欄位是 EDIFACT_AN 資料類型，並介於 1 到 35 個字元。</span><span class="sxs-lookup"><span data-stu-id="534a4-118">To resolve this error, make sure that the ISA06 field is of the X12_AN data type and is 15 characters long (with or without trailing spaces) or that the UNB2.1 field is of the EDIFACT_AN data type and is between 1 and 35 characters.</span></span> <span data-ttu-id="534a4-119">重新傳送交換。</span><span class="sxs-lookup"><span data-stu-id="534a4-119">Have the interchange resent.</span></span>