---
title: 單一登入： 事件 10809 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7331d12b-1000-4a60-83b3-f092968e0e51
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4d4bf5ba006af8c479abc621accdc28296c0eae3
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37016061"
---
# <a name="single-sign-on-event-10809"></a><span data-ttu-id="d213d-102">單一登入： 事件 10809</span><span class="sxs-lookup"><span data-stu-id="d213d-102">Single Sign-On: Event 10809</span></span>
## <a name="details"></a><span data-ttu-id="d213d-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="d213d-103">Details</span></span>  
  
|                 |                                                                   |
|-----------------|-------------------------------------------------------------------|
|  <span data-ttu-id="d213d-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="d213d-104">Product Name</span></span>   |                     <span data-ttu-id="d213d-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="d213d-105">Enterprise Single Sign-On</span></span>                     |
| <span data-ttu-id="d213d-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="d213d-106">Product Version</span></span> |    [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]     |
|    <span data-ttu-id="d213d-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="d213d-107">Event ID</span></span>     |                               <span data-ttu-id="d213d-108">10809</span><span class="sxs-lookup"><span data-stu-id="d213d-108">10809</span></span>                               |
|  <span data-ttu-id="d213d-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="d213d-109">Event Source</span></span>   |                              <span data-ttu-id="d213d-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="d213d-110">ENTSSO</span></span>                               |
|    <span data-ttu-id="d213d-111">元件</span><span class="sxs-lookup"><span data-stu-id="d213d-111">Component</span></span>    |                                <span data-ttu-id="d213d-112">不適用</span><span class="sxs-lookup"><span data-stu-id="d213d-112">N/A</span></span>                                |
|  <span data-ttu-id="d213d-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="d213d-113">Symbolic Name</span></span>  |                  <span data-ttu-id="d213d-114">ENTSSO_E_HISSO_APP_NOT_ENABLED</span><span class="sxs-lookup"><span data-stu-id="d213d-114">ENTSSO_E_HISSO_APP_NOT_ENABLED</span></span>                   |
|  <span data-ttu-id="d213d-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="d213d-115">Message Text</span></span>   | <span data-ttu-id="d213d-116">應用程式未啟用主控件初始化的單一登入。</span><span class="sxs-lookup"><span data-stu-id="d213d-116">The application is not enabled for Host Initiated Single Sign-On.</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="d213d-117">說明</span><span class="sxs-lookup"><span data-stu-id="d213d-117">Explanation</span></span>  
 <span data-ttu-id="d213d-118">應用程式未啟用主控件初始化的單一登入。</span><span class="sxs-lookup"><span data-stu-id="d213d-118">The application is not enabled for Host Initiated Single Sign-On.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="d213d-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="d213d-119">User Action</span></span>  
 <span data-ttu-id="d213d-120">使用系統管理工具來設定主應用程式起始單一登入。</span><span class="sxs-lookup"><span data-stu-id="d213d-120">Use the administrative tools to configure Host Initiated Single Sign-On.</span></span> <span data-ttu-id="d213d-121">這將會設定</span><span class="sxs-lookup"><span data-stu-id="d213d-121">This will set the</span></span>  
  
 <span data-ttu-id="d213d-122">在應用程式上的 SSO_FLAG_SSO_EXTERNAL_TO_WINDOWS 旗標。</span><span class="sxs-lookup"><span data-stu-id="d213d-122">SSO_FLAG_SSO_EXTERNAL_TO_WINDOWS flag on the application.</span></span>