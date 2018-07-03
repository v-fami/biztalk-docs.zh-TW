---
title: 單一登入： 事件 10561 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 770e6fc1-0854-4555-8f2a-5f199e3aaca7
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 053b17fcb940383d58110378710aeb6bc8d3fbe6
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36992491"
---
# <a name="single-sign-on-event-10561"></a><span data-ttu-id="8a4d6-102">單一登入： 事件 10561</span><span class="sxs-lookup"><span data-stu-id="8a4d6-102">Single Sign-On: Event 10561</span></span>
## <a name="details"></a><span data-ttu-id="8a4d6-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="8a4d6-103">Details</span></span>  
  
|                 |                                                                                                                                                                                                                                 |
|-----------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="8a4d6-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="8a4d6-104">Product Name</span></span>   |                                                                                                    <span data-ttu-id="8a4d6-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="8a4d6-105">Enterprise Single Sign-On</span></span>                                                                                                    |
| <span data-ttu-id="8a4d6-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="8a4d6-106">Product Version</span></span> |                                                                                   [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                                    |
|    <span data-ttu-id="8a4d6-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="8a4d6-107">Event ID</span></span>     |                                                                                                              <span data-ttu-id="8a4d6-108">10561</span><span class="sxs-lookup"><span data-stu-id="8a4d6-108">10561</span></span>                                                                                                              |
|  <span data-ttu-id="8a4d6-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="8a4d6-109">Event Source</span></span>   |                                                                                                             <span data-ttu-id="8a4d6-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="8a4d6-110">ENTSSO</span></span>                                                                                                              |
|    <span data-ttu-id="8a4d6-111">元件</span><span class="sxs-lookup"><span data-stu-id="8a4d6-111">Component</span></span>    |                                                                                                               <span data-ttu-id="8a4d6-112">不適用</span><span class="sxs-lookup"><span data-stu-id="8a4d6-112">N/A</span></span>                                                                                                               |
|  <span data-ttu-id="8a4d6-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="8a4d6-113">Symbolic Name</span></span>  |                                                                                                  <span data-ttu-id="8a4d6-114">SSO_ERROR_BACKUP_FAILED_MEDIA</span><span class="sxs-lookup"><span data-stu-id="8a4d6-114">SSO_ERROR_BACKUP_FAILED_MEDIA</span></span>                                                                                                  |
|  <span data-ttu-id="8a4d6-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="8a4d6-115">Message Text</span></span>   | <span data-ttu-id="8a4d6-116">所指定的主要祕密備份檔案必須在 NTFS 檔案系統或卸除式 media.%r</span><span class="sxs-lookup"><span data-stu-id="8a4d6-116">The file specified for backup of the master secrets must be on an NTFS file system or removable media.%r</span></span><br /><br /> <span data-ttu-id="8a4d6-117">檔案名稱: %1 %r</span><span class="sxs-lookup"><span data-stu-id="8a4d6-117">File Name: %1%r</span></span><br /><br /> <span data-ttu-id="8a4d6-118">用戶端使用者: %2 %r</span><span class="sxs-lookup"><span data-stu-id="8a4d6-118">Client User: %2%r</span></span><br /><br /> <span data-ttu-id="8a4d6-119">用戶端電腦: %3 %r</span><span class="sxs-lookup"><span data-stu-id="8a4d6-119">Client Computer: %3%r</span></span><br /><br /> <span data-ttu-id="8a4d6-120">錯誤碼： %4</span><span class="sxs-lookup"><span data-stu-id="8a4d6-120">Error Code: %4</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="8a4d6-121">說明</span><span class="sxs-lookup"><span data-stu-id="8a4d6-121">Explanation</span></span>  
 <span data-ttu-id="8a4d6-122">備份已嘗試使用不正確的媒體，例如 FAT 檔案。</span><span class="sxs-lookup"><span data-stu-id="8a4d6-122">A backup was attempted using an invalid media, such as a FAT file.</span></span> <span data-ttu-id="8a4d6-123">所指定的主要祕密備份檔案必須在 NTFS 檔案系統或卸除式媒體上。</span><span class="sxs-lookup"><span data-stu-id="8a4d6-123">The file specified for backup of the master secrets must be on an NTFS file system or removable media.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="8a4d6-124">使用者動作</span><span class="sxs-lookup"><span data-stu-id="8a4d6-124">User Action</span></span>  
 <span data-ttu-id="8a4d6-125">檢查媒體格式，並確定它是 NTFS 或卸除式。</span><span class="sxs-lookup"><span data-stu-id="8a4d6-125">Check the media format and make sure it is NTFS or removable.</span></span>