---
title: 單一登入： 事件 10611 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4549ac01-b828-478f-aea0-862e14fac149
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7ca43eff86b20df7000c973f7c6ade472a8780de
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37023564"
---
# <a name="single-sign-on-event-10611"></a><span data-ttu-id="1ee5c-102">單一登入： 事件 10611</span><span class="sxs-lookup"><span data-stu-id="1ee5c-102">Single Sign-On: Event 10611</span></span>
## <a name="details"></a><span data-ttu-id="1ee5c-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="1ee5c-103">Details</span></span>  
  
|                 |                                                                                                                                                                                                                                           |
|-----------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="1ee5c-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="1ee5c-104">Product Name</span></span>   |                                                                                                         <span data-ttu-id="1ee5c-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="1ee5c-105">Enterprise Single Sign-On</span></span>                                                                                                         |
| <span data-ttu-id="1ee5c-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="1ee5c-106">Product Version</span></span> |                                                                                        [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                                         |
|    <span data-ttu-id="1ee5c-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="1ee5c-107">Event ID</span></span>     |                                                                                                                   <span data-ttu-id="1ee5c-108">10611</span><span class="sxs-lookup"><span data-stu-id="1ee5c-108">10611</span></span>                                                                                                                   |
|  <span data-ttu-id="1ee5c-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="1ee5c-109">Event Source</span></span>   |                                                                                                                  <span data-ttu-id="1ee5c-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="1ee5c-110">ENTSSO</span></span>                                                                                                                   |
|    <span data-ttu-id="1ee5c-111">元件</span><span class="sxs-lookup"><span data-stu-id="1ee5c-111">Component</span></span>    |                                                                                                                    <span data-ttu-id="1ee5c-112">不適用</span><span class="sxs-lookup"><span data-stu-id="1ee5c-112">N/A</span></span>                                                                                                                    |
|  <span data-ttu-id="1ee5c-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="1ee5c-113">Symbolic Name</span></span>  |                                                                                                     <span data-ttu-id="1ee5c-114">SSO_INFO_SERVICE_STARTING_NO_SSL</span><span class="sxs-lookup"><span data-stu-id="1ee5c-114">SSO_INFO_SERVICE_STARTING_NO_SSL</span></span>                                                                                                      |
|  <span data-ttu-id="1ee5c-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="1ee5c-115">Message Text</span></span>   | <span data-ttu-id="1ee5c-116">SSO 服務正在 starting.%r</span><span class="sxs-lookup"><span data-stu-id="1ee5c-116">The SSO service is starting.%r</span></span><br /><br /> <span data-ttu-id="1ee5c-117">電腦名稱: %1 %r</span><span class="sxs-lookup"><span data-stu-id="1ee5c-117">Computer Name: %1%r</span></span><br /><br /> <span data-ttu-id="1ee5c-118">SQL Server 名稱: %2 %r</span><span class="sxs-lookup"><span data-stu-id="1ee5c-118">SQL Server Name: %2%r</span></span><br /><br /> <span data-ttu-id="1ee5c-119">SSO 資料庫名稱: %3 %r</span><span class="sxs-lookup"><span data-stu-id="1ee5c-119">SSO Database Name: %3%r</span></span><br /><br /> <span data-ttu-id="1ee5c-120">未使用 SSL。</span><span class="sxs-lookup"><span data-stu-id="1ee5c-120">Not using SSL.</span></span> <span data-ttu-id="1ee5c-121">如何保護 SQL Server 連接，請參閱文件，如需詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="1ee5c-121">See documentation for details on how to secure the SQL Server connection.</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="1ee5c-122">說明</span><span class="sxs-lookup"><span data-stu-id="1ee5c-122">Explanation</span></span>  
 <span data-ttu-id="1ee5c-123">ENTSSO 服務正在啟動而不使用安全通訊端層 (SSL)。</span><span class="sxs-lookup"><span data-stu-id="1ee5c-123">The ENTSSO Service is starting without using Secure Sockets Layer (SSL).</span></span> <span data-ttu-id="1ee5c-124">建議您從 SSO 服務保護您的連線，to SQL。</span><span class="sxs-lookup"><span data-stu-id="1ee5c-124">It is recommended that you secure your connection from the SSO Service to SQL.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="1ee5c-125">使用者動作</span><span class="sxs-lookup"><span data-stu-id="1ee5c-125">User Action</span></span>  
 <span data-ttu-id="1ee5c-126">請參閱文件，網址[如何啟用 SSO 的 SSL](../core/how-to-enable-ssl-for-sso.md)</span><span class="sxs-lookup"><span data-stu-id="1ee5c-126">See the documentation at [How to Enable SSL for SSO](../core/how-to-enable-ssl-for-sso.md)</span></span>  
  
 <span data-ttu-id="1ee5c-127">執行個體時提供 SQL Server 登入。</span><span class="sxs-lookup"><span data-stu-id="1ee5c-127">.</span></span>