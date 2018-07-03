---
title: 單一登入： 事件 10564 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e523c97a-608e-4bf4-8747-cfa0cce10acf
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8be4ea87757a1fa0cb5d8ebd2e344ce521dbf740
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36997143"
---
# <a name="single-sign-on-event-10564"></a><span data-ttu-id="c8326-102">單一登入： 事件 10564</span><span class="sxs-lookup"><span data-stu-id="c8326-102">Single Sign-On: Event 10564</span></span>
## <a name="details"></a><span data-ttu-id="c8326-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="c8326-103">Details</span></span>  
  
|                 |                                                            |
|-----------------|------------------------------------------------------------|
|  <span data-ttu-id="c8326-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="c8326-104">Product Name</span></span>   |                 <span data-ttu-id="c8326-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="c8326-105">Enterprise Single Sign-On</span></span>                  |
| <span data-ttu-id="c8326-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="c8326-106">Product Version</span></span> | [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)] |
|    <span data-ttu-id="c8326-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="c8326-107">Event ID</span></span>     |                           <span data-ttu-id="c8326-108">10564</span><span class="sxs-lookup"><span data-stu-id="c8326-108">10564</span></span>                            |
|  <span data-ttu-id="c8326-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="c8326-109">Event Source</span></span>   |                           <span data-ttu-id="c8326-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="c8326-110">ENTSSO</span></span>                           |
|    <span data-ttu-id="c8326-111">元件</span><span class="sxs-lookup"><span data-stu-id="c8326-111">Component</span></span>    |                            <span data-ttu-id="c8326-112">不適用</span><span class="sxs-lookup"><span data-stu-id="c8326-112">N/A</span></span>                             |
|  <span data-ttu-id="c8326-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="c8326-113">Symbolic Name</span></span>  |           <span data-ttu-id="c8326-114">SSO_ERROR_BACKUP_FILE_INCORRECT_FORMAT</span><span class="sxs-lookup"><span data-stu-id="c8326-114">SSO_ERROR_BACKUP_FILE_INCORRECT_FORMAT</span></span>           |
|  <span data-ttu-id="c8326-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="c8326-115">Message Text</span></span>   |     <span data-ttu-id="c8326-116">備份檔案並沒有正確的格式。</span><span class="sxs-lookup"><span data-stu-id="c8326-116">The backup file does not have the correct format.</span></span>      |
  
## <a name="explanation"></a><span data-ttu-id="c8326-117">說明</span><span class="sxs-lookup"><span data-stu-id="c8326-117">Explanation</span></span>  
 <span data-ttu-id="c8326-118">備份檔案並沒有正確的格式。</span><span class="sxs-lookup"><span data-stu-id="c8326-118">The backup file does not have the correct format.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="c8326-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="c8326-119">User Action</span></span>  
 <span data-ttu-id="c8326-120">查看您擁有正確的檔案和位置。</span><span class="sxs-lookup"><span data-stu-id="c8326-120">Check that you have the correct file and location.</span></span> <span data-ttu-id="c8326-121">您也應該確認該資料夾中沒有任何其他檔案。BAK 延伸模組，做為 ENTSSO 系統可能會混淆它們實際的備份檔案。</span><span class="sxs-lookup"><span data-stu-id="c8326-121">You should also confirm that there are no other files in that folder with the .BAK extension, as the ENTSSO system may confuse them with the actual backup file.</span></span>