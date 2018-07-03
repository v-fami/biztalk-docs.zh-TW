---
title: 單一登入： 事件 10708 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 63675191-41cb-43fc-9355-e4ddc3f354c5
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4b052e3545aa67b27bc94de579faedde782c0dec
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37003087"
---
# <a name="single-sign-on-event-10708"></a><span data-ttu-id="0d6ce-102">單一登入： 事件 10708</span><span class="sxs-lookup"><span data-stu-id="0d6ce-102">Single Sign-On: Event 10708</span></span>
## <a name="details"></a><span data-ttu-id="0d6ce-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="0d6ce-103">Details</span></span>  

|                 |                                                                                                                                |
|-----------------|--------------------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="0d6ce-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="0d6ce-104">Product Name</span></span>   |                                                   <span data-ttu-id="0d6ce-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="0d6ce-105">Enterprise Single Sign-On</span></span>                                                    |
| <span data-ttu-id="0d6ce-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="0d6ce-106">Product Version</span></span> |                                   [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                   |
|    <span data-ttu-id="0d6ce-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="0d6ce-107">Event ID</span></span>     |                                                             <span data-ttu-id="0d6ce-108">10708</span><span class="sxs-lookup"><span data-stu-id="0d6ce-108">10708</span></span>                                                              |
|  <span data-ttu-id="0d6ce-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="0d6ce-109">Event Source</span></span>   |                                                             <span data-ttu-id="0d6ce-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="0d6ce-110">ENTSSO</span></span>                                                             |
|    <span data-ttu-id="0d6ce-111">元件</span><span class="sxs-lookup"><span data-stu-id="0d6ce-111">Component</span></span>    |                                                              <span data-ttu-id="0d6ce-112">N\A</span><span class="sxs-lookup"><span data-stu-id="0d6ce-112">N\A</span></span>                                                               |
|  <span data-ttu-id="0d6ce-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="0d6ce-113">Symbolic Name</span></span>  |                                                    <span data-ttu-id="0d6ce-114">SSO_WARN_PS_NO_WIN_SYNC</span><span class="sxs-lookup"><span data-stu-id="0d6ce-114">SSO_WARN_PS_NO_WIN_SYNC</span></span>                                                     |
|  <span data-ttu-id="0d6ce-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="0d6ce-115">Message Text</span></span>   | <span data-ttu-id="0d6ce-116">不允許從 Windows 進行密碼同步。</span><span class="sxs-lookup"><span data-stu-id="0d6ce-116">Password sync from Windows is not allowed.</span></span> <span data-ttu-id="0d6ce-117">檢查全域旗標。%r</span><span class="sxs-lookup"><span data-stu-id="0d6ce-117">Check the global flags.%r</span></span><br /><br /> <span data-ttu-id="0d6ce-118">追蹤識別碼: %1 %r</span><span class="sxs-lookup"><span data-stu-id="0d6ce-118">Tracking ID: %1%r</span></span><br /><br /> <span data-ttu-id="0d6ce-119">用戶端使用者： %2</span><span class="sxs-lookup"><span data-stu-id="0d6ce-119">Client User: %2</span></span> |

## <a name="explanation"></a><span data-ttu-id="0d6ce-120">說明</span><span class="sxs-lookup"><span data-stu-id="0d6ce-120">Explanation</span></span>  
 <span data-ttu-id="0d6ce-121">這個警告事件表示 Windows 已要求密碼同步，但是未設定任何全域旗標。</span><span class="sxs-lookup"><span data-stu-id="0d6ce-121">This Warning event indicates that password sync is requested by Windows and neither of the global flags is set.</span></span> <span data-ttu-id="0d6ce-122">有兩個旗標，可讓傳送密碼至外部系統的其中一個： SSO_FLAG_FULL_SYNC_FROM_WINDOWS_TO_EXTERNAL，另一個可接收外部系統 SSO_FLAG_PARTIAL_SYNC_FROM_EXTERNAL_TO_DB 的密碼。</span><span class="sxs-lookup"><span data-stu-id="0d6ce-122">There are two flags, one that allows sending of password to external system: SSO_FLAG_FULL_SYNC_FROM_WINDOWS_TO_EXTERNAL and another that allows receiving of passwords from external systems SSO_FLAG_PARTIAL_SYNC_FROM_EXTERNAL_TO_DB.</span></span>  

## <a name="user-action"></a><span data-ttu-id="0d6ce-123">使用者動作</span><span class="sxs-lookup"><span data-stu-id="0d6ce-123">User Action</span></span>  
 <span data-ttu-id="0d6ce-124">若要解決這個警告，執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="0d6ce-124">To resolve this warning, do the following:</span></span>  

-   <span data-ttu-id="0d6ce-125">使用 SSO 管理 MMC 嵌入式管理單元，(系統&#124;屬性&#124;選項) 或命令列工具`ssomanage –enable winsync/extsync`若要啟用全域旗標。</span><span class="sxs-lookup"><span data-stu-id="0d6ce-125">Use the SSO Admin MMC Snap-In, (System &#124; Properties &#124; Options) or command line tool  `ssomanage –enable winsync/extsync` to enable the global flags.</span></span>  

## <a name="more-info"></a><span data-ttu-id="0d6ce-126">其他資訊</span><span class="sxs-lookup"><span data-stu-id="0d6ce-126">More info</span></span>

- <span data-ttu-id="0d6ce-127">**企業單一登入旗標** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="0d6ce-127">**Enterprise Single Sign-On Flags** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span>

- [<span data-ttu-id="0d6ce-128">如何管理密碼同步處理</span><span class="sxs-lookup"><span data-stu-id="0d6ce-128">How to Administer Password Synchronization</span></span>](../core/how-to-administer-password-synchronization.md)
