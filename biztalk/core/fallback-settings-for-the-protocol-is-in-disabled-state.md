---
title: 通訊協定的後援設定處於停用狀態 |Microsoft Docs
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
ms.openlocfilehash: c1661aed16d2a63b158f3e1ae886b7dde381da14
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36983439"
---
# <a name="fallback-settings-for-the-protocol-is-in-disabled-state"></a><span data-ttu-id="8c0c5-102">通訊協定的後援設定處於停用狀態</span><span class="sxs-lookup"><span data-stu-id="8c0c5-102">Fallback Settings for the Protocol is in Disabled state</span></span>
## <a name="details"></a><span data-ttu-id="8c0c5-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="8c0c5-103">Details</span></span>  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  <span data-ttu-id="8c0c5-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="8c0c5-104">Product Name</span></span>   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| <span data-ttu-id="8c0c5-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="8c0c5-105">Product Version</span></span> |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    <span data-ttu-id="8c0c5-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="8c0c5-106">Event ID</span></span>     |                                           -                                            |
|  <span data-ttu-id="8c0c5-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="8c0c5-107">Event Source</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="8c0c5-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="8c0c5-108"> EDI</span></span> |
|    <span data-ttu-id="8c0c5-109">元件</span><span class="sxs-lookup"><span data-stu-id="8c0c5-109">Component</span></span>    |                                       <span data-ttu-id="8c0c5-110">將 EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="8c0c5-110">EDI Engine</span></span>                                       |
|  <span data-ttu-id="8c0c5-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="8c0c5-111">Symbolic Name</span></span>  |                      <span data-ttu-id="8c0c5-112">AgreementResolutionFallbackSettingsDisabled</span><span class="sxs-lookup"><span data-stu-id="8c0c5-112">AgreementResolutionFallbackSettingsDisabled</span></span>                       |
|  <span data-ttu-id="8c0c5-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="8c0c5-113">Message Text</span></span>   |              <span data-ttu-id="8c0c5-114">後援設定{0}通訊協定處於停用狀態。</span><span class="sxs-lookup"><span data-stu-id="8c0c5-114">Fallback Settings for the {0} Protocol is in Disabled state.</span></span>              |
  
## <a name="explanation"></a><span data-ttu-id="8c0c5-115">說明</span><span class="sxs-lookup"><span data-stu-id="8c0c5-115">Explanation</span></span>  
 <span data-ttu-id="8c0c5-116">這個錯誤/警告/資訊事件表示 BizTalk Server 能夠解析為協議與已重新導向至後援設定並找到 後援設定處於停用狀態的特定通訊協定。</span><span class="sxs-lookup"><span data-stu-id="8c0c5-116">This Error/Warning/Information event indicates BizTalk Server was able to resolve to an agreement and has been redirected to Fallback settings and found that the fallback settings were in disabled state for the particular protocol.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="8c0c5-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="8c0c5-117">User Action</span></span>  
 <span data-ttu-id="8c0c5-118">若要解決這個錯誤，請啟用特定的通訊協定的後援設定。</span><span class="sxs-lookup"><span data-stu-id="8c0c5-118">To resolve this error, please enable the fallback settings for the particular protocol.</span></span>