---
title: BizTalk 商務活動監控尚未設定 EDI AS2 狀態報告 |Microsoft 文件
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
ms.openlocfilehash: e84301e55cd6fbdcb74467758c7e338e61b727f5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22241350"
---
# <a name="biztalk-business-activity-monitoring-has-not-been-configured-for-edi-as2-status-reporting"></a><span data-ttu-id="3a7f1-102">BizTalk 商務活動監控尚未設定 EDI AS2 狀態報告</span><span class="sxs-lookup"><span data-stu-id="3a7f1-102">BizTalk Business Activity Monitoring has not been configured for EDI-AS2 status reporting</span></span>
## <a name="details"></a><span data-ttu-id="3a7f1-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="3a7f1-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="3a7f1-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="3a7f1-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="3a7f1-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="3a7f1-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="3a7f1-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="3a7f1-106">Event ID</span></span>|-|  
|<span data-ttu-id="3a7f1-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="3a7f1-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="3a7f1-108">EDI</span><span class="sxs-lookup"><span data-stu-id="3a7f1-108"> EDI</span></span>|  
|<span data-ttu-id="3a7f1-109">元件</span><span class="sxs-lookup"><span data-stu-id="3a7f1-109">Component</span></span>|<span data-ttu-id="3a7f1-110">AS2 引擎</span><span class="sxs-lookup"><span data-stu-id="3a7f1-110">AS2 Engine</span></span>|  
|<span data-ttu-id="3a7f1-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="3a7f1-111">Symbolic Name</span></span>|-|  
|<span data-ttu-id="3a7f1-112">訊息文字</span><span class="sxs-lookup"><span data-stu-id="3a7f1-112">Message Text</span></span>|<span data-ttu-id="3a7f1-113">針對 EDI/AS2 狀態報告 BizTalk 商務活動監控尚未設定。</span><span class="sxs-lookup"><span data-stu-id="3a7f1-113">BizTalk Business Activity Monitoring has not been configured for EDI/AS2 status reporting.</span></span> <span data-ttu-id="3a7f1-114">因此會停用狀態報告功能。</span><span class="sxs-lookup"><span data-stu-id="3a7f1-114">Hence status reporting feature will be disabled.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="3a7f1-115">說明</span><span class="sxs-lookup"><span data-stu-id="3a7f1-115">Explanation</span></span>  
 <span data-ttu-id="3a7f1-116">這個錯誤/警告/資訊事件表示，EDI/AS2 狀態報告未啟用，因為尚未設定商務活動監控 (BAM) 透過 BizTalk 組態精靈。</span><span class="sxs-lookup"><span data-stu-id="3a7f1-116">This Error/Warning/Information event indicates that EDI/AS2 status reporting is not enabled because Business Activity Monitoring (BAM) has not been configured through the BizTalk Configuration Wizard.</span></span> <span data-ttu-id="3a7f1-117">BAM 基礎結構是 EDI/AS2 狀態報告的必要條件。</span><span class="sxs-lookup"><span data-stu-id="3a7f1-117">The BAM infrastructure is a prerequisite for EDI/AS2 status reporting.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="3a7f1-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="3a7f1-118">User Action</span></span>  
 <span data-ttu-id="3a7f1-119">若要解決這個錯誤，執行 BizTalk 組態精靈 並設定商務活動監控。</span><span class="sxs-lookup"><span data-stu-id="3a7f1-119">To resolve this error, run the BizTalk Configuration Wizard and configure Business Activity Monitoring.</span></span>