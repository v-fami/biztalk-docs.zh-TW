---
title: 單一登入： 事件 10594 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1f4c6041-39a8-49bc-b39e-66cb6eb2efae
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ba733d9a919b2af09824242a48a2fa85af8ab481
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37004758"
---
# <a name="single-sign-on-event-10594"></a><span data-ttu-id="af443-102">單一登入： 事件 10594</span><span class="sxs-lookup"><span data-stu-id="af443-102">Single Sign-On: Event 10594</span></span>
## <a name="details"></a><span data-ttu-id="af443-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="af443-103">Details</span></span>  
  
|                 |                                                                                                                                                                                            |
|-----------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="af443-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="af443-104">Product Name</span></span>   |                                                                                 <span data-ttu-id="af443-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="af443-105">Enterprise Single Sign-On</span></span>                                                                                  |
| <span data-ttu-id="af443-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="af443-106">Product Version</span></span> |                                                                 [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                 |
|    <span data-ttu-id="af443-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="af443-107">Event ID</span></span>     |                                                                                           <span data-ttu-id="af443-108">10594</span><span class="sxs-lookup"><span data-stu-id="af443-108">10594</span></span>                                                                                            |
|  <span data-ttu-id="af443-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="af443-109">Event Source</span></span>   |                                                                                           <span data-ttu-id="af443-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="af443-110">ENTSSO</span></span>                                                                                           |
|    <span data-ttu-id="af443-111">元件</span><span class="sxs-lookup"><span data-stu-id="af443-111">Component</span></span>    |                                                                                            <span data-ttu-id="af443-112">不適用</span><span class="sxs-lookup"><span data-stu-id="af443-112">N/A</span></span>                                                                                             |
|  <span data-ttu-id="af443-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="af443-113">Symbolic Name</span></span>  |                                                                              <span data-ttu-id="af443-114">SSO_WARN_TICKET_VALIDATE_FAILED</span><span class="sxs-lookup"><span data-stu-id="af443-114">SSO_WARN_TICKET_VALIDATE_FAILED</span></span>                                                                               |
|  <span data-ttu-id="af443-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="af443-115">Message Text</span></span>   | <span data-ttu-id="af443-116">驗證票證失敗。</span><span class="sxs-lookup"><span data-stu-id="af443-116">Validation of the ticket failed.</span></span> <span data-ttu-id="af443-117">寄件者名稱必須符合票證 issuer.%r</span><span class="sxs-lookup"><span data-stu-id="af443-117">The sender name must match that of the ticket issuer.%r</span></span><br /><br /> <span data-ttu-id="af443-118">應用程式名稱: %1 %r</span><span class="sxs-lookup"><span data-stu-id="af443-118">Application Name: %1%r</span></span><br /><br /> <span data-ttu-id="af443-119">票證發出者: %2 %r</span><span class="sxs-lookup"><span data-stu-id="af443-119">Ticket Issued By: %2%r</span></span><br /><br /> <span data-ttu-id="af443-120">寄件者名稱： %3</span><span class="sxs-lookup"><span data-stu-id="af443-120">Sender Name: %3</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="af443-121">說明</span><span class="sxs-lookup"><span data-stu-id="af443-121">Explanation</span></span>  
 <span data-ttu-id="af443-122">為了讓驗證票證，必須符合票證核發者和寄件者名稱中的欄位 （警告訊息）。</span><span class="sxs-lookup"><span data-stu-id="af443-122">In order for a ticket to be validated, the Ticket Issued By and Sender Name fields (in the warning message) must match.</span></span> <span data-ttu-id="af443-123">不過，透過 BizTalk 不受信任主應用程式傳送訊息，寄件者名稱會變更名稱之 BizTalk 不受信任的主控件，則將不會驗證票證。</span><span class="sxs-lookup"><span data-stu-id="af443-123">If, however, the message is sent through a BizTalk untrusted host, the Sender Name gets changed to the name of the BizTalk untrusted host, and the ticket will not validate.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="af443-124">使用者動作</span><span class="sxs-lookup"><span data-stu-id="af443-124">User Action</span></span>  
 <span data-ttu-id="af443-125">如果您使用企業單一登入，請確定您的訊息會流經只能透過受信任的 BizTalk 主控件。</span><span class="sxs-lookup"><span data-stu-id="af443-125">If you are using Enterprise Single Sign-On, ensure that your message is flowing only through BizTalk trusted hosts.</span></span> <span data-ttu-id="af443-126">這會減少訊息中的資料遭竄改的風險。</span><span class="sxs-lookup"><span data-stu-id="af443-126">This will reduce the risk of tampering with the data in the message.</span></span>  
  
 <span data-ttu-id="af443-127">如果您完全了解的安全性影響您的案例，您可以關閉此應用程式的驗證。</span><span class="sxs-lookup"><span data-stu-id="af443-127">If you fully understand the security implications for your scenario, you can turn off validation for this application.</span></span> <span data-ttu-id="af443-128">請注意，驗證可以在系統或只是此特定應用程式關閉的管理選項。</span><span class="sxs-lookup"><span data-stu-id="af443-128">Note that validation is an administration option which can be turned off for the system or just for this particular application.</span></span>