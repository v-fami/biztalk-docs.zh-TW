---
title: 找不到的通訊協定的後援設定 |Microsoft Docs
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
ms.openlocfilehash: 13d703e9cd82dde0dc0da55a630f69f1b42903e4
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36993119"
---
# <a name="fallback-settings-for-the-protocol-not-found"></a><span data-ttu-id="c98df-102">找不到的通訊協定的後援設定</span><span class="sxs-lookup"><span data-stu-id="c98df-102">Fallback Settings for the Protocol not found</span></span>
## <a name="details"></a><span data-ttu-id="c98df-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="c98df-103">Details</span></span>  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  <span data-ttu-id="c98df-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="c98df-104">Product Name</span></span>   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| <span data-ttu-id="c98df-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="c98df-105">Product Version</span></span> |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    <span data-ttu-id="c98df-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="c98df-106">Event ID</span></span>     |                                           -                                            |
|  <span data-ttu-id="c98df-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="c98df-107">Event Source</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="c98df-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="c98df-108"> EDI</span></span> |
|    <span data-ttu-id="c98df-109">元件</span><span class="sxs-lookup"><span data-stu-id="c98df-109">Component</span></span>    |                                       <span data-ttu-id="c98df-110">將 EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="c98df-110">EDI Engine</span></span>                                       |
|  <span data-ttu-id="c98df-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="c98df-111">Symbolic Name</span></span>  |                      <span data-ttu-id="c98df-112">AgreementResolutionFallbackSettingsNotFound</span><span class="sxs-lookup"><span data-stu-id="c98df-112">AgreementResolutionFallbackSettingsNotFound</span></span>                       |
|  <span data-ttu-id="c98df-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="c98df-113">Message Text</span></span>   |                   <span data-ttu-id="c98df-114">後援設定{0}找不到的通訊協定。</span><span class="sxs-lookup"><span data-stu-id="c98df-114">Fallback Settings for the {0} Protocol not found.</span></span>                    |
  
## <a name="explanation"></a><span data-ttu-id="c98df-115">說明</span><span class="sxs-lookup"><span data-stu-id="c98df-115">Explanation</span></span>  
 <span data-ttu-id="c98df-116">這個錯誤/警告/資訊事件表示 BizTalk Server 能夠解析為協議與已重新導向至後援設定並找到 後援設定有未針對特定的通訊協定。</span><span class="sxs-lookup"><span data-stu-id="c98df-116">This Error/Warning/Information event indicates BizTalk Server was able to resolve to an agreement and has been redirected to Fallback settings and found that the fallback settings were not there for the particular protocol.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="c98df-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="c98df-117">User Action</span></span>  
 <span data-ttu-id="c98df-118">若要解決這個錯誤，請設定特定通訊協定的後援設定。</span><span class="sxs-lookup"><span data-stu-id="c98df-118">To resolve this error, please configure the fallback settings for the particular protocol.</span></span>