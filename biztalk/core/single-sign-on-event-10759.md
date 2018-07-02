---
title: 單一登入： 事件 10759 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5347f3d6-d31a-4c00-a64c-c0b0f680de88
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 177b5d1383a583ddc33a67a7290bff98b1d13364
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36967583"
---
# <a name="single-sign-on-event-10759"></a><span data-ttu-id="206a1-102">單一登入： 事件 10759</span><span class="sxs-lookup"><span data-stu-id="206a1-102">Single Sign-On: Event 10759</span></span>
## <a name="details"></a><span data-ttu-id="206a1-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="206a1-103">Details</span></span>  
  
|                 |                                                                                                                   |
|-----------------|-------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="206a1-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="206a1-104">Product Name</span></span>   |                                             <span data-ttu-id="206a1-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="206a1-105">Enterprise Single Sign-On</span></span>                                             |
| <span data-ttu-id="206a1-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="206a1-106">Product Version</span></span> |                            [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                             |
|    <span data-ttu-id="206a1-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="206a1-107">Event ID</span></span>     |                                                       <span data-ttu-id="206a1-108">10759</span><span class="sxs-lookup"><span data-stu-id="206a1-108">10759</span></span>                                                       |
|  <span data-ttu-id="206a1-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="206a1-109">Event Source</span></span>   |                                                      <span data-ttu-id="206a1-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="206a1-110">ENTSSO</span></span>                                                       |
|    <span data-ttu-id="206a1-111">元件</span><span class="sxs-lookup"><span data-stu-id="206a1-111">Component</span></span>    |                                                        <span data-ttu-id="206a1-112">不適用</span><span class="sxs-lookup"><span data-stu-id="206a1-112">N/A</span></span>                                                        |
|  <span data-ttu-id="206a1-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="206a1-113">Symbolic Name</span></span>  |                                       <span data-ttu-id="206a1-114">ENTSSO_E_BACKUP_RESTORE_FAILED_MEDIA</span><span class="sxs-lookup"><span data-stu-id="206a1-114">ENTSSO_E_BACKUP_RESTORE_FAILED_MEDIA</span></span>                                        |
|  <span data-ttu-id="206a1-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="206a1-115">Message Text</span></span>   | <span data-ttu-id="206a1-116">針對主要密碼備份或還原指定的檔案必須位於 NTFS 檔案系統或卸除式媒體。</span><span class="sxs-lookup"><span data-stu-id="206a1-116">The file specified for backup or restore of the master secrets must be on an NTFS file system or removable media.</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="206a1-117">說明</span><span class="sxs-lookup"><span data-stu-id="206a1-117">Explanation</span></span>  
 <span data-ttu-id="206a1-118">只有 NTFS 檔案系統或卸除式媒體可以進行保護。</span><span class="sxs-lookup"><span data-stu-id="206a1-118">Only NTFS file systems or removable media can be secured.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="206a1-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="206a1-119">User Action</span></span>  
 <span data-ttu-id="206a1-120">切換至 NTFS 檔案系統來備份主要密碼的卸除式媒體。</span><span class="sxs-lookup"><span data-stu-id="206a1-120">Switch to either an NTFS file system of removable media to back up the master secret.</span></span>