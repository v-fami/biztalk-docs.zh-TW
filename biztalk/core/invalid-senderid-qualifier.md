---
title: 無效的 SenderId 辨識符號 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cfe9c51c-d569-4f14-a690-f145ef1bf6a4
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dbe4b48e4e90443539b70c591750acf038be6e6b
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37014695"
---
# <a name="invalid-senderid-qualifier"></a><span data-ttu-id="d77eb-102">無效的 SenderId 辨識符號</span><span class="sxs-lookup"><span data-stu-id="d77eb-102">Invalid SenderId Qualifier</span></span>
## <a name="details"></a><span data-ttu-id="d77eb-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="d77eb-103">Details</span></span>  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  <span data-ttu-id="d77eb-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="d77eb-104">Product Name</span></span>   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| <span data-ttu-id="d77eb-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="d77eb-105">Product Version</span></span> |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    <span data-ttu-id="d77eb-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="d77eb-106">Event ID</span></span>     |                                           -                                            |
|  <span data-ttu-id="d77eb-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="d77eb-107">Event Source</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="d77eb-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="d77eb-108"> EDI</span></span> |
|    <span data-ttu-id="d77eb-109">元件</span><span class="sxs-lookup"><span data-stu-id="d77eb-109">Component</span></span>    |                                       <span data-ttu-id="d77eb-110">將 EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="d77eb-110">EDI Engine</span></span>                                       |
|  <span data-ttu-id="d77eb-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="d77eb-111">Symbolic Name</span></span>  |                       <span data-ttu-id="d77eb-112">X12Ta1InvalidSenderIdQualifierDescription</span><span class="sxs-lookup"><span data-stu-id="d77eb-112">X12Ta1InvalidSenderIdQualifierDescription</span></span>                        |
|  <span data-ttu-id="d77eb-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="d77eb-113">Message Text</span></span>   |                               <span data-ttu-id="d77eb-114">無效的 SenderId 辨識符號</span><span class="sxs-lookup"><span data-stu-id="d77eb-114">Invalid SenderId Qualifier</span></span>                               |
  
## <a name="explanation"></a><span data-ttu-id="d77eb-115">說明</span><span class="sxs-lookup"><span data-stu-id="d77eb-115">Explanation</span></span>  
 <span data-ttu-id="d77eb-116">這個錯誤/警告/資訊事件表示，接收管線無法處理內送交換因為 ISA05 欄位中的傳送者辨識符號 (x12 交換) 或 （適用於 EDIFACT 的 [UNB2.2] 欄位中的寄件者代碼辨識符號交換） 不符合服務結構描述 (x12serviceschema BaseArtifacts.dll 中的 EdifactServiceSchema) 所建立的列舉中的值。</span><span class="sxs-lookup"><span data-stu-id="d77eb-116">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming interchange because the Sender Qualifier in the ISA05 field (for an X12 interchange) or the Sender Code Qualifier in the UNB2.2 field (for an EDIFACT interchange) did not match a value in the enumeration established by the service schema (X12ServiceSchema or the EdifactServiceSchema in BaseArtifacts.dll).</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="d77eb-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="d77eb-117">User Action</span></span>  
 <span data-ttu-id="d77eb-118">若要解決這個錯誤，請確定 ISA07 欄位或 [UNB3.2] 欄位符合其中一個服務結構描述所建立的列舉型別中的值。</span><span class="sxs-lookup"><span data-stu-id="d77eb-118">To resolve this error, make sure that the ISA07 field or the UNB3.2 field matches one of the values in the enumeration established by the service schema.</span></span> <span data-ttu-id="d77eb-119">重新傳送交換。</span><span class="sxs-lookup"><span data-stu-id="d77eb-119">Have the interchange resent.</span></span>