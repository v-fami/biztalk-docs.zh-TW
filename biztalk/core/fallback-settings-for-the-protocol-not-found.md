---
title: 找不到通訊協定的後援設定 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d93e5db1-16a3-4796-8fa2-fef934508034
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a5b3f8ea35f4f29859f5156ff254137ea7a8f8db
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22245902"
---
# <a name="fallback-settings-for-the-protocol-not-found"></a><span data-ttu-id="b4536-102">找不到通訊協定的後援設定</span><span class="sxs-lookup"><span data-stu-id="b4536-102">Fallback Settings for the Protocol not found</span></span>
## <a name="details"></a><span data-ttu-id="b4536-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="b4536-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b4536-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="b4536-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="b4536-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="b4536-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="b4536-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="b4536-106">Event ID</span></span>|-|  
|<span data-ttu-id="b4536-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="b4536-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="b4536-108">EDI</span><span class="sxs-lookup"><span data-stu-id="b4536-108"> EDI</span></span>|  
|<span data-ttu-id="b4536-109">元件</span><span class="sxs-lookup"><span data-stu-id="b4536-109">Component</span></span>|<span data-ttu-id="b4536-110">EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="b4536-110">EDI Engine</span></span>|  
|<span data-ttu-id="b4536-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="b4536-111">Symbolic Name</span></span>|<span data-ttu-id="b4536-112">AgreementResolutionFallbackSettingsNotFound</span><span class="sxs-lookup"><span data-stu-id="b4536-112">AgreementResolutionFallbackSettingsNotFound</span></span>|  
|<span data-ttu-id="b4536-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="b4536-113">Message Text</span></span>|<span data-ttu-id="b4536-114">後援 {0} 找不到通訊協定的設定。</span><span class="sxs-lookup"><span data-stu-id="b4536-114">Fallback Settings for the {0} Protocol not found.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="b4536-115">說明</span><span class="sxs-lookup"><span data-stu-id="b4536-115">Explanation</span></span>  
 <span data-ttu-id="b4536-116">這個錯誤/警告/資訊事件表示 BizTalk 伺服器無法解析為協議並已重新導向至後援設定，找到 後援設定有沒有特定的通訊協定。</span><span class="sxs-lookup"><span data-stu-id="b4536-116">This Error/Warning/Information event indicates BizTalk Server was able to resolve to an agreement and has been redirected to Fallback settings and found that the fallback settings were not there for the particular protocol.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="b4536-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="b4536-117">User Action</span></span>  
 <span data-ttu-id="b4536-118">若要解決這個錯誤，請設定特定通訊協定的後援設定。</span><span class="sxs-lookup"><span data-stu-id="b4536-118">To resolve this error, please configure the fallback settings for the particular protocol.</span></span>