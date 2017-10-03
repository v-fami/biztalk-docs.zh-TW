---
title: "Windows SharePoint Services 安全性 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security, Windows SharePoint Services
- Windows SharePoint Services, security
- security, BAS
- BAS, security
ms.assetid: ada6abd3-b867-49a6-8ee0-1466adc87dc5
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 184f5a237f796eac69de6c481e69a87a4a5358df
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="windows-sharepoint-services-security"></a><span data-ttu-id="e65a1-102">Windows SharePoint Services 安全性</span><span class="sxs-lookup"><span data-stu-id="e65a1-102">Windows SharePoint Services Security</span></span>
<span data-ttu-id="e65a1-103">Windows SharePoint Services 3.0 會使用 Windows SharePoint Services 網站群組來管理整個網站的安全性。</span><span class="sxs-lookup"><span data-stu-id="e65a1-103">Windows SharePoint Services 3.0 uses Windows SharePoint Services site groups to manage site-wide security.</span></span> <span data-ttu-id="e65a1-104">每個站台 群組具有對應的權限。</span><span class="sxs-lookup"><span data-stu-id="e65a1-104">Each site group possesses corresponding rights.</span></span> <span data-ttu-id="e65a1-105">有權限的使用者可以執行的動作，例如檢視、 編輯和刪除站台資源。</span><span class="sxs-lookup"><span data-stu-id="e65a1-105">Rights are actions that users can perform—such as view, edit, and delete site resources.</span></span> <span data-ttu-id="e65a1-106">資源包括站台清單、 文件庫和站台管理。</span><span class="sxs-lookup"><span data-stu-id="e65a1-106">Resources include site lists, document libraries, and site administration.</span></span> <span data-ttu-id="e65a1-107">在設定檔 Web 用戶端需要定義 Windows SharePoint Services 網站群組，並據以指派權限的每個資源，且該群組中建立每個角色可以存取。</span><span class="sxs-lookup"><span data-stu-id="e65a1-107">For each role created in the Profile Web Client you need to define a Windows SharePoint Service site group and assign rights accordingly to each resource to which that group has access.</span></span>  
  
 <span data-ttu-id="e65a1-108">如需 WSS 3.0 安全性的詳細資訊，請參閱 WSS 3.0 評估指南 》，網址[http://go.microsoft.com/fwlink/?LinkID=94370](http://go.microsoft.com/fwlink/?LinkID=94370)。</span><span class="sxs-lookup"><span data-stu-id="e65a1-108">For more information about WSS 3.0 security, see the WSS 3.0 evaluation guide at [http://go.microsoft.com/fwlink/?LinkID=94370](http://go.microsoft.com/fwlink/?LinkID=94370).</span></span>  
  
 <span data-ttu-id="e65a1-109">此部分包含：</span><span class="sxs-lookup"><span data-stu-id="e65a1-109">This section contains:</span></span>  
  
-   [<span data-ttu-id="e65a1-110">設定 A4SWIFT 使用者</span><span class="sxs-lookup"><span data-stu-id="e65a1-110">Configuring A4SWIFT Users</span></span>](../../adapters-and-accelerators/accelerator-swift/configuring-a4swift-users.md)  
  
-   [<span data-ttu-id="e65a1-111">設定 A4SWIFT 網站群組</span><span class="sxs-lookup"><span data-stu-id="e65a1-111">Configuring A4SWIFT Site Groups</span></span>](../../adapters-and-accelerators/accelerator-swift/configuring-a4swift-site-groups.md)  
  
-   [<span data-ttu-id="e65a1-112">指派權限</span><span class="sxs-lookup"><span data-stu-id="e65a1-112">Assigning Rights</span></span>](../../adapters-and-accelerators/accelerator-swift/assigning-rights.md)