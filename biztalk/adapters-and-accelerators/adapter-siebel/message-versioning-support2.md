---
title: 訊息版本控制 Support2 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- message versioning, support for
ms.assetid: 5b7b9202-9f45-450e-918f-b26a03711aab
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 04514a9c55fa29a930b6ba7467177d6a754ff3db
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22221854"
---
# <a name="message-versioning-support"></a><span data-ttu-id="91e7c-102">訊息版本控制支援</span><span class="sxs-lookup"><span data-stu-id="91e7c-102">Message Versioning Support</span></span>
<span data-ttu-id="91e7c-103">[!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)]訊息動作、 命名空間和節點識別碼中包含的版本字串元件的支援版本控制作業中顯示。</span><span class="sxs-lookup"><span data-stu-id="91e7c-103">The [!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)] supports versioning by including a version string component in the message actions, namespaces, and node IDs surfaced for operations.</span></span> <span data-ttu-id="91e7c-104">目前的版本是 http://Microsoft.LobServices.Siebel/2007/03。</span><span class="sxs-lookup"><span data-stu-id="91e7c-104">The current version is http://Microsoft.LobServices.Siebel/2007/03.</span></span> <span data-ttu-id="91e7c-105">這表示在 Siebel 儲存機制中的帳戶商務物件上插入作業，配接器所顯示的插入作業具有下列：</span><span class="sxs-lookup"><span data-stu-id="91e7c-105">This means that for an Insert operation on an Account business object in the Siebel repository, the Insert operation surfaced by the adapter has the following:</span></span>  
  
-   <span data-ttu-id="91e7c-106">節點 ID: http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects/Account/Account/Insert</span><span class="sxs-lookup"><span data-stu-id="91e7c-106">Node ID: http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects/Account/Account/Insert</span></span>  
  
-   <span data-ttu-id="91e7c-107">訊息的動作： http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects/Account/Account/Insert</span><span class="sxs-lookup"><span data-stu-id="91e7c-107">Message action: http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects/Account/Account/Insert</span></span>  
  
-   <span data-ttu-id="91e7c-108">命名空間： http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects/Account/Account/Operation</span><span class="sxs-lookup"><span data-stu-id="91e7c-108">Namespace: http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects/Account/Account/Operation</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="91e7c-109">這項功能不提供與舊版配接器的回溯相容性。</span><span class="sxs-lookup"><span data-stu-id="91e7c-109">This feature does not provide backward compatibility with the earlier versions of the adapter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91e7c-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="91e7c-110">See Also</span></span>  
 [<span data-ttu-id="91e7c-111">訊息和訊息結構描述，BizTalk adapter for Siebel eBusiness 應用程式</span><span class="sxs-lookup"><span data-stu-id="91e7c-111">Messages and Message Schemas for BizTalk Adapter for Siebel eBusiness Applications</span></span>](../../adapters-and-accelerators/adapter-siebel/messages-and-message-schemas-for-siebel-adapter-in-biztalk.md)