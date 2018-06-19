---
title: 管理主要密碼 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Master Secret server, managing
- managing [Master Secret server]
- SSO, Master Secret server
ms.assetid: f79e8f3f-c740-4ea1-9589-b42552fcd52d
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c2505fa6f5ec1abc04ded45e7701fd4e5212f889
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22262174"
---
# <a name="managing-the-master-secret"></a><span data-ttu-id="10bdc-102">管理主要密碼</span><span class="sxs-lookup"><span data-stu-id="10bdc-102">Managing the Master Secret</span></span>
<span data-ttu-id="10bdc-103">主要密碼是用以加密所有儲存在 SSO 資料庫中之資訊的金鑰。</span><span class="sxs-lookup"><span data-stu-id="10bdc-103">The master secret is the key used to encrypt all the information stored in the SSO database.</span></span> <span data-ttu-id="10bdc-104">若主要密碼伺服器失敗且密碼遺失，您將無法擷取儲存在 SSO 資料庫中的資訊。</span><span class="sxs-lookup"><span data-stu-id="10bdc-104">If the master secret server fails and you lose the secret, you will not be able to retrieve the information stored in the SSO database.</span></span> <span data-ttu-id="10bdc-105">因此，請務必在產生主要密碼之後立即備份。</span><span class="sxs-lookup"><span data-stu-id="10bdc-105">Therefore, it is very important to back up the master secret as soon as you generate it.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="10bdc-106">本節內容</span><span class="sxs-lookup"><span data-stu-id="10bdc-106">In This Section</span></span>  
  
-   [<span data-ttu-id="10bdc-107">如何產生主要密碼</span><span class="sxs-lookup"><span data-stu-id="10bdc-107">How to Generate the Master Secret</span></span>](../core/how-to-generate-the-master-secret.md)  
  
-   [<span data-ttu-id="10bdc-108">如何備份主要密碼</span><span class="sxs-lookup"><span data-stu-id="10bdc-108">How to Back Up the Master Secret</span></span>](../core/how-to-back-up-the-master-secret.md)  
  
-   [<span data-ttu-id="10bdc-109">如何還原主要密碼</span><span class="sxs-lookup"><span data-stu-id="10bdc-109">How to Restore the Master Secret</span></span>](../core/how-to-restore-the-master-secret.md)  
  
-   [<span data-ttu-id="10bdc-110">如何移動主要密碼伺服器</span><span class="sxs-lookup"><span data-stu-id="10bdc-110">How to Move the Master Secret Server</span></span>](../core/how-to-move-the-master-secret-server.md)