---
title: 疑難排解 BizTalk Server 權限 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e47bd1fc-2edf-4525-97dd-4bd9d3e2d6ff
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7c4187d666cb0f93229a0cf4117ca24b92d479c9
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36995991"
---
# <a name="troubleshooting-biztalk-server-permissions"></a><span data-ttu-id="f18d1-102">BizTalk Server 權限疑難排解</span><span class="sxs-lookup"><span data-stu-id="f18d1-102">Troubleshooting BizTalk Server Permissions</span></span>
<span data-ttu-id="f18d1-103">BizTalk Server 中的權限問題通常會分為下列類別：</span><span class="sxs-lookup"><span data-stu-id="f18d1-103">Permissions problems in BizTalk Server typically fall into one of the following categories:</span></span>  
  
- <span data-ttu-id="f18d1-104">SQL Server 權限</span><span class="sxs-lookup"><span data-stu-id="f18d1-104">SQL Server permissions</span></span>  
  
- <span data-ttu-id="f18d1-105">BizTalk Server 多伺服器安裝上的 Active Directory 權限</span><span class="sxs-lookup"><span data-stu-id="f18d1-105">Active Directory permissions on multiserver installations of BizTalk Server</span></span>  
  
- <span data-ttu-id="f18d1-106">Web 服務權限</span><span class="sxs-lookup"><span data-stu-id="f18d1-106">Web services permissions</span></span>  
  
- <span data-ttu-id="f18d1-107">IIS 權限</span><span class="sxs-lookup"><span data-stu-id="f18d1-107">IIS permissions</span></span>  
  
  <span data-ttu-id="f18d1-108">本主題包含一些一般指導方針，可用來避免權限問題，另外也包含用於特定案例的疑難排解步驟。</span><span class="sxs-lookup"><span data-stu-id="f18d1-108">This topic provides some general guidelines for avoiding permissions problems and troubleshooting steps for specific scenarios.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f18d1-109">本節內容</span><span class="sxs-lookup"><span data-stu-id="f18d1-109">In This Section</span></span>  
  
-   [<span data-ttu-id="f18d1-110">解決 SQL Server 權限問題的指導方針</span><span class="sxs-lookup"><span data-stu-id="f18d1-110">Guidelines for Resolving SQL Server Permissions Problems</span></span>](../core/guidelines-for-resolving-sql-server-permissions-problems.md)  
  
-   [<span data-ttu-id="f18d1-111">在 BizTalk 多伺服器安裝上實作 Active Directory 權限的指導方針</span><span class="sxs-lookup"><span data-stu-id="f18d1-111">Guidelines for Implementing Active Directory Permissions on Multi Server BizTalk Installations</span></span>](../core/implement-active-directory-permissions-on-multi-server-biztalk-installations.md)  
  
-   [<span data-ttu-id="f18d1-112">解決 Web 服務權限問題的指導方針</span><span class="sxs-lookup"><span data-stu-id="f18d1-112">Guidelines for Resolving Web Services Permissions Problems</span></span>](../core/guidelines-for-resolving-web-services-permissions-problems.md)  
  
-   [<span data-ttu-id="f18d1-113">解決 IIS 權限問題的指導方針</span><span class="sxs-lookup"><span data-stu-id="f18d1-113">Guidelines for Resolving IIS Permissions Problems</span></span>](../core/guidelines-for-resolving-iis-permissions-problems.md)