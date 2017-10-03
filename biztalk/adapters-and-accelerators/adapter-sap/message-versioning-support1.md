---
title: "訊息版本控制 Support1 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: message versioning, support for
ms.assetid: 650b966e-9fa6-4af8-a061-7852a892717a
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7a2175ba0a3aafd052e6830439800569cf5f005f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="message-versioning-support"></a><span data-ttu-id="49954-102">訊息版本控制支援</span><span class="sxs-lookup"><span data-stu-id="49954-102">Message Versioning Support</span></span>
<span data-ttu-id="49954-103">[!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]訊息動作、 命名空間和節點識別碼中包含的版本字串元件的支援版本控制作業中顯示。</span><span class="sxs-lookup"><span data-stu-id="49954-103">The [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] supports versioning by including a version string component in the message actions, namespaces, and node IDs surfaced for operations.</span></span> <span data-ttu-id="49954-104">目前的版本是 http://Microsoft.LobServices.Sap/2007/03。</span><span class="sxs-lookup"><span data-stu-id="49954-104">The current version is http://Microsoft.LobServices.Sap/2007/03.</span></span> <span data-ttu-id="49954-105">這表示名為"RFC_SAMPLE"rfc，配接器所顯示的 RFC 作業具有下列：</span><span class="sxs-lookup"><span data-stu-id="49954-105">This means that for an RFC named "RFC_SAMPLE", the RFC operation surfaced by the adapter has the following:</span></span>  
  
-   <span data-ttu-id="49954-106">節點 ID: http://Microsoft.LobServices.Sap/2007/03/Rfc/RFC_SAMPLE</span><span class="sxs-lookup"><span data-stu-id="49954-106">Node ID: http://Microsoft.LobServices.Sap/2007/03/Rfc/RFC_SAMPLE</span></span>  
  
-   <span data-ttu-id="49954-107">訊息的動作： http://Microsoft.LobServices.Sap/2007/03/Rfc/RFC_SAMPLE</span><span class="sxs-lookup"><span data-stu-id="49954-107">Message action: http://Microsoft.LobServices.Sap/2007/03/Rfc/RFC_SAMPLE</span></span>  
  
-   <span data-ttu-id="49954-108">命名空間： http://Microsoft.LobServices.Sap/2007/03/Rfc</span><span class="sxs-lookup"><span data-stu-id="49954-108">Namespace: http://Microsoft.LobServices.Sap/2007/03/Rfc</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="49954-109">這項功能不提供與舊版配接器的回溯相容性。</span><span class="sxs-lookup"><span data-stu-id="49954-109">This feature does not provide backward compatibility with the earlier versions of the adapter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49954-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="49954-110">See Also</span></span>  
 [<span data-ttu-id="49954-111">訊息和訊息結構描述，BizTalk adapter for mySAP Business Suite</span><span class="sxs-lookup"><span data-stu-id="49954-111">Messages and Message Schemas for BizTalk Adapter for mySAP Business Suite</span></span>](../../adapters-and-accelerators/adapter-sap/messages-and-message-schemas-for-biztalk-adapter-for-mysap-business-suite.md)