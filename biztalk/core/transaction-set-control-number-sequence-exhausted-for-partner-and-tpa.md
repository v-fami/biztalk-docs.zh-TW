---
title: 交易集控制編號序號已耗盡夥伴和 TPA 的 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 67f194ca-3e0f-4ad4-8bc8-88aa7e5193a7
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7c39815ccd013deea9ac4ef78426320e5c371feb
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36968511"
---
# <a name="transaction-set-control-number-sequence-exhausted-for-partner-and-tpa"></a><span data-ttu-id="83b7a-102">協力電腦和 TPA 的交易集控制編號序號已耗盡</span><span class="sxs-lookup"><span data-stu-id="83b7a-102">Transaction set control number sequence exhausted for Partner and TPA</span></span>
## <a name="details"></a><span data-ttu-id="83b7a-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="83b7a-103">Details</span></span>  
  
|                 |                                                                                                                                                                        |
|-----------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="83b7a-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="83b7a-104">Product Name</span></span>   |                                           [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                                           |
| <span data-ttu-id="83b7a-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="83b7a-105">Product Version</span></span> |                                                       [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                                       |
|    <span data-ttu-id="83b7a-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="83b7a-106">Event ID</span></span>     |                                                                                   -                                                                                    |
|  <span data-ttu-id="83b7a-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="83b7a-107">Event Source</span></span>   |                                         [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="83b7a-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="83b7a-108"> EDI</span></span>                                         |
|    <span data-ttu-id="83b7a-109">元件</span><span class="sxs-lookup"><span data-stu-id="83b7a-109">Component</span></span>    |                                                                               <span data-ttu-id="83b7a-110">將 EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="83b7a-110">EDI Engine</span></span>                                                                               |
|  <span data-ttu-id="83b7a-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="83b7a-111">Symbolic Name</span></span>  |                                                                   <span data-ttu-id="83b7a-112">EdiControlNumberExhaustedForParty</span><span class="sxs-lookup"><span data-stu-id="83b7a-112">EdiControlNumberExhaustedForParty</span></span>                                                                    |
|  <span data-ttu-id="83b7a-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="83b7a-113">Message Text</span></span>   | <span data-ttu-id="83b7a-114">交易集控制編號序號已耗盡夥伴的 '{1}'用於 TPA'{2}'。</span><span class="sxs-lookup"><span data-stu-id="83b7a-114">Transaction set control number sequence exhausted for Partner '{1}' for the TPA '{2}'.</span></span> <span data-ttu-id="83b7a-115">重設在序列{2}-EDI 屬性使用 BizTalk Server 管理。</span><span class="sxs-lookup"><span data-stu-id="83b7a-115">Reset the sequence in {2} - EDI Properties using BizTalk Server Administration.</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="83b7a-116">說明</span><span class="sxs-lookup"><span data-stu-id="83b7a-116">Explanation</span></span>  
 <span data-ttu-id="83b7a-117">這個錯誤/警告/資訊事件表示 BizTalk Server 找不到文件的交易集控制範圍，因為已使用協議中的處理序{2}。</span><span class="sxs-lookup"><span data-stu-id="83b7a-117">This Error/Warning/Information event indicates BizTalk Server was not able to process the document because the Transaction set control range has been used up for the agreement in {2}.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="83b7a-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="83b7a-118">User Action</span></span>  
 <span data-ttu-id="83b7a-119">若要解決這個錯誤，請勾選核取方塊，以重設的控制編號{2}合約或增加控制編號範圍，或者協議中遇到對控制項的數字範圍規格 [重設] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="83b7a-119">To resolve this error, please tick the checkbox to reset the control number for the {2} agreement or increase the control number range or hit the reset button against the control number range specification in the agreement.</span></span>