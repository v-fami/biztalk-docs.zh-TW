---
title: 若要啟用狀態報告，請執行&#39;BizTalk Server 組態&#39;並設定 EDI-AS2 狀態報告功能 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bf125919-80ab-4cb8-b1f5-0f2616cc6f5c
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 89d7fcf5e473485d0b61edcd6d5f287198021d3f
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36992711"
---
# <a name="to-enable-status-reporting-run-39biztalk-server-configuration39-and-configure-edi-as2-status-reporting-feature"></a><span data-ttu-id="0e05d-102">若要啟用狀態報告，請執行&#39;BizTalk Server 組態&#39;並設定 EDI-AS2 狀態報告功能</span><span class="sxs-lookup"><span data-stu-id="0e05d-102">To enable status reporting, run &#39;BizTalk Server Configuration&#39; and configure EDI-AS2 status reporting feature</span></span>
## <a name="details"></a><span data-ttu-id="0e05d-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="0e05d-103">Details</span></span>  
  
|                 |                                                                                                                |
|-----------------|----------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="0e05d-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="0e05d-104">Product Name</span></span>   |               [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]               |
| <span data-ttu-id="0e05d-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="0e05d-105">Product Version</span></span> |                           [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                           |
|    <span data-ttu-id="0e05d-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="0e05d-106">Event ID</span></span>     |                                                       -                                                        |
|  <span data-ttu-id="0e05d-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="0e05d-107">Event Source</span></span>   |             [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="0e05d-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="0e05d-108"> EDI</span></span>             |
|    <span data-ttu-id="0e05d-109">元件</span><span class="sxs-lookup"><span data-stu-id="0e05d-109">Component</span></span>    |                                                   <span data-ttu-id="0e05d-110">將 EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="0e05d-110">EDI Engine</span></span>                                                   |
|  <span data-ttu-id="0e05d-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="0e05d-111">Symbolic Name</span></span>  |                                                       <span data-ttu-id="0e05d-112">0</span><span class="sxs-lookup"><span data-stu-id="0e05d-112">0</span></span>                                                        |
|  <span data-ttu-id="0e05d-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="0e05d-113">Message Text</span></span>   | <span data-ttu-id="0e05d-114">若要啟用狀態報告，請執行 [BizTalk Server 組態] 並設定 EDI/AS2 狀態報告功能。</span><span class="sxs-lookup"><span data-stu-id="0e05d-114">To enable status reporting, run 'BizTalk Server Configuration' and configure EDI/AS2 status reporting feature.</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="0e05d-115">說明</span><span class="sxs-lookup"><span data-stu-id="0e05d-115">Explanation</span></span>  
 <span data-ttu-id="0e05d-116">這個錯誤/警告/資訊事件表示，EDI/AS2 狀態報告並未運作，因為尚未設定。</span><span class="sxs-lookup"><span data-stu-id="0e05d-116">This Error/Warning/Information event indicates that EDI/AS2 status reporting is not working because it has not been configured.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="0e05d-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="0e05d-117">User Action</span></span>  
 <span data-ttu-id="0e05d-118">若要解決這個錯誤，執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="0e05d-118">To resolve this error, do the following:</span></span>  
  
1.  <span data-ttu-id="0e05d-119">執行 BizTalk Server 組態精靈。</span><span class="sxs-lookup"><span data-stu-id="0e05d-119">Run the BizTalk Server Configuration wizard.</span></span> <span data-ttu-id="0e05d-120">按一下 [BizTalk EDI/AS2 Runtime] 節點中，並檢查 「 啟用 BizTalk EDI/AS2 執行階段狀態報告為此 BizTalk 群組 」 屬性。</span><span class="sxs-lookup"><span data-stu-id="0e05d-120">Click the BizTalk EDI/AS2 Runtime node, and check the "Enable BizTalk EDI/AS2 Runtime Status Reporting for this BizTalk Group" property.</span></span> <span data-ttu-id="0e05d-121">若要設定 EDI/AS2 狀態報告，您必須設定 BAM。</span><span class="sxs-lookup"><span data-stu-id="0e05d-121">You must configure BAM in order to configure EDI/AS2 status reporting.</span></span>  
  
2.  <span data-ttu-id="0e05d-122">在 BizTalk Server 管理主控台中，啟用 EDI 狀態報告的合作對象，按一下 [啟動 EDI 報告] 屬性中的 [EDI 屬性] 對話方塊中的 [一般] 頁面。</span><span class="sxs-lookup"><span data-stu-id="0e05d-122">In the BizTalk Server Administration Console, enable EDI status reporting for the party by clicking the "Activate EDI reporting" property in the General page of the EDI Properties dialog box.</span></span> <span data-ttu-id="0e05d-123">啟用 AS2 狀態報告的合作對象，按一下 [啟動 AS2 報告] 屬性中的 [AS2 屬性] 對話方塊中的 [一般] 頁面。</span><span class="sxs-lookup"><span data-stu-id="0e05d-123">Enable AS2 status reporting for the party by clicking the "Activate AS2 reporting" property in the General page of the AS2 Properties dialog box.</span></span> <span data-ttu-id="0e05d-124">您必須在啟用 EDI 或 AS2 狀態報告之後，重新啟動 BizTalk 服務。</span><span class="sxs-lookup"><span data-stu-id="0e05d-124">You must restart the BizTalk service after enabling EDI or AS2 status reporting.</span></span>