---
title: 群組控制編號序號已耗盡協力電腦和 TPA |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cf341f8d-02ec-4618-a980-c8ac90654b1a
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1850b968a2c9b4c8d2c16fd90d9e37d80b60f8b6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22246398"
---
# <a name="group-control-number-sequence-exhausted-for-partner-and-tpa"></a><span data-ttu-id="f05c8-102">群組控制編號序號已耗盡協力電腦和 TPA</span><span class="sxs-lookup"><span data-stu-id="f05c8-102">Group control number sequence exhausted for Partner and TPA</span></span>
## <a name="details"></a><span data-ttu-id="f05c8-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="f05c8-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f05c8-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="f05c8-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="f05c8-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="f05c8-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="f05c8-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="f05c8-106">Event ID</span></span>|-|  
|<span data-ttu-id="f05c8-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="f05c8-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="f05c8-108">EDI</span><span class="sxs-lookup"><span data-stu-id="f05c8-108"> EDI</span></span>|  
|<span data-ttu-id="f05c8-109">元件</span><span class="sxs-lookup"><span data-stu-id="f05c8-109">Component</span></span>|<span data-ttu-id="f05c8-110">EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="f05c8-110">EDI Engine</span></span>|  
|<span data-ttu-id="f05c8-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="f05c8-111">Symbolic Name</span></span>|<span data-ttu-id="f05c8-112">EdiControlNumberExhaustedForParty</span><span class="sxs-lookup"><span data-stu-id="f05c8-112">EdiControlNumberExhaustedForParty</span></span>|  
|<span data-ttu-id="f05c8-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="f05c8-113">Message Text</span></span>|<span data-ttu-id="f05c8-114">群組控制編號序號用盡夥伴 '{1}' TPA '{2}'。</span><span class="sxs-lookup"><span data-stu-id="f05c8-114">Group control number sequence exhausted for Partner '{1}' for the TPA '{2}'.</span></span> <span data-ttu-id="f05c8-115">重設 {2}-EDI 屬性使用 BizTalk Server 管理 中的順序。</span><span class="sxs-lookup"><span data-stu-id="f05c8-115">Reset the sequence in {2} - EDI Properties using BizTalk Server Administration.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="f05c8-116">說明</span><span class="sxs-lookup"><span data-stu-id="f05c8-116">Explanation</span></span>  
 <span data-ttu-id="f05c8-117">這個錯誤/警告/資訊事件表示 BizTalk Server 無法處理文件，因為在 {2} 協議的群組控制項的範圍用完。</span><span class="sxs-lookup"><span data-stu-id="f05c8-117">This Error/Warning/Information event indicates BizTalk Server was not able to process the document because the Group control range has been used up for the agreement in {2}.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="f05c8-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="f05c8-118">User Action</span></span>  
 <span data-ttu-id="f05c8-119">若要解決這個錯誤，請發出滴答聲 {2} 協議的控制編號重設或增加控制編號範圍或點擊重設按鈕控制項的數字範圍規格針對協議中的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="f05c8-119">To resolve this error, please tick the checkbox to reset the control number for the {2} agreement or increase the control number range or hit the reset button against the control number range specification in the agreement.</span></span>