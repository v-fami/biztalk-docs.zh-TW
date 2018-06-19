---
title: 單一登入： 事件 10563 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7c944cc4-7fe0-41cc-9608-ee954e8222e0
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e2ff30e245350004d798b0c6c2950b5bab345e77
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22269710"
---
# <a name="single-sign-on-event-10563"></a><span data-ttu-id="2be86-102">單一登入： 事件 10563</span><span class="sxs-lookup"><span data-stu-id="2be86-102">Single Sign-On: Event 10563</span></span>
## <a name="details"></a><span data-ttu-id="2be86-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="2be86-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2be86-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="2be86-104">Product Name</span></span>|<span data-ttu-id="2be86-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="2be86-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="2be86-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="2be86-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="2be86-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="2be86-107">Event ID</span></span>|<span data-ttu-id="2be86-108">10563</span><span class="sxs-lookup"><span data-stu-id="2be86-108">10563</span></span>|  
|<span data-ttu-id="2be86-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="2be86-109">Event Source</span></span>|<span data-ttu-id="2be86-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="2be86-110">ENTSSO</span></span>|  
|<span data-ttu-id="2be86-111">元件</span><span class="sxs-lookup"><span data-stu-id="2be86-111">Component</span></span>|<span data-ttu-id="2be86-112">不適用</span><span class="sxs-lookup"><span data-stu-id="2be86-112">N/A</span></span>|  
|<span data-ttu-id="2be86-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="2be86-113">Symbolic Name</span></span>|<span data-ttu-id="2be86-114">SSO_WARN_PERFMON_FAILED</span><span class="sxs-lookup"><span data-stu-id="2be86-114">SSO_WARN_PERFMON_FAILED</span></span>|  
|<span data-ttu-id="2be86-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="2be86-115">Message Text</span></span>|<span data-ttu-id="2be86-116">無法啟動效能監控 start.%r</span><span class="sxs-lookup"><span data-stu-id="2be86-116">Performance monitoring failed to start.%r</span></span><br /><br /> <span data-ttu-id="2be86-117">錯誤碼： %1</span><span class="sxs-lookup"><span data-stu-id="2be86-117">Error Code: %1</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="2be86-118">說明</span><span class="sxs-lookup"><span data-stu-id="2be86-118">Explanation</span></span>  
 <span data-ttu-id="2be86-119">效能監視無法啟動。</span><span class="sxs-lookup"><span data-stu-id="2be86-119">Performance monitoring failed to start.</span></span> <span data-ttu-id="2be86-120">系統會繼續正常執行，但效能監視將無法使用。</span><span class="sxs-lookup"><span data-stu-id="2be86-120">The system will continue to run normally but performance monitoring will not be available.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="2be86-121">使用者動作</span><span class="sxs-lookup"><span data-stu-id="2be86-121">User Action</span></span>  
 <span data-ttu-id="2be86-122">它可能需要解除安裝再重新安裝 perfmon 的公用程式。</span><span class="sxs-lookup"><span data-stu-id="2be86-122">It may be necessary to uninstall and reinstall the perfmon utility.</span></span>