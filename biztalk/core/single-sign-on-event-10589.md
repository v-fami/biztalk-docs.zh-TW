---
title: 單一登入： 事件 10589 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0fe962bb-e9bb-4107-a5fb-21c180d54e21
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b1f8dd6c8a6045f9e4e1678aa06faec8bb783c1a
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36986183"
---
# <a name="single-sign-on-event-10589"></a><span data-ttu-id="551d3-102">單一登入： 事件 10589</span><span class="sxs-lookup"><span data-stu-id="551d3-102">Single Sign-On: Event 10589</span></span>
## <a name="details"></a><span data-ttu-id="551d3-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="551d3-103">Details</span></span>  
  
|                 |                                                                                                                                                                                                                                                                   |
|-----------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="551d3-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="551d3-104">Product Name</span></span>   |                                                                                                                     <span data-ttu-id="551d3-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="551d3-105">Enterprise Single Sign-On</span></span>                                                                                                                     |
| <span data-ttu-id="551d3-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="551d3-106">Product Version</span></span> |                                                                                                    [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                                                     |
|    <span data-ttu-id="551d3-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="551d3-107">Event ID</span></span>     |                                                                                                                               <span data-ttu-id="551d3-108">10589</span><span class="sxs-lookup"><span data-stu-id="551d3-108">10589</span></span>                                                                                                                               |
|  <span data-ttu-id="551d3-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="551d3-109">Event Source</span></span>   |                                                                                                                              <span data-ttu-id="551d3-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="551d3-110">ENTSSO</span></span>                                                                                                                               |
|    <span data-ttu-id="551d3-111">元件</span><span class="sxs-lookup"><span data-stu-id="551d3-111">Component</span></span>    |                                                                                                                                <span data-ttu-id="551d3-112">不適用</span><span class="sxs-lookup"><span data-stu-id="551d3-112">N/A</span></span>                                                                                                                                |
|  <span data-ttu-id="551d3-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="551d3-113">Symbolic Name</span></span>  |                                                                                                                 <span data-ttu-id="551d3-114">SSO_ERROR_BACKUP_SECRET_REQUIRED</span><span class="sxs-lookup"><span data-stu-id="551d3-114">SSO_ERROR_BACKUP_SECRET_REQUIRED</span></span>                                                                                                                  |
|  <span data-ttu-id="551d3-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="551d3-115">Message Text</span></span>   | <span data-ttu-id="551d3-116">主要祕密尚未備份。</span><span class="sxs-lookup"><span data-stu-id="551d3-116">The master secret has not been backed up.</span></span> <span data-ttu-id="551d3-117">如果您遺失主要祕密儲存在 SSO 系統中的所有資訊將都會永久遺失，和您的系統可能無法正確運作。</span><span class="sxs-lookup"><span data-stu-id="551d3-117">If you lose the master secret all the information stored in the SSO system will be lost permanently and your systems may fail to work correctly.</span></span> <span data-ttu-id="551d3-118">請使用 SSO 管理工具來備份您的主要祕密。</span><span class="sxs-lookup"><span data-stu-id="551d3-118">Please use the SSO administration tools to back up your master secret.</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="551d3-119">說明</span><span class="sxs-lookup"><span data-stu-id="551d3-119">Explanation</span></span>  
 <span data-ttu-id="551d3-120">主要祕密尚未備份。</span><span class="sxs-lookup"><span data-stu-id="551d3-120">The master secret has not been backed up.</span></span> <span data-ttu-id="551d3-121">如果您遺失主要祕密儲存在 SSO 系統中的所有資訊將都會永久遺失，和您的系統可能無法正確運作。</span><span class="sxs-lookup"><span data-stu-id="551d3-121">If you lose the master secret all the information stored in the SSO system will be lost permanently and your systems may fail to work correctly.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="551d3-122">使用者動作</span><span class="sxs-lookup"><span data-stu-id="551d3-122">User Action</span></span>  
 <span data-ttu-id="551d3-123">如需備份主要祕密的資訊，請參閱 <<c0> [ 管理主要密碼](../core/managing-the-master-secret.md)。</span><span class="sxs-lookup"><span data-stu-id="551d3-123">For information on backing up the master secret, see [Managing the Master Secret](../core/managing-the-master-secret.md).</span></span>