---
title: 單一登入： 事件 10808 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0b4efc1d-f163-4440-a78e-53065c6af36c
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 49d4e6ab0f6a9ea10ef28440f5b8399778fbc93b
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36971399"
---
# <a name="single-sign-on-event-10808"></a><span data-ttu-id="0cda3-102">單一登入： 事件 10808</span><span class="sxs-lookup"><span data-stu-id="0cda3-102">Single Sign-On: Event 10808</span></span>
## <a name="details"></a><span data-ttu-id="0cda3-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="0cda3-103">Details</span></span>  
  
|                 |                                                                  |
|-----------------|------------------------------------------------------------------|
|  <span data-ttu-id="0cda3-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="0cda3-104">Product Name</span></span>   |                    <span data-ttu-id="0cda3-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="0cda3-105">Enterprise Single Sign-On</span></span>                     |
| <span data-ttu-id="0cda3-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="0cda3-106">Product Version</span></span> |    [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]    |
|    <span data-ttu-id="0cda3-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="0cda3-107">Event ID</span></span>     |                              <span data-ttu-id="0cda3-108">10808</span><span class="sxs-lookup"><span data-stu-id="0cda3-108">10808</span></span>                               |
|  <span data-ttu-id="0cda3-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="0cda3-109">Event Source</span></span>   |                              <span data-ttu-id="0cda3-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="0cda3-110">ENTSSO</span></span>                              |
|    <span data-ttu-id="0cda3-111">元件</span><span class="sxs-lookup"><span data-stu-id="0cda3-111">Component</span></span>    |                               <span data-ttu-id="0cda3-112">不適用</span><span class="sxs-lookup"><span data-stu-id="0cda3-112">N/A</span></span>                                |
|  <span data-ttu-id="0cda3-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="0cda3-113">Symbolic Name</span></span>  |                <span data-ttu-id="0cda3-114">ENTSSO_E_HISSO_SYSTEM_NOT_ENABLED</span><span class="sxs-lookup"><span data-stu-id="0cda3-114">ENTSSO_E_HISSO_SYSTEM_NOT_ENABLED</span></span>                 |
|  <span data-ttu-id="0cda3-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="0cda3-115">Message Text</span></span>   | <span data-ttu-id="0cda3-116">SSO 系統不會啟用主控件初始化的單一登入。</span><span class="sxs-lookup"><span data-stu-id="0cda3-116">The SSO system is not enabled for Host Initiated Single Sign-On.</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="0cda3-117">說明</span><span class="sxs-lookup"><span data-stu-id="0cda3-117">Explanation</span></span>  
 <span data-ttu-id="0cda3-118">SSO 系統不會啟用主控件初始化的單一登入。</span><span class="sxs-lookup"><span data-stu-id="0cda3-118">The SSO system is not enabled for Host Initiated Single Sign-On.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="0cda3-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="0cda3-119">User Action</span></span>  
 <span data-ttu-id="0cda3-120">使用系統管理工具來設定主應用程式起始單一登入。</span><span class="sxs-lookup"><span data-stu-id="0cda3-120">Use the administrative tools to configure Host Initiated Single Sign-On.</span></span> <span data-ttu-id="0cda3-121">這將會設定</span><span class="sxs-lookup"><span data-stu-id="0cda3-121">This will set the</span></span>  
  
 <span data-ttu-id="0cda3-122">全域資訊 SSO_FLAG_SSO_EXTERNAL_TO_WINDOWS 旗標。</span><span class="sxs-lookup"><span data-stu-id="0cda3-122">SSO_FLAG_SSO_EXTERNAL_TO_WINDOWS flag on the global information.</span></span>