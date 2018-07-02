---
title: 單一登入： 事件 10765 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e28fe42e-aa2b-4be4-b757-bc9c5c37526b
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bd49ead3fc30d3b98ea804a98a5882696ea749d7
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36975103"
---
# <a name="single-sign-on-event-10765"></a><span data-ttu-id="35bea-102">單一登入： 事件 10765</span><span class="sxs-lookup"><span data-stu-id="35bea-102">Single Sign-On: Event 10765</span></span>
## <a name="details"></a><span data-ttu-id="35bea-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="35bea-103">Details</span></span>  
  
|                 |                                                            |
|-----------------|------------------------------------------------------------|
|  <span data-ttu-id="35bea-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="35bea-104">Product Name</span></span>   |                 <span data-ttu-id="35bea-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="35bea-105">Enterprise Single Sign-On</span></span>                  |
| <span data-ttu-id="35bea-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="35bea-106">Product Version</span></span> | [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)] |
|    <span data-ttu-id="35bea-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="35bea-107">Event ID</span></span>     |                           <span data-ttu-id="35bea-108">10765</span><span class="sxs-lookup"><span data-stu-id="35bea-108">10765</span></span>                            |
|  <span data-ttu-id="35bea-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="35bea-109">Event Source</span></span>   |                           <span data-ttu-id="35bea-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="35bea-110">ENTSSO</span></span>                           |
|    <span data-ttu-id="35bea-111">元件</span><span class="sxs-lookup"><span data-stu-id="35bea-111">Component</span></span>    |                            <span data-ttu-id="35bea-112">不適用</span><span class="sxs-lookup"><span data-stu-id="35bea-112">N/A</span></span>                             |
|  <span data-ttu-id="35bea-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="35bea-113">Symbolic Name</span></span>  |                  <span data-ttu-id="35bea-114">ENTSSO_E_NO_CREDENTIALS</span><span class="sxs-lookup"><span data-stu-id="35bea-114">ENTSSO_E_NO_CREDENTIALS</span></span>                   |
|  <span data-ttu-id="35bea-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="35bea-115">Message Text</span></span>   |       <span data-ttu-id="35bea-116">對應已設定無認證。</span><span class="sxs-lookup"><span data-stu-id="35bea-116">No credentials have been set for the mapping.</span></span>        |
  
## <a name="explanation"></a><span data-ttu-id="35bea-117">說明</span><span class="sxs-lookup"><span data-stu-id="35bea-117">Explanation</span></span>  
 <span data-ttu-id="35bea-118">您所要求上的對應，GetCredentials 和指定的對應中沒有任何憑證。</span><span class="sxs-lookup"><span data-stu-id="35bea-118">You have requested a GetCredentials on a mapping, and the mapping specified has no credentials.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="35bea-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="35bea-119">User Action</span></span>  
 <span data-ttu-id="35bea-120">使用命令列或 MMC 嵌入式管理單元來設定對應的認證。</span><span class="sxs-lookup"><span data-stu-id="35bea-120">Use the command line or the MMC Snap-in to set credentials for the mapping.</span></span>