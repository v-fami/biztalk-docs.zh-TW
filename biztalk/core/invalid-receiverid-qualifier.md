---
title: 無效的 ReceiverId 辨識符號 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 52d60f7e-6f16-424d-91b8-dc8181206249
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7f4cf13bb338959ca4cd7d2d25a85749f0ff0171
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36981815"
---
# <a name="invalid-receiverid-qualifier"></a><span data-ttu-id="ea4d5-102">無效的 ReceiverId 辨識符號</span><span class="sxs-lookup"><span data-stu-id="ea4d5-102">Invalid ReceiverId Qualifier</span></span>
## <a name="details"></a><span data-ttu-id="ea4d5-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="ea4d5-103">Details</span></span>  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  <span data-ttu-id="ea4d5-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="ea4d5-104">Product Name</span></span>   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| <span data-ttu-id="ea4d5-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="ea4d5-105">Product Version</span></span> |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    <span data-ttu-id="ea4d5-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="ea4d5-106">Event ID</span></span>     |                                           -                                            |
|  <span data-ttu-id="ea4d5-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="ea4d5-107">Event Source</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="ea4d5-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="ea4d5-108"> EDI</span></span> |
|    <span data-ttu-id="ea4d5-109">元件</span><span class="sxs-lookup"><span data-stu-id="ea4d5-109">Component</span></span>    |                                       <span data-ttu-id="ea4d5-110">將 EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="ea4d5-110">EDI Engine</span></span>                                       |
|  <span data-ttu-id="ea4d5-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="ea4d5-111">Symbolic Name</span></span>  |                      <span data-ttu-id="ea4d5-112">X12Ta1InvalidReceiverIdQualifierDescription</span><span class="sxs-lookup"><span data-stu-id="ea4d5-112">X12Ta1InvalidReceiverIdQualifierDescription</span></span>                       |
|  <span data-ttu-id="ea4d5-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="ea4d5-113">Message Text</span></span>   |                              <span data-ttu-id="ea4d5-114">無效的 ReceiverId 辨識符號</span><span class="sxs-lookup"><span data-stu-id="ea4d5-114">Invalid ReceiverId Qualifier</span></span>                              |
  
## <a name="explanation"></a><span data-ttu-id="ea4d5-115">說明</span><span class="sxs-lookup"><span data-stu-id="ea4d5-115">Explanation</span></span>  
 <span data-ttu-id="ea4d5-116">這個錯誤/警告/資訊事件表示，接收管線無法處理內送交換因為 ISA07 欄位中的接收者辨識符號 (x12 交換) 或 （適用於 EDIFACT 的 [UNB3.2] 欄位中的收件者代碼辨識符號交換） 不符合服務結構描述 (x12serviceschema BaseArtifacts.dll 中的 EdifactServiceSchema) 所建立的列舉中的值。</span><span class="sxs-lookup"><span data-stu-id="ea4d5-116">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming interchange because the Receiver Qualifier in the ISA07 field (for an X12 interchange) or the Recipient Code Qualifier in the UNB3.2 field (for an EDIFACT interchange) did not match a value in the enumeration established by the service schema (X12ServiceSchema or the EdifactServiceSchema in BaseArtifacts.dll).</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="ea4d5-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="ea4d5-117">User Action</span></span>  
 <span data-ttu-id="ea4d5-118">若要解決這個錯誤，請確定 ISA07 欄位或 [UNB3.2] 欄位符合其中一個服務結構描述所建立的列舉型別中的值。</span><span class="sxs-lookup"><span data-stu-id="ea4d5-118">To resolve this error, make sure that the ISA07 field or the UNB3.2 field matches one of the values in the enumeration established by the service schema.</span></span> <span data-ttu-id="ea4d5-119">重新傳送交換。</span><span class="sxs-lookup"><span data-stu-id="ea4d5-119">Have the interchange resent.</span></span>