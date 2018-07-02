---
title: 單一登入： 事件 10605 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4c9812b4-43bc-43c4-be8f-6f57c432bda6
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c578462759d2eeb69767d21191e028ef9e8ce1e5
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36972511"
---
# <a name="single-sign-on-event-10605"></a><span data-ttu-id="d615a-102">單一登入： 事件 10605</span><span class="sxs-lookup"><span data-stu-id="d615a-102">Single Sign-On: Event 10605</span></span>
## <a name="details"></a><span data-ttu-id="d615a-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="d615a-103">Details</span></span>  
  
|                 |                                                                                                                                                                       |
|-----------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="d615a-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="d615a-104">Product Name</span></span>   |                                                                       <span data-ttu-id="d615a-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="d615a-105">Enterprise Single Sign-On</span></span>                                                                       |
| <span data-ttu-id="d615a-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="d615a-106">Product Version</span></span> |                                                      [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                       |
|    <span data-ttu-id="d615a-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="d615a-107">Event ID</span></span>     |                                                                                 <span data-ttu-id="d615a-108">10605</span><span class="sxs-lookup"><span data-stu-id="d615a-108">10605</span></span>                                                                                 |
|  <span data-ttu-id="d615a-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="d615a-109">Event Source</span></span>   |                                                                                <span data-ttu-id="d615a-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="d615a-110">ENTSSO</span></span>                                                                                 |
|    <span data-ttu-id="d615a-111">元件</span><span class="sxs-lookup"><span data-stu-id="d615a-111">Component</span></span>    |                                                                                  <span data-ttu-id="d615a-112">不適用</span><span class="sxs-lookup"><span data-stu-id="d615a-112">N/A</span></span>                                                                                  |
|  <span data-ttu-id="d615a-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="d615a-113">Symbolic Name</span></span>  |                                                                         <span data-ttu-id="d615a-114">SSO_ERROR_DTC_IMPORT</span><span class="sxs-lookup"><span data-stu-id="d615a-114">SSO_ERROR_DTC_IMPORT</span></span>                                                                          |
|  <span data-ttu-id="d615a-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="d615a-115">Message Text</span></span>   | <span data-ttu-id="d615a-116">無法匯入 DTC 交易。</span><span class="sxs-lookup"><span data-stu-id="d615a-116">Could not import a DTC transaction.</span></span> <span data-ttu-id="d615a-117">請檢查 MSDTC 已正確設定為支援遠端作業。</span><span class="sxs-lookup"><span data-stu-id="d615a-117">Please check that MSDTC is configured correctly for remote operation.</span></span> <span data-ttu-id="d615a-118">請參閱 details.%r 文件</span><span class="sxs-lookup"><span data-stu-id="d615a-118">See documentation for details.%r</span></span><br /><br /> <span data-ttu-id="d615a-119">錯誤碼： %1</span><span class="sxs-lookup"><span data-stu-id="d615a-119">Error Code: %1</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="d615a-120">說明</span><span class="sxs-lookup"><span data-stu-id="d615a-120">Explanation</span></span>  
 <span data-ttu-id="d615a-121">Microsoft 分散式交易協調器 (MSDTC) 發生問題。</span><span class="sxs-lookup"><span data-stu-id="d615a-121">There is a problem with the Microsoft Distributed Transaction Coordinator (MSDTC).</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="d615a-122">使用者動作</span><span class="sxs-lookup"><span data-stu-id="d615a-122">User Action</span></span>  
 <span data-ttu-id="d615a-123">如需 MSDTC 問題的說明，請參閱 < [MSDTC 問題疑難排解](../core/troubleshooting-problems-with-msdtc.md)。</span><span class="sxs-lookup"><span data-stu-id="d615a-123">For help on MSDTC issues, see [Troubleshooting Problems with MSDTC](../core/troubleshooting-problems-with-msdtc.md).</span></span>