---
title: 單一登入： 事件 10849 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fdfb1cea-e445-4318-9891-b6b70a266ca9
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1cb1d63cf12c19a8e2213c7506f1752f86a02a85
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36991847"
---
# <a name="single-sign-on-event-10849"></a><span data-ttu-id="7479e-102">單一登入： 事件 10849</span><span class="sxs-lookup"><span data-stu-id="7479e-102">Single Sign-On: Event 10849</span></span>
## <a name="details"></a><span data-ttu-id="7479e-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="7479e-103">Details</span></span>  
  
|                 |                                                                                  |
|-----------------|----------------------------------------------------------------------------------|
|  <span data-ttu-id="7479e-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="7479e-104">Product Name</span></span>   |                            <span data-ttu-id="7479e-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="7479e-105">Enterprise Single Sign-On</span></span>                             |
| <span data-ttu-id="7479e-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="7479e-106">Product Version</span></span> |            [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]            |
|    <span data-ttu-id="7479e-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="7479e-107">Event ID</span></span>     |                                      <span data-ttu-id="7479e-108">10849</span><span class="sxs-lookup"><span data-stu-id="7479e-108">10849</span></span>                                       |
|  <span data-ttu-id="7479e-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="7479e-109">Event Source</span></span>   |                                      <span data-ttu-id="7479e-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="7479e-110">ENTSSO</span></span>                                      |
|    <span data-ttu-id="7479e-111">元件</span><span class="sxs-lookup"><span data-stu-id="7479e-111">Component</span></span>    |                                       <span data-ttu-id="7479e-112">不適用</span><span class="sxs-lookup"><span data-stu-id="7479e-112">N/A</span></span>                                        |
|  <span data-ttu-id="7479e-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="7479e-113">Symbolic Name</span></span>  |                     <span data-ttu-id="7479e-114">ENTSSO_E_DIRECT_SYNC_NOT_ALLOWED_CREATE</span><span class="sxs-lookup"><span data-stu-id="7479e-114">ENTSSO_E_DIRECT_SYNC_NOT_ALLOWED_CREATE</span></span>                      |
|  <span data-ttu-id="7479e-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="7479e-115">Message Text</span></span>   | <span data-ttu-id="7479e-116">無法指定 'direct 密碼同步處理' 旗標建立應用程式。</span><span class="sxs-lookup"><span data-stu-id="7479e-116">An application cannot be created with the ‘direct password sync’ flag specified.</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="7479e-117">說明</span><span class="sxs-lookup"><span data-stu-id="7479e-117">Explanation</span></span>  
 <span data-ttu-id="7479e-118">無法指定 'direct 密碼同步處理' 旗標建立應用程式。</span><span class="sxs-lookup"><span data-stu-id="7479e-118">An application cannot be created with the ‘direct password sync’ flag specified.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="7479e-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="7479e-119">User Action</span></span>  
 <span data-ttu-id="7479e-120">建立應用程式，而不需要直接密碼同步旗標。</span><span class="sxs-lookup"><span data-stu-id="7479e-120">Create the application without the direct password sync flag.</span></span> <span data-ttu-id="7479e-121">接著加入和建立欄位，讓應用程式，並且指定直接密碼同步旗標。</span><span class="sxs-lookup"><span data-stu-id="7479e-121">Then add and create the fields, enable the application, and specify the direct password sync flag.</span></span>