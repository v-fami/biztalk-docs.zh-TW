---
title: "管理 Certificates2 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0e3bc75f-1a58-49d8-8a1d-6936b1a4105b
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0a810ae301f8d0ca55e171f775fae26f78953b6a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="managing-certificates"></a><span data-ttu-id="5cd31-102">管理憑證</span><span class="sxs-lookup"><span data-stu-id="5cd31-102">Managing Certificates</span></span>
<span data-ttu-id="5cd31-103">本章節描述如何管理數位簽章搭配[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="5cd31-103">This section describes how to manage digital certificates used with [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)].</span></span> <span data-ttu-id="5cd31-104">其主題描述如何安裝憑證 （並安裝到哪個資料夾），以及如何設定[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]MIME/SMIME 和 AS2，並使用 BizTalk 配接器使用的憑證。</span><span class="sxs-lookup"><span data-stu-id="5cd31-104">Its topics describe how to install certificates (and which folder to install them into), and how to configure [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to use the certificate for MIME/SMIME and AS2, and for use with BizTalk adapters.</span></span> <span data-ttu-id="5cd31-105">Microsoft[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]可以讓的公開金鑰基礎結構 (PKI) 數位憑證用於文件加密和解密的用途、 文件簽署和驗證 （不可否認性），且合作對象解析。</span><span class="sxs-lookup"><span data-stu-id="5cd31-105">Microsoft [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] can make use of public key infrastructure (PKI) digital certificates for purposes of document encryption and decryption, document signing and verification (non-repudiation), and party resolution.</span></span>  
  
 <span data-ttu-id="5cd31-106">若要安裝憑證的步驟的檢查清單，請參閱[檢查清單： 安裝和設定憑證](~/technical-guides/checklist-installing-and-configuring-certificates.md)。</span><span class="sxs-lookup"><span data-stu-id="5cd31-106">For a checklist of steps to install the certificates, see [Checklist: Installing and Configuring Certificates](~/technical-guides/checklist-installing-and-configuring-certificates.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5cd31-107">本節內容</span><span class="sxs-lookup"><span data-stu-id="5cd31-107">In This Section</span></span>  
  
-   [<span data-ttu-id="5cd31-108">管理 Certificates2 的最佳作法</span><span class="sxs-lookup"><span data-stu-id="5cd31-108">Best Practices for Managing Certificates2</span></span>](../technical-guides/best-practices-for-managing-certificates2.md)  
  
-   [<span data-ttu-id="5cd31-109">在 BizTalk Server 中憑證的已知的問題</span><span class="sxs-lookup"><span data-stu-id="5cd31-109">Known Issues with Certificates in BizTalk Server</span></span>](../technical-guides/known-issues-with-certificates-in-biztalk-server.md)  
  
-   [<span data-ttu-id="5cd31-110">安裝和設定數位簽章</span><span class="sxs-lookup"><span data-stu-id="5cd31-110">Installing and Configuring Digital Certificates</span></span>](~/technical-guides/installing-and-configuring-digital-certificates.md)