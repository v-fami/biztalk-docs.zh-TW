---
title: 單一登入： 事件 10658 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c5bee12d-502b-4fee-bc84-25807eb0e48e
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dd6ea4cb33e6df4fe8a59fc1041861bdb530aaa4
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36982247"
---
# <a name="single-sign-on-event-10658"></a><span data-ttu-id="6edab-102">單一登入： 事件 10658</span><span class="sxs-lookup"><span data-stu-id="6edab-102">Single Sign-On: Event 10658</span></span>
## <a name="details"></a><span data-ttu-id="6edab-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="6edab-103">Details</span></span>  

|                 |                                                                                   |
|-----------------|-----------------------------------------------------------------------------------|
|  <span data-ttu-id="6edab-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="6edab-104">Product Name</span></span>   |                             <span data-ttu-id="6edab-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="6edab-105">Enterprise Single Sign-On</span></span>                             |
| <span data-ttu-id="6edab-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="6edab-106">Product Version</span></span> |            [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]             |
|    <span data-ttu-id="6edab-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="6edab-107">Event ID</span></span>     |                                       <span data-ttu-id="6edab-108">10658</span><span class="sxs-lookup"><span data-stu-id="6edab-108">10658</span></span>                                       |
|  <span data-ttu-id="6edab-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="6edab-109">Event Source</span></span>   |                                      <span data-ttu-id="6edab-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="6edab-110">ENTSSO</span></span>                                       |
|    <span data-ttu-id="6edab-111">元件</span><span class="sxs-lookup"><span data-stu-id="6edab-111">Component</span></span>    |                                        <span data-ttu-id="6edab-112">N\A</span><span class="sxs-lookup"><span data-stu-id="6edab-112">N\A</span></span>                                        |
|  <span data-ttu-id="6edab-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="6edab-113">Symbolic Name</span></span>  |                   <span data-ttu-id="6edab-114">SSO_ERROR_PASSWORD_SYNC_ADAPTERS_START_FAILED</span><span class="sxs-lookup"><span data-stu-id="6edab-114">SSO_ERROR_PASSWORD_SYNC_ADAPTERS_START_FAILED</span></span>                   |
|  <span data-ttu-id="6edab-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="6edab-115">Message Text</span></span>   | <span data-ttu-id="6edab-116">外部配接器的密碼同步無法啟動。%r</span><span class="sxs-lookup"><span data-stu-id="6edab-116">Password sync for external adapters failed to start.%r</span></span><br /><br /> <span data-ttu-id="6edab-117">錯誤碼： %1</span><span class="sxs-lookup"><span data-stu-id="6edab-117">Error Code: %1</span></span> |

## <a name="explanation"></a><span data-ttu-id="6edab-118">說明</span><span class="sxs-lookup"><span data-stu-id="6edab-118">Explanation</span></span>  
 <span data-ttu-id="6edab-119">這個錯誤事件表示外部配接器的密碼同步無法啟動。</span><span class="sxs-lookup"><span data-stu-id="6edab-119">This Error event indicates that password sync for external adapters failed to start.</span></span>  

## <a name="user-action"></a><span data-ttu-id="6edab-120">使用者動作</span><span class="sxs-lookup"><span data-stu-id="6edab-120">User Action</span></span>  
 <span data-ttu-id="6edab-121">若要解決這個錯誤，請執行下列一個或多個動作：</span><span class="sxs-lookup"><span data-stu-id="6edab-121">To resolve this error, do one or more of the following:</span></span>  

-   <span data-ttu-id="6edab-122">檢查應用程式和系統事件記錄檔相關聯的事件。</span><span class="sxs-lookup"><span data-stu-id="6edab-122">Check the application and system event logs for associated events.</span></span>  

-   <span data-ttu-id="6edab-123">確認配接器組態屬性。</span><span class="sxs-lookup"><span data-stu-id="6edab-123">Verify adapter configuration properties.</span></span>  

## <a name="more-info"></a><span data-ttu-id="6edab-124">其他資訊</span><span class="sxs-lookup"><span data-stu-id="6edab-124">More info</span></span>  

- [<span data-ttu-id="6edab-125">如何管理密碼同步處理</span><span class="sxs-lookup"><span data-stu-id="6edab-125">How to Administer Password Synchronization</span></span>](../core/how-to-administer-password-synchronization.md)  

- <span data-ttu-id="6edab-126">**企業單一登入 UI 說明** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="6edab-126">**Enterprise Single Sign-On UI Help** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span>
