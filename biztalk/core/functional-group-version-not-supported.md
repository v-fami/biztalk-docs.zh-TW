---
title: 不支援的功能群組版本 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 715e6585-a07a-4060-a15b-0c9603fbef19
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c7b92b7844c750d9a709ac2376bb8f126a32119f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22246446"
---
# <a name="functional-group-version-not-supported"></a><span data-ttu-id="e467b-102">不支援的功能群組版本</span><span class="sxs-lookup"><span data-stu-id="e467b-102">Functional Group Version Not Supported</span></span>
## <a name="details"></a><span data-ttu-id="e467b-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="e467b-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e467b-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="e467b-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="e467b-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="e467b-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="e467b-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="e467b-106">Event ID</span></span>|-|  
|<span data-ttu-id="e467b-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="e467b-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="e467b-108">EDI</span><span class="sxs-lookup"><span data-stu-id="e467b-108"> EDI</span></span>|  
|<span data-ttu-id="e467b-109">元件</span><span class="sxs-lookup"><span data-stu-id="e467b-109">Component</span></span>|<span data-ttu-id="e467b-110">EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="e467b-110">EDI Engine</span></span>|  
|<span data-ttu-id="e467b-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="e467b-111">Symbolic Name</span></span>|<span data-ttu-id="e467b-112">X12FaGroupVersionNotSupportedDescription</span><span class="sxs-lookup"><span data-stu-id="e467b-112">X12FaGroupVersionNotSupportedDescription</span></span>|  
|<span data-ttu-id="e467b-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="e467b-113">Message Text</span></span>|<span data-ttu-id="e467b-114">不支援的功能群組版本</span><span class="sxs-lookup"><span data-stu-id="e467b-114">Functional Group Version Not Supported</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="e467b-115">說明</span><span class="sxs-lookup"><span data-stu-id="e467b-115">Explanation</span></span>  
 <span data-ttu-id="e467b-116">這個錯誤/警告/資訊事件表示，接收管線無法處理內送交換因為 BizTalk Server 不支援的功能群組的 GS08 區段中的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="e467b-116">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming interchange because BizTalk Server does not support the version number in segment GS08 of a functional group.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="e467b-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="e467b-117">User Action</span></span>  
 <span data-ttu-id="e467b-118">若要解決這個錯誤，請確認每個區段在交換中的所有功能群組中的 GS08 支援 BizTalk Server 執行個體的版本號碼，則需要重新傳送交換。</span><span class="sxs-lookup"><span data-stu-id="e467b-118">To resolve this error, ensure that the version numbers in each instance of segment GS08 in all functional groups in the interchange are supported by BizTalk Server, and then have the interchange resent.</span></span> <span data-ttu-id="e467b-119">請注意 BizTalk Server 支援的標準版本會列出的 「 EDI 文件結構描述支援 」 主題[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]產品說明。</span><span class="sxs-lookup"><span data-stu-id="e467b-119">Note that the standard versions that BizTalk Server supports are listed in the "EDI Document Schema Support" topic of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] product help.</span></span>