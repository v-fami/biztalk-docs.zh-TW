---
title: 不支援的功能群組版本 |Microsoft Docs
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
ms.openlocfilehash: 8ce3ff1cfb525b98e646c31180aa6668d3173cb0
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36997711"
---
# <a name="functional-group-version-not-supported"></a><span data-ttu-id="f386d-102">不支援的功能群組版本</span><span class="sxs-lookup"><span data-stu-id="f386d-102">Functional Group Version Not Supported</span></span>
## <a name="details"></a><span data-ttu-id="f386d-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="f386d-103">Details</span></span>  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  <span data-ttu-id="f386d-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="f386d-104">Product Name</span></span>   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| <span data-ttu-id="f386d-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="f386d-105">Product Version</span></span> |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    <span data-ttu-id="f386d-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="f386d-106">Event ID</span></span>     |                                           -                                            |
|  <span data-ttu-id="f386d-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="f386d-107">Event Source</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="f386d-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="f386d-108"> EDI</span></span> |
|    <span data-ttu-id="f386d-109">元件</span><span class="sxs-lookup"><span data-stu-id="f386d-109">Component</span></span>    |                                       <span data-ttu-id="f386d-110">將 EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="f386d-110">EDI Engine</span></span>                                       |
|  <span data-ttu-id="f386d-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="f386d-111">Symbolic Name</span></span>  |                        <span data-ttu-id="f386d-112">X12FaGroupVersionNotSupportedDescription</span><span class="sxs-lookup"><span data-stu-id="f386d-112">X12FaGroupVersionNotSupportedDescription</span></span>                        |
|  <span data-ttu-id="f386d-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="f386d-113">Message Text</span></span>   |                         <span data-ttu-id="f386d-114">不支援的功能群組版本</span><span class="sxs-lookup"><span data-stu-id="f386d-114">Functional Group Version Not Supported</span></span>                         |
  
## <a name="explanation"></a><span data-ttu-id="f386d-115">說明</span><span class="sxs-lookup"><span data-stu-id="f386d-115">Explanation</span></span>  
 <span data-ttu-id="f386d-116">這個錯誤/警告/資訊事件表示，接收管線無法處理內送交換因為區段 GS08 功能群組的 BizTalk Server 不支援的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="f386d-116">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming interchange because BizTalk Server does not support the version number in segment GS08 of a functional group.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="f386d-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="f386d-117">User Action</span></span>  
 <span data-ttu-id="f386d-118">若要解決這個錯誤，請確認每個執行個體的 GS08 在交換中的所有功能群組中 BizTalk Server 所支援的區段中的版本號碼，並就會重新傳送交換。</span><span class="sxs-lookup"><span data-stu-id="f386d-118">To resolve this error, ensure that the version numbers in each instance of segment GS08 in all functional groups in the interchange are supported by BizTalk Server, and then have the interchange resent.</span></span> <span data-ttu-id="f386d-119">請注意 BizTalk Server 支援的標準版本所述的 「 EDI 文件結構描述支援 」 主題[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]產品說明。</span><span class="sxs-lookup"><span data-stu-id="f386d-119">Note that the standard versions that BizTalk Server supports are listed in the "EDI Document Schema Support" topic of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] product help.</span></span>