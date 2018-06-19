---
title: 單一登入： 事件 10604 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eea14ab1-5a89-4a62-b414-1bcb36ea339e
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0d9d6858fb13542ca642c9c48a8a187b66ba6526
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22270542"
---
# <a name="single-sign-on-event-10604"></a><span data-ttu-id="ef83e-102">單一登入： 事件 10604</span><span class="sxs-lookup"><span data-stu-id="ef83e-102">Single Sign-On: Event 10604</span></span>
## <a name="details"></a><span data-ttu-id="ef83e-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="ef83e-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ef83e-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="ef83e-104">Product Name</span></span>|<span data-ttu-id="ef83e-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="ef83e-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="ef83e-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="ef83e-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="ef83e-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="ef83e-107">Event ID</span></span>|<span data-ttu-id="ef83e-108">10604</span><span class="sxs-lookup"><span data-stu-id="ef83e-108">10604</span></span>|  
|<span data-ttu-id="ef83e-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="ef83e-109">Event Source</span></span>|<span data-ttu-id="ef83e-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="ef83e-110">ENTSSO</span></span>|  
|<span data-ttu-id="ef83e-111">元件</span><span class="sxs-lookup"><span data-stu-id="ef83e-111">Component</span></span>|<span data-ttu-id="ef83e-112">不適用</span><span class="sxs-lookup"><span data-stu-id="ef83e-112">N/A</span></span>|  
|<span data-ttu-id="ef83e-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="ef83e-113">Symbolic Name</span></span>|<span data-ttu-id="ef83e-114">SSO_ERROR_SSOCSTX_OUT_OF_PROC</span><span class="sxs-lookup"><span data-stu-id="ef83e-114">SSO_ERROR_SSOCSTX_OUT_OF_PROC</span></span>|  
|<span data-ttu-id="ef83e-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="ef83e-115">Message Text</span></span>|<span data-ttu-id="ef83e-116">' ENTSSO Server' COM + 應用程式未正確設定。</span><span class="sxs-lookup"><span data-stu-id="ef83e-116">The 'ENTSSO Server' COM+ application is not configured correctly.</span></span> <span data-ttu-id="ef83e-117">它必須是 COM + 程式庫應用程式。</span><span class="sxs-lookup"><span data-stu-id="ef83e-117">It must be a COM+ library application.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="ef83e-118">說明</span><span class="sxs-lookup"><span data-stu-id="ef83e-118">Explanation</span></span>  
 <span data-ttu-id="ef83e-119">COM + 應用程式必須設定為 COM + 程式庫應用程式。</span><span class="sxs-lookup"><span data-stu-id="ef83e-119">The COM+ application must be configured as a COM+ library application.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="ef83e-120">使用者動作</span><span class="sxs-lookup"><span data-stu-id="ef83e-120">User Action</span></span>  
 <span data-ttu-id="ef83e-121">在 ENTSSO MMC 嵌入式管理單元中，展開 COM + 資料夾，並找出您 ENTSSO 伺服器。</span><span class="sxs-lookup"><span data-stu-id="ef83e-121">In the ENTSSO MMC Snap-In, expand the COM+ folder and locate your ENTSSO Server.</span></span> <span data-ttu-id="ef83e-122">以滑鼠右鍵按一下伺服器，然後按一下 屬性。</span><span class="sxs-lookup"><span data-stu-id="ef83e-122">Right-click the server, and then click Properties.</span></span> <span data-ttu-id="ef83e-123">選取程式庫應用程式，而不是伺服器應用程式，然後按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="ef83e-123">Select Library Application instead of Server Application, and click OK.</span></span>