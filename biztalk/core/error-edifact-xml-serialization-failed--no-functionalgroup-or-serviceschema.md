---
title: Edifact 交換 Xml 序列化失敗，因為無效的結構，無 FunctionalGroup 或 ServiceSchema |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 530faadd-e301-4743-b4b3-b04ba7578f1d
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 370b9844faaa46955f6e45bfcea78f6eba0f8cf9
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37003151"
---
# <a name="edifact-interchange-xml-serialization-failed-due-to-invalid-structure-no-functionalgroup-or-serviceschema"></a><span data-ttu-id="00eba-102">Edifact 交換 Xml 序列化失敗，因為無效的結構，無 FunctionalGroup 或 ServiceSchema</span><span class="sxs-lookup"><span data-stu-id="00eba-102">Edifact interchange Xml serialization failed due to invalid structure, no FunctionalGroup or ServiceSchema</span></span>
## <a name="details"></a><span data-ttu-id="00eba-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="00eba-103">Details</span></span>  
  
|                 |                                                                                                                                              |
|-----------------|----------------------------------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="00eba-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="00eba-104">Product Name</span></span>   |                              [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                              |
| <span data-ttu-id="00eba-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="00eba-105">Product Version</span></span> |                                          [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                          |
|    <span data-ttu-id="00eba-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="00eba-106">Event ID</span></span>     |                                                                      -                                                                       |
|  <span data-ttu-id="00eba-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="00eba-107">Event Source</span></span>   |                            [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="00eba-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="00eba-108"> EDI</span></span>                            |
|    <span data-ttu-id="00eba-109">元件</span><span class="sxs-lookup"><span data-stu-id="00eba-109">Component</span></span>    |                                                                  <span data-ttu-id="00eba-110">將 EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="00eba-110">EDI Engine</span></span>                                                                  |
|  <span data-ttu-id="00eba-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="00eba-111">Symbolic Name</span></span>  |                                                                      -                                                                       |
|  <span data-ttu-id="00eba-112">訊息文字</span><span class="sxs-lookup"><span data-stu-id="00eba-112">Message Text</span></span>   | <span data-ttu-id="00eba-113">Edifact 交換 Xml 序列化失敗，因為無效的結構。</span><span class="sxs-lookup"><span data-stu-id="00eba-113">Edifact interchange Xml serialization failed due to invalid structure.</span></span> <span data-ttu-id="00eba-114">尋找 FunctionalGroup 或 ServiceSchema UNZ，但是找不到。</span><span class="sxs-lookup"><span data-stu-id="00eba-114">Looking for FunctionalGroup or ServiceSchema for UNZ, but none found.</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="00eba-115">說明</span><span class="sxs-lookup"><span data-stu-id="00eba-115">Explanation</span></span>  
 <span data-ttu-id="00eba-116">這個錯誤/警告/資訊事件表示傳送管線無法處理批次的 EDIFACT 交換因為交換 XML 檔案中未包含 TransactionSetGroup 或 FunctionalGroup 的標記時保留。</span><span class="sxs-lookup"><span data-stu-id="00eba-116">This Error/Warning/Information event indicates that the send pipeline could not process an EDIFACT batched interchange that was preserved because the TransactionSetGroup or FunctionalGroup tags were not included in the interchange XML file.</span></span>  
  
 <span data-ttu-id="00eba-117">BizTalk 可處理的批次的交換時，會保留，交易集的群組或交換的 XML 檔案中的群組一組指定的 XML 標記。</span><span class="sxs-lookup"><span data-stu-id="00eba-117">When BizTalk processes a batched interchange that is preserved, a group of transaction sets or a group of groups in the interchange's XML file are given an XML tag.</span></span> <span data-ttu-id="00eba-118">群組一組指定的 FunctionalGroup 標記。</span><span class="sxs-lookup"><span data-stu-id="00eba-118">A group of groups is given the FunctionalGroup tag.</span></span> <span data-ttu-id="00eba-119">ServiceSchema 旗標會指出用於保留批次交換的控制結構描述。</span><span class="sxs-lookup"><span data-stu-id="00eba-119">The ServiceSchema flag indicates the control schema used for the preserved-batch interchange.</span></span> <span data-ttu-id="00eba-120">如果您設定保留批次使用 接收管線，並通過傳輸的傳送管線，就會發生這個錯誤狀況。</span><span class="sxs-lookup"><span data-stu-id="00eba-120">This error condition occurs if you set up a preserved batch using a receive pipeline and a passthrough transmit send pipeline.</span></span> <span data-ttu-id="00eba-121">標記會由接收管線設定，並移除的傳送管線。</span><span class="sxs-lookup"><span data-stu-id="00eba-121">The tags are set by the receive pipeline and stripped out by the send pipeline.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="00eba-122">使用者動作</span><span class="sxs-lookup"><span data-stu-id="00eba-122">User Action</span></span>  
 <span data-ttu-id="00eba-123">若要解決這個錯誤，請確定保留批次產生的 XML 檔有格式正確的 XML 結構 （適用於多個群組） 的 FunctionalGroup 標記和/或 ServiceSchema 標記 （用於保留批次交換的控制結構描述）。</span><span class="sxs-lookup"><span data-stu-id="00eba-123">To resolve this error, ensure that the XML file generated for the preserved batch has a well-formed XML structure with the FunctionalGroup tag (for multiple groups) and/or the ServiceSchema tag (for the control schema used for the preserved-batch interchange).</span></span>