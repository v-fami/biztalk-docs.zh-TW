---
title: "SSO 伺服器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Master Secret server, tasks
- Master Secret server, SSO
- servers, SSO
- SSO, servers
- SSO, Master Secret server
ms.assetid: 40240d6b-b7d1-48fb-b750-be0e380d52e3
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 37f2f24911a0336a734125436d97dbce6f9e0b77
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="sso-server"></a><span data-ttu-id="784e1-102">SSO 伺服器</span><span class="sxs-lookup"><span data-stu-id="784e1-102">SSO Server</span></span>
<span data-ttu-id="784e1-103">「企業單一登入」(SSO) 伺服器可執行下列任何工作：</span><span class="sxs-lookup"><span data-stu-id="784e1-103">The Enterprise Single Sign-On (SSO) server can perform any of the following tasks:</span></span>  
  
-   <span data-ttu-id="784e1-104">**主要密碼伺服器當做函式。**</span><span class="sxs-lookup"><span data-stu-id="784e1-104">**Functions as the master secret server.**</span></span> <span data-ttu-id="784e1-105">主要密碼伺服器會存放一份主要密碼或金鑰的保存複本，可用來加密 SSO 系統中的所有認證。</span><span class="sxs-lookup"><span data-stu-id="784e1-105">The master secret server holds a persisted copy of the master secret, or key, used to encrypt all the credentials in the SSO system.</span></span> <span data-ttu-id="784e1-106">雖然主要密碼伺服器可做為查詢與管理的伺服器，但基於安全性理由，建議僅使用此伺服器做為主要密碼伺服器。</span><span class="sxs-lookup"><span data-stu-id="784e1-106">Though the master secret server can act as a server for lookups and administration, it is recommended to use this server to act only as a master secret server for security reasons.</span></span> <span data-ttu-id="784e1-107">如需詳細資訊的函式主要密碼伺服器會執行，請參閱[主要密碼伺服器](../core/master-secret-server.md)。</span><span class="sxs-lookup"><span data-stu-id="784e1-107">For more information about the functions the master secret server performs, see [Master Secret Server](../core/master-secret-server.md).</span></span>  
  
-   <span data-ttu-id="784e1-108">**執行管理作業。**</span><span class="sxs-lookup"><span data-stu-id="784e1-108">**Performs administrative operations.**</span></span> <span data-ttu-id="784e1-109">SSO 系統管理員可以使用任何單一登入伺服器來執行管理工作，像是管理分支機構應用程式、設定使用者認證以及管理使用者對應。</span><span class="sxs-lookup"><span data-stu-id="784e1-109">SSO administrators can use any of the Single Sign-On Servers to perform administrative tasks such as managing affiliate applications, setting user credentials, and managing user mappings.</span></span>  
  
-   <span data-ttu-id="784e1-110">**執行查詢作業。**</span><span class="sxs-lookup"><span data-stu-id="784e1-110">**Performs lookup operations.**</span></span> <span data-ttu-id="784e1-111">SSO 伺服器使用執行階段元件來查詢使用者認證。</span><span class="sxs-lookup"><span data-stu-id="784e1-111">The SSO server uses the runtime component to look up the user credentials.</span></span>  
  
-   <span data-ttu-id="784e1-112">**發出與贖回票證。**</span><span class="sxs-lookup"><span data-stu-id="784e1-112">**Issues and Redeems Tickets.**</span></span> <span data-ttu-id="784e1-113">SSO 伺服器還會發出與贖回 SSO 票證。</span><span class="sxs-lookup"><span data-stu-id="784e1-113">The SSO server also issues and redeems SSO tickets.</span></span>  
  
-   <span data-ttu-id="784e1-114">**密碼同步處理。**</span><span class="sxs-lookup"><span data-stu-id="784e1-114">**Password Synchronization.**</span></span> <span data-ttu-id="784e1-115">您可以在 SSO 伺服器上建立和管理密碼同步配接器。</span><span class="sxs-lookup"><span data-stu-id="784e1-115">You can create and manage password synchronization adapters on the SSO Server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="784e1-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="784e1-116">See Also</span></span>  
 <span data-ttu-id="784e1-117">[使用 SSO](../core/using-sso.md) </span><span class="sxs-lookup"><span data-stu-id="784e1-117">[Using SSO](../core/using-sso.md) </span></span>  
 [<span data-ttu-id="784e1-118">安裝 SSO</span><span class="sxs-lookup"><span data-stu-id="784e1-118">Installing SSO</span></span>](../core/installing-sso.md)