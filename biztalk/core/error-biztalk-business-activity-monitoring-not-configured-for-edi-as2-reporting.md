---
title: BizTalk 商務活動監控尚未設定 EDI-AS2 狀態報告 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2f46c1c8-2771-4b16-8fb1-71952792ac4a
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: eb2a6b9d6eaa6ac14f51c7f05e40a9f6ccffccd5
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37010527"
---
# <a name="biztalk-business-activity-monitoring-has-not-been-configured-for-edi-as2-status-reporting"></a><span data-ttu-id="94f87-102">BizTalk 商務活動監控尚未設定 EDI-AS2 狀態報告</span><span class="sxs-lookup"><span data-stu-id="94f87-102">BizTalk Business Activity Monitoring has not been configured for EDI-AS2 status reporting</span></span>
## <a name="details"></a><span data-ttu-id="94f87-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="94f87-103">Details</span></span>  
  
|                 |                                                                                                                                             |
|-----------------|---------------------------------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="94f87-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="94f87-104">Product Name</span></span>   |                             [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                              |
| <span data-ttu-id="94f87-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="94f87-105">Product Version</span></span> |                                         [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                          |
|    <span data-ttu-id="94f87-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="94f87-106">Event ID</span></span>     |                                                                      -                                                                      |
|  <span data-ttu-id="94f87-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="94f87-107">Event Source</span></span>   |                           [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="94f87-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="94f87-108"> EDI</span></span>                            |
|    <span data-ttu-id="94f87-109">元件</span><span class="sxs-lookup"><span data-stu-id="94f87-109">Component</span></span>    |                                                                 <span data-ttu-id="94f87-110">AS2 引擎</span><span class="sxs-lookup"><span data-stu-id="94f87-110">AS2 Engine</span></span>                                                                  |
|  <span data-ttu-id="94f87-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="94f87-111">Symbolic Name</span></span>  |                                                                      -                                                                      |
|  <span data-ttu-id="94f87-112">訊息文字</span><span class="sxs-lookup"><span data-stu-id="94f87-112">Message Text</span></span>   | <span data-ttu-id="94f87-113">EDI/AS2 狀態報告 BizTalk 商務活動監控尚未設定。</span><span class="sxs-lookup"><span data-stu-id="94f87-113">BizTalk Business Activity Monitoring has not been configured for EDI/AS2 status reporting.</span></span> <span data-ttu-id="94f87-114">因此將停用狀態報告功能。</span><span class="sxs-lookup"><span data-stu-id="94f87-114">Hence status reporting feature will be disabled.</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="94f87-115">說明</span><span class="sxs-lookup"><span data-stu-id="94f87-115">Explanation</span></span>  
 <span data-ttu-id="94f87-116">這個錯誤/警告/資訊事件表示，EDI/AS2 狀態報告未啟用，因為尚未設定商務活動監控 (BAM) 透過 「 BizTalk 組態精靈 」。</span><span class="sxs-lookup"><span data-stu-id="94f87-116">This Error/Warning/Information event indicates that EDI/AS2 status reporting is not enabled because Business Activity Monitoring (BAM) has not been configured through the BizTalk Configuration Wizard.</span></span> <span data-ttu-id="94f87-117">BAM 基礎結構是 EDI/AS2 狀態報告的必要條件。</span><span class="sxs-lookup"><span data-stu-id="94f87-117">The BAM infrastructure is a prerequisite for EDI/AS2 status reporting.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="94f87-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="94f87-118">User Action</span></span>  
 <span data-ttu-id="94f87-119">若要解決這個錯誤，請執行 BizTalk 組態精靈設定商務活動監控。</span><span class="sxs-lookup"><span data-stu-id="94f87-119">To resolve this error, run the BizTalk Configuration Wizard and configure Business Activity Monitoring.</span></span>