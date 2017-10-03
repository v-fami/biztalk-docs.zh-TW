---
title: "Siebel 系統與配接器之間的安全性 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security, IPsec
- connection URI
- security considerations, between the Siebel system and the adapter
ms.assetid: 40b03d4e-f489-4dce-ba7b-6b6f394275ac
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cb9ced17c00432039ff3b85ac85d56e1b6031049
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="security-between-the-siebel-system-and-the-adapter"></a>Siebel 系統與配接器之間的安全性
## <a name="encryption-and-authentication"></a>加密及驗證
[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]可以支援 rsa 或 mscrypto 加密交換與 Siebel 系統的資料。 您可以設定透過查詢字串參數的加密模式中連線的 URI。 如需有關 Siebel 連線 URI 的詳細資訊，請參閱[建立 Siebel 系統連接 URI](../../adapters-and-accelerators/adapter-siebel/create-the-siebel-system-connection-uri.md)。 如需 rsa 和 mscrypto siebel 的加密支援的詳細資訊，請參閱 Siebel 文件。  
  
 指定加密模式可以協助確保隱私權的介面卡與 Siebel 系統之間交換資料不過，[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]不提供支援這類交換的授權、 驗證或資料完整性的機制。 如果您的環境中的顧慮，這些問題，您必須提供可協助減輕這些安全性機制。  
  
 一個可能的機制，可協助在網路上提供更高的安全性是網際網路通訊協定安全性 (IPsec)。 IPsec 是來保護通訊，網際網路通訊協定 (IP) 網路上的開放式標準的架構。 如需有關 IPsec 以及使用 IPsec 與 Microsoft 產品的詳細資訊，請參閱 Microsoft TechNet 文章"IPsec 」 在[http://go.microsoft.com/fwlink/?LinkID=196851](http://go.microsoft.com/fwlink/?LinkID=196851)。  
  
 [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]支援，它會建立與 Siebel 系統，透過您提供的使用者名稱密碼認證，連接上的授權和驗證。 [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]時在開啟連線，驗證 Siebel 系統上的使用者會使用這些認證。 這些認證提供 Siebel 系統的連線層級的授權。 [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]提供多種方法，您可以透過此提供這些認證。 如需如何更安全的方式提供 Siebel BizTalk 方案中的認證資訊，請參閱[Siebel 配接器與 BizTalk Server 安全性](../../adapters-and-accelerators/adapter-siebel/security-with-siebel-adapter-and-biztalk-server.md)。 如需如何以更安全地提供程式設計的方案中的 Siebel 系統認證資訊，請參閱[Siebel 配接器使用的安全程式設計](../../adapters-and-accelerators/adapter-siebel/secure-programming-with-the-siebel-adapter.md)。  
  
> [!NOTE]
>  所使用的認證[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]來連接到 Siebel 系統不提供訊息層級或傳輸層級的驗證或授權的網路上傳輸的資料。 它們只用來開啟連接，並針對 Siebel 系統驗證使用者。  
  
## <a name="see-also"></a>另請參閱  
[保護您的 Siebel 應用程式](../../adapters-and-accelerators/adapter-siebel/secure-your-siebel-applications.md)