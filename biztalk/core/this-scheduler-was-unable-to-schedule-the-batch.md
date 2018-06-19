---
title: 這個排程器無法排程批次 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4146124c-1eb0-4c1e-843b-b19c687a56b7
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2129e81168ee893adadb48a6c379d346d111fd60
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22278142"
---
# <a name="this-scheduler-was-unable-to-schedule-the-batch"></a><span data-ttu-id="71ea6-102">這個排程器無法排程批次</span><span class="sxs-lookup"><span data-stu-id="71ea6-102">This scheduler was unable to schedule the batch</span></span>
## <a name="details"></a><span data-ttu-id="71ea6-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="71ea6-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="71ea6-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="71ea6-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="71ea6-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="71ea6-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="71ea6-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="71ea6-106">Event ID</span></span>|-|  
|<span data-ttu-id="71ea6-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="71ea6-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="71ea6-108">EDI</span><span class="sxs-lookup"><span data-stu-id="71ea6-108"> EDI</span></span>|  
|<span data-ttu-id="71ea6-109">元件</span><span class="sxs-lookup"><span data-stu-id="71ea6-109">Component</span></span>|<span data-ttu-id="71ea6-110">批次處理引擎</span><span class="sxs-lookup"><span data-stu-id="71ea6-110">Batching Engine</span></span>|  
|<span data-ttu-id="71ea6-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="71ea6-111">Symbolic Name</span></span>|<span data-ttu-id="71ea6-112">UnableToScheduleBatch</span><span class="sxs-lookup"><span data-stu-id="71ea6-112">UnableToScheduleBatch</span></span>|  
|<span data-ttu-id="71ea6-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="71ea6-113">Message Text</span></span>|<span data-ttu-id="71ea6-114">這個排程器無法排程批次</span><span class="sxs-lookup"><span data-stu-id="71ea6-114">This scheduler was unable to schedule the batch</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="71ea6-115">說明</span><span class="sxs-lookup"><span data-stu-id="71ea6-115">Explanation</span></span>  
 <span data-ttu-id="71ea6-116">此錯誤表示排程器無法判斷下一個出現的批次釋放。</span><span class="sxs-lookup"><span data-stu-id="71ea6-116">This error indicates the scheduler could not determine the next occurrence of a batch release.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="71ea6-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="71ea6-117">User Action</span></span>  
 <span data-ttu-id="71ea6-118">若要解決這個錯誤，請確定排定的批次釋放是有效的。</span><span class="sxs-lookup"><span data-stu-id="71ea6-118">To resolve this error, make sure the batch release schedule is valid.</span></span>