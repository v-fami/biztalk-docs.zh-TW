---
title: 單一登入： 事件 10595 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1517478c-7217-4e34-a5cb-ff7deea367ed
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0cbc952197971f4e0db0586bc4f1d2d6c37aba44
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36995223"
---
# <a name="single-sign-on-event-10595"></a><span data-ttu-id="bae16-102">單一登入： 事件 10595</span><span class="sxs-lookup"><span data-stu-id="bae16-102">Single Sign-On: Event 10595</span></span>
## <a name="details"></a><span data-ttu-id="bae16-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="bae16-103">Details</span></span>  
  
|                 |                                                                                                                                                                                                                    |
|-----------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="bae16-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="bae16-104">Product Name</span></span>   |                                                                                             <span data-ttu-id="bae16-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="bae16-105">Enterprise Single Sign-On</span></span>                                                                                              |
| <span data-ttu-id="bae16-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="bae16-106">Product Version</span></span> |                                                                             [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                             |
|    <span data-ttu-id="bae16-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="bae16-107">Event ID</span></span>     |                                                                                                       <span data-ttu-id="bae16-108">10595</span><span class="sxs-lookup"><span data-stu-id="bae16-108">10595</span></span>                                                                                                        |
|  <span data-ttu-id="bae16-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="bae16-109">Event Source</span></span>   |                                                                                                       <span data-ttu-id="bae16-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="bae16-110">ENTSSO</span></span>                                                                                                       |
|    <span data-ttu-id="bae16-111">元件</span><span class="sxs-lookup"><span data-stu-id="bae16-111">Component</span></span>    |                                                                                                        <span data-ttu-id="bae16-112">不適用</span><span class="sxs-lookup"><span data-stu-id="bae16-112">N/A</span></span>                                                                                                         |
|  <span data-ttu-id="bae16-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="bae16-113">Symbolic Name</span></span>  |                                                                                           <span data-ttu-id="bae16-114">SSO_WARN_APP_INCOMPLETE_FIELDS</span><span class="sxs-lookup"><span data-stu-id="bae16-114">SSO_WARN_APP_INCOMPLETE_FIELDS</span></span>                                                                                           |
|  <span data-ttu-id="bae16-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="bae16-115">Message Text</span></span>   | <span data-ttu-id="bae16-116">無法啟用應用程式，因為欄位不完整，此 application.%r</span><span class="sxs-lookup"><span data-stu-id="bae16-116">The application cannot be enabled because the fields are incomplete for this application.%r</span></span><br /><br /> <span data-ttu-id="bae16-117">應用程式名稱: %1 %r</span><span class="sxs-lookup"><span data-stu-id="bae16-117">Application Name: %1%r</span></span><br /><br /> <span data-ttu-id="bae16-118">定義的欄位數目: %2 %r</span><span class="sxs-lookup"><span data-stu-id="bae16-118">Number of Fields Defined: %2%r</span></span><br /><br /> <span data-ttu-id="bae16-119">建立的欄位數目： %3</span><span class="sxs-lookup"><span data-stu-id="bae16-119">Number of Fields Created: %3</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="bae16-120">說明</span><span class="sxs-lookup"><span data-stu-id="bae16-120">Explanation</span></span>  
 <span data-ttu-id="bae16-121">在建立時應用程式的 API 層級，您會指定的欄位 （也就是使用者識別碼，密碼） 會定義應用程式數目。</span><span class="sxs-lookup"><span data-stu-id="bae16-121">When creating an application at the API level, you specified the number of fields (i.e. UserID, Password) the application would define.</span></span> <span data-ttu-id="bae16-122">也必須建立已定義的每個欄位。</span><span class="sxs-lookup"><span data-stu-id="bae16-122">Each field that has been defined must also be created.</span></span> <span data-ttu-id="bae16-123">這則警告訊息會列出應用程式名稱、 定義的欄位數目和建立的欄位數目。</span><span class="sxs-lookup"><span data-stu-id="bae16-123">This warning message lists the application name, number of fields defined, and number of fields created.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="bae16-124">使用者動作</span><span class="sxs-lookup"><span data-stu-id="bae16-124">User Action</span></span>  
 <span data-ttu-id="bae16-125">判斷哪些欄位所定義，但不是會建立，然後返回，並建立它們。</span><span class="sxs-lookup"><span data-stu-id="bae16-125">Determine which fields were defined but not created, and then go back and create them.</span></span>