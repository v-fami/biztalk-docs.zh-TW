---
title: "單一登入： 事件 10594 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1f4c6041-39a8-49bc-b39e-66cb6eb2efae
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 804b2616080ceee0b6a31f7623e19e05c11481f5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10594"></a><span data-ttu-id="ee89c-102">單一登入： 事件 10594</span><span class="sxs-lookup"><span data-stu-id="ee89c-102">Single Sign-On: Event 10594</span></span>
## <a name="details"></a><span data-ttu-id="ee89c-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="ee89c-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ee89c-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="ee89c-104">Product Name</span></span>|<span data-ttu-id="ee89c-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="ee89c-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="ee89c-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="ee89c-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="ee89c-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="ee89c-107">Event ID</span></span>|<span data-ttu-id="ee89c-108">10594</span><span class="sxs-lookup"><span data-stu-id="ee89c-108">10594</span></span>|  
|<span data-ttu-id="ee89c-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="ee89c-109">Event Source</span></span>|<span data-ttu-id="ee89c-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="ee89c-110">ENTSSO</span></span>|  
|<span data-ttu-id="ee89c-111">元件</span><span class="sxs-lookup"><span data-stu-id="ee89c-111">Component</span></span>|<span data-ttu-id="ee89c-112">不適用</span><span class="sxs-lookup"><span data-stu-id="ee89c-112">N/A</span></span>|  
|<span data-ttu-id="ee89c-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="ee89c-113">Symbolic Name</span></span>|<span data-ttu-id="ee89c-114">SSO_WARN_TICKET_VALIDATE_FAILED</span><span class="sxs-lookup"><span data-stu-id="ee89c-114">SSO_WARN_TICKET_VALIDATE_FAILED</span></span>|  
|<span data-ttu-id="ee89c-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="ee89c-115">Message Text</span></span>|<span data-ttu-id="ee89c-116">驗證票證失敗。</span><span class="sxs-lookup"><span data-stu-id="ee89c-116">Validation of the ticket failed.</span></span> <span data-ttu-id="ee89c-117">寄件者名稱必須符合票證 issuer.%r</span><span class="sxs-lookup"><span data-stu-id="ee89c-117">The sender name must match that of the ticket issuer.%r</span></span><br /><br /> <span data-ttu-id="ee89c-118">應用程式名稱: %1 %r</span><span class="sxs-lookup"><span data-stu-id="ee89c-118">Application Name: %1%r</span></span><br /><br /> <span data-ttu-id="ee89c-119">票證核發者: %2 %r</span><span class="sxs-lookup"><span data-stu-id="ee89c-119">Ticket Issued By: %2%r</span></span><br /><br /> <span data-ttu-id="ee89c-120">寄件者名稱： %3</span><span class="sxs-lookup"><span data-stu-id="ee89c-120">Sender Name: %3</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="ee89c-121">說明</span><span class="sxs-lookup"><span data-stu-id="ee89c-121">Explanation</span></span>  
 <span data-ttu-id="ee89c-122">要驗證票證的順序必須符合票證發出者和寄件者名稱中的欄位 （警告訊息）。</span><span class="sxs-lookup"><span data-stu-id="ee89c-122">In order for a ticket to be validated, the Ticket Issued By and Sender Name fields (in the warning message) must match.</span></span> <span data-ttu-id="ee89c-123">不過，訊息傳送到 BizTalk 不受信任的主控件時，如果寄件者名稱取得變更的 BizTalk 不受信任的主控件，名稱為，將不會驗證票證。</span><span class="sxs-lookup"><span data-stu-id="ee89c-123">If, however, the message is sent through a BizTalk untrusted host, the Sender Name gets changed to the name of the BizTalk untrusted host, and the ticket will not validate.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="ee89c-124">使用者動作</span><span class="sxs-lookup"><span data-stu-id="ee89c-124">User Action</span></span>  
 <span data-ttu-id="ee89c-125">如果您使用企業單一登入，請確定您的訊息僅透過受信任的 BizTalk 主控件流動。</span><span class="sxs-lookup"><span data-stu-id="ee89c-125">If you are using Enterprise Single Sign-On, ensure that your message is flowing only through BizTalk trusted hosts.</span></span> <span data-ttu-id="ee89c-126">這會降低訊息中的資料遭到竄改的風險。</span><span class="sxs-lookup"><span data-stu-id="ee89c-126">This will reduce the risk of tampering with the data in the message.</span></span>  
  
 <span data-ttu-id="ee89c-127">如果您完全了解的安全性影響您的案例，您可以關閉此應用程式的驗證。</span><span class="sxs-lookup"><span data-stu-id="ee89c-127">If you fully understand the security implications for your scenario, you can turn off validation for this application.</span></span> <span data-ttu-id="ee89c-128">請注意，驗證可以在系統或只針對此特定應用程式關閉的管理選項。</span><span class="sxs-lookup"><span data-stu-id="ee89c-128">Note that validation is an administration option which can be turned off for the system or just for this particular application.</span></span>