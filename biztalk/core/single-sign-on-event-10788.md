---
title: 單一登入： 事件 10788 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: deeb8859-6b2e-452d-a7e5-0cb10de68bd2
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b1bf8d17abd7fd5652821b998cae34915e7777f2
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37019659"
---
# <a name="single-sign-on-event-10788"></a><span data-ttu-id="e5210-102">單一登入： 事件 10788</span><span class="sxs-lookup"><span data-stu-id="e5210-102">Single Sign-On: Event 10788</span></span>
## <a name="details"></a><span data-ttu-id="e5210-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="e5210-103">Details</span></span>  
  
|                 |                                                                                                                                          |
|-----------------|------------------------------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="e5210-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="e5210-104">Product Name</span></span>   |                                                        <span data-ttu-id="e5210-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="e5210-105">Enterprise Single Sign-On</span></span>                                                         |
| <span data-ttu-id="e5210-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="e5210-106">Product Version</span></span> |                                        [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                        |
|    <span data-ttu-id="e5210-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="e5210-107">Event ID</span></span>     |                                                                  <span data-ttu-id="e5210-108">10788</span><span class="sxs-lookup"><span data-stu-id="e5210-108">10788</span></span>                                                                   |
|  <span data-ttu-id="e5210-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="e5210-109">Event Source</span></span>   |                                                                  <span data-ttu-id="e5210-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="e5210-110">ENTSSO</span></span>                                                                  |
|    <span data-ttu-id="e5210-111">元件</span><span class="sxs-lookup"><span data-stu-id="e5210-111">Component</span></span>    |                                                                   <span data-ttu-id="e5210-112">不適用</span><span class="sxs-lookup"><span data-stu-id="e5210-112">N/A</span></span>                                                                    |
|  <span data-ttu-id="e5210-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="e5210-113">Symbolic Name</span></span>  |                                                       <span data-ttu-id="e5210-114">ENTSSO_E_DTC_IMPORT_FAILED1</span><span class="sxs-lookup"><span data-stu-id="e5210-114">ENTSSO_E_DTC_IMPORT_FAILED1</span></span>                                                        |
|  <span data-ttu-id="e5210-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="e5210-115">Message Text</span></span>   | <span data-ttu-id="e5210-116">無法匯入 DTC 交易。</span><span class="sxs-lookup"><span data-stu-id="e5210-116">Could not import a DTC transaction.</span></span> <span data-ttu-id="e5210-117">請檢查 MSDTC 已正確設定為支援遠端作業。</span><span class="sxs-lookup"><span data-stu-id="e5210-117">Please check that MSDTC is configured correctly for remote operation.</span></span> <span data-ttu-id="e5210-118">請參閱文件，如需詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="e5210-118">See documentation for details.</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="e5210-119">說明</span><span class="sxs-lookup"><span data-stu-id="e5210-119">Explanation</span></span>  
 <span data-ttu-id="e5210-120">無法匯入 DTC 交易。</span><span class="sxs-lookup"><span data-stu-id="e5210-120">Could not import a DTC transaction.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="e5210-121">使用者動作</span><span class="sxs-lookup"><span data-stu-id="e5210-121">User Action</span></span>  
 <span data-ttu-id="e5210-122">檢查 MSDTC 已正確設定為支援遠端作業，並參閱事件日誌以取得詳細資料指定的電腦上。</span><span class="sxs-lookup"><span data-stu-id="e5210-122">Check that MSDTC is configured correctly for remote operation, and see the event log on the specified computer for more details.</span></span>  
  
 <span data-ttu-id="e5210-123">如需 MSDTC 問題的說明，請參閱 < [MSDTC 問題疑難排解](../core/troubleshooting-problems-with-msdtc.md)。</span><span class="sxs-lookup"><span data-stu-id="e5210-123">For help on MSDTC issues, see [Troubleshooting Problems with MSDTC](../core/troubleshooting-problems-with-msdtc.md).</span></span>