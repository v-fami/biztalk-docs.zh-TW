---
title: 單一登入： 事件 10706 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d73db77e-5bb6-431c-a8ca-5682d7ab3d6a
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e9e56600b86856af6a9cdb14fd2a902b047e84b5
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37022452"
---
# <a name="single-sign-on-event-10706"></a><span data-ttu-id="5aa24-102">單一登入： 事件 10706</span><span class="sxs-lookup"><span data-stu-id="5aa24-102">Single Sign-On: Event 10706</span></span>
## <a name="details"></a><span data-ttu-id="5aa24-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="5aa24-103">Details</span></span>  

|                 |                                                                                                                           |
|-----------------|---------------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="5aa24-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="5aa24-104">Product Name</span></span>   |                                                 <span data-ttu-id="5aa24-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="5aa24-105">Enterprise Single Sign-On</span></span>                                                 |
| <span data-ttu-id="5aa24-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="5aa24-106">Product Version</span></span> |                                [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                 |
|    <span data-ttu-id="5aa24-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="5aa24-107">Event ID</span></span>     |                                                           <span data-ttu-id="5aa24-108">10706</span><span class="sxs-lookup"><span data-stu-id="5aa24-108">10706</span></span>                                                           |
|  <span data-ttu-id="5aa24-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="5aa24-109">Event Source</span></span>   |                                                          <span data-ttu-id="5aa24-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="5aa24-110">ENTSSO</span></span>                                                           |
|    <span data-ttu-id="5aa24-111">元件</span><span class="sxs-lookup"><span data-stu-id="5aa24-111">Component</span></span>    |                                                            <span data-ttu-id="5aa24-112">N\A</span><span class="sxs-lookup"><span data-stu-id="5aa24-112">N\A</span></span>                                                            |
|  <span data-ttu-id="5aa24-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="5aa24-113">Symbolic Name</span></span>  |                                                <span data-ttu-id="5aa24-114">SSO_WARN_PS_NO_GLOBAL_SYNC</span><span class="sxs-lookup"><span data-stu-id="5aa24-114">SSO_WARN_PS_NO_GLOBAL_SYNC</span></span>                                                 |
|  <span data-ttu-id="5aa24-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="5aa24-115">Message Text</span></span>   | <span data-ttu-id="5aa24-116">群組配接器需要全域旗標允許密碼同步處理。</span><span class="sxs-lookup"><span data-stu-id="5aa24-116">Group adapters require password sync to be allowed by the global flags.</span></span> <span data-ttu-id="5aa24-117">檢查全域旗標。%r</span><span class="sxs-lookup"><span data-stu-id="5aa24-117">Check the global flags.%r</span></span><br /><br /> <span data-ttu-id="5aa24-118">配接器： %1</span><span class="sxs-lookup"><span data-stu-id="5aa24-118">Adapter: %1</span></span> |

## <a name="explanation"></a><span data-ttu-id="5aa24-119">說明</span><span class="sxs-lookup"><span data-stu-id="5aa24-119">Explanation</span></span>  
 <span data-ttu-id="5aa24-120">這個警告事件表示外部密碼同步配接器已要求密碼同步，且兩者皆非全域的旗標的設定。</span><span class="sxs-lookup"><span data-stu-id="5aa24-120">This Warning event indicates that password sync is requested by an external password sync adapter and neither of the global flags is set.</span></span> <span data-ttu-id="5aa24-121">有兩個旗標，可讓傳送密碼至外部系統的其中一個： SSO_FLAG_FULL_SYNC_FROM_WINDOWS_TO_EXTERNAL，另一個可接收外部系統 SSO_FLAG_PARTIAL_SYNC_FROM_EXTERNAL_TO_DB 的密碼。</span><span class="sxs-lookup"><span data-stu-id="5aa24-121">There are two flags, one that allows sending of password to external system: SSO_FLAG_FULL_SYNC_FROM_WINDOWS_TO_EXTERNAL and another that allows receiving of passwords from external systems SSO_FLAG_PARTIAL_SYNC_FROM_EXTERNAL_TO_DB.</span></span>  

## <a name="user-action"></a><span data-ttu-id="5aa24-122">使用者動作</span><span class="sxs-lookup"><span data-stu-id="5aa24-122">User Action</span></span>  
 <span data-ttu-id="5aa24-123">若要解決這個警告，執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="5aa24-123">To resolve this warning, do the following:</span></span>  

-   <span data-ttu-id="5aa24-124">使用 SSO 管理 MMC 嵌入式管理單元，(系統&#124;屬性&#124;選項) 或命令列工具`ssomanage –enable winsync/extsync`若要啟用全域旗標。</span><span class="sxs-lookup"><span data-stu-id="5aa24-124">Use the SSO Admin MMC Snap-In, (System &#124; Properties &#124; Options) or command line tool  `ssomanage –enable winsync/extsync` to enable the global flags.</span></span>  

## <a name="more-info"></a><span data-ttu-id="5aa24-125">其他資訊</span><span class="sxs-lookup"><span data-stu-id="5aa24-125">More info</span></span>

- <span data-ttu-id="5aa24-126">**企業單一登入旗標** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="5aa24-126">**Enterprise Single Sign-On Flags** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span>

- [<span data-ttu-id="5aa24-127">如何管理密碼同步處理</span><span class="sxs-lookup"><span data-stu-id="5aa24-127">How to Administer Password Synchronization</span></span>](../core/how-to-administer-password-synchronization.md)
