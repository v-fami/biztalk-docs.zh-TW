---
title: 通訊協定無法的內容屬性根據協議解析 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 58fccd84-579c-4b5e-872b-33730d4079e8
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a2cac1ea6e940385fceac541df96582f93eb058e
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37008167"
---
# <a name="agreement-resolution-based-on-the-context-properties-for-protocol-has-failed"></a><span data-ttu-id="e1449-102">無法解析內容屬性基礎通訊協定的協議</span><span class="sxs-lookup"><span data-stu-id="e1449-102">Agreement Resolution based on the context properties for Protocol has failed</span></span>
## <a name="details"></a><span data-ttu-id="e1449-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="e1449-103">Details</span></span>  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  <span data-ttu-id="e1449-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="e1449-104">Product Name</span></span>   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| <span data-ttu-id="e1449-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="e1449-105">Product Version</span></span> |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    <span data-ttu-id="e1449-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="e1449-106">Event ID</span></span>     |                                           -                                            |
|  <span data-ttu-id="e1449-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="e1449-107">Event Source</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="e1449-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="e1449-108"> EDI</span></span> |
|    <span data-ttu-id="e1449-109">元件</span><span class="sxs-lookup"><span data-stu-id="e1449-109">Component</span></span>    |                                       <span data-ttu-id="e1449-110">將 EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="e1449-110">EDI Engine</span></span>                                       |
|  <span data-ttu-id="e1449-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="e1449-111">Symbolic Name</span></span>  |                    <span data-ttu-id="e1449-112">AgreementResolutionContextPropertiesLookupFailed</span><span class="sxs-lookup"><span data-stu-id="e1449-112">AgreementResolutionContextPropertiesLookupFailed</span></span>                    |
|  <span data-ttu-id="e1449-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="e1449-113">Message Text</span></span>   |   <span data-ttu-id="e1449-114">內容屬性為基礎的協議解析{0}通訊協定驗證失敗。</span><span class="sxs-lookup"><span data-stu-id="e1449-114">Agreement Resolution based on the context properties for {0} Protocol has failed.</span></span>    |
  
## <a name="explanation"></a><span data-ttu-id="e1449-115">說明</span><span class="sxs-lookup"><span data-stu-id="e1449-115">Explanation</span></span>  
 <span data-ttu-id="e1449-116">這個錯誤/警告/資訊事件表示 BizTalk Server 無法解析為協議，根據客戶所提供的內容屬性。</span><span class="sxs-lookup"><span data-stu-id="e1449-116">This Error/Warning/Information event indicates BizTalk Server was not able to resolve to an Agreement based on the context properties that are provided by the customer.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="e1449-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="e1449-117">User Action</span></span>  
 <span data-ttu-id="e1449-118">若要解決這個錯誤，請提供的內容屬性做為 BizTalk 訊息的一部分，因此協議解析可能會發生。</span><span class="sxs-lookup"><span data-stu-id="e1449-118">To resolve this error, please provide the context properties as part of the BizTalk message such that Agreement Resolution can happen.</span></span>