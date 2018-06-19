---
title: 協議解析根據內容屬性失敗，通訊協定 |Microsoft 文件
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
ms.openlocfilehash: 76d74ad7aa4a73f4a0befcef32bc8051195cb080
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22229934"
---
# <a name="agreement-resolution-based-on-the-context-properties-for-protocol-has-failed"></a><span data-ttu-id="0d345-102">無法解析通訊協定根據內容屬性的協議</span><span class="sxs-lookup"><span data-stu-id="0d345-102">Agreement Resolution based on the context properties for Protocol has failed</span></span>
## <a name="details"></a><span data-ttu-id="0d345-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="0d345-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="0d345-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="0d345-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="0d345-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="0d345-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="0d345-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="0d345-106">Event ID</span></span>|-|  
|<span data-ttu-id="0d345-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="0d345-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="0d345-108">EDI</span><span class="sxs-lookup"><span data-stu-id="0d345-108"> EDI</span></span>|  
|<span data-ttu-id="0d345-109">元件</span><span class="sxs-lookup"><span data-stu-id="0d345-109">Component</span></span>|<span data-ttu-id="0d345-110">EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="0d345-110">EDI Engine</span></span>|  
|<span data-ttu-id="0d345-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="0d345-111">Symbolic Name</span></span>|<span data-ttu-id="0d345-112">AgreementResolutionContextPropertiesLookupFailed</span><span class="sxs-lookup"><span data-stu-id="0d345-112">AgreementResolutionContextPropertiesLookupFailed</span></span>|  
|<span data-ttu-id="0d345-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="0d345-113">Message Text</span></span>|<span data-ttu-id="0d345-114">協議解析根據 {0} 通訊協定失敗的內容屬性。</span><span class="sxs-lookup"><span data-stu-id="0d345-114">Agreement Resolution based on the context properties for {0} Protocol has failed.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="0d345-115">說明</span><span class="sxs-lookup"><span data-stu-id="0d345-115">Explanation</span></span>  
 <span data-ttu-id="0d345-116">這個錯誤/警告/資訊事件表示 BizTalk Server 無法解析為協議，根據客戶所提供的內容屬性。</span><span class="sxs-lookup"><span data-stu-id="0d345-116">This Error/Warning/Information event indicates BizTalk Server was not able to resolve to an Agreement based on the context properties that are provided by the customer.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="0d345-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="0d345-117">User Action</span></span>  
 <span data-ttu-id="0d345-118">若要解決這個錯誤，請提供的內容屬性做為 BizTalk 訊息的一部分，可能是協議解析。</span><span class="sxs-lookup"><span data-stu-id="0d345-118">To resolve this error, please provide the context properties as part of the BizTalk message such that Agreement Resolution can happen.</span></span>