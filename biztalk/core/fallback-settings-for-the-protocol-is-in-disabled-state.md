---
title: 後援設定通訊協定處於停用 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f14a5e46-1028-4250-af7b-8137fa927d7e
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9060dbe2bf3644310d862d4949d2cf944269105d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22245774"
---
# <a name="fallback-settings-for-the-protocol-is-in-disabled-state"></a><span data-ttu-id="6b93f-102">後援設定通訊協定處於停用狀態</span><span class="sxs-lookup"><span data-stu-id="6b93f-102">Fallback Settings for the Protocol is in Disabled state</span></span>
## <a name="details"></a><span data-ttu-id="6b93f-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="6b93f-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6b93f-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="6b93f-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="6b93f-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="6b93f-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="6b93f-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="6b93f-106">Event ID</span></span>|-|  
|<span data-ttu-id="6b93f-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="6b93f-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="6b93f-108">EDI</span><span class="sxs-lookup"><span data-stu-id="6b93f-108"> EDI</span></span>|  
|<span data-ttu-id="6b93f-109">元件</span><span class="sxs-lookup"><span data-stu-id="6b93f-109">Component</span></span>|<span data-ttu-id="6b93f-110">EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="6b93f-110">EDI Engine</span></span>|  
|<span data-ttu-id="6b93f-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="6b93f-111">Symbolic Name</span></span>|<span data-ttu-id="6b93f-112">AgreementResolutionFallbackSettingsDisabled</span><span class="sxs-lookup"><span data-stu-id="6b93f-112">AgreementResolutionFallbackSettingsDisabled</span></span>|  
|<span data-ttu-id="6b93f-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="6b93f-113">Message Text</span></span>|<span data-ttu-id="6b93f-114">{0} 後援設定通訊協定處於停用狀態。</span><span class="sxs-lookup"><span data-stu-id="6b93f-114">Fallback Settings for the {0} Protocol is in Disabled state.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="6b93f-115">說明</span><span class="sxs-lookup"><span data-stu-id="6b93f-115">Explanation</span></span>  
 <span data-ttu-id="6b93f-116">這個錯誤/警告/資訊事件表示 BizTalk 伺服器能夠解析為協議與已重新導向至後援設定，找到 後援設定已停用狀態的特定通訊協定。</span><span class="sxs-lookup"><span data-stu-id="6b93f-116">This Error/Warning/Information event indicates BizTalk Server was able to resolve to an agreement and has been redirected to Fallback settings and found that the fallback settings were in disabled state for the particular protocol.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="6b93f-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="6b93f-117">User Action</span></span>  
 <span data-ttu-id="6b93f-118">若要解決這個錯誤，請啟用後援設定特定通訊協定。</span><span class="sxs-lookup"><span data-stu-id="6b93f-118">To resolve this error, please enable the fallback settings for the particular protocol.</span></span>