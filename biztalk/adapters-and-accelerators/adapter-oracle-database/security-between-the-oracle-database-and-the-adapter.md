---
title: Oracle 資料庫與配接器之間的安全性 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- adapter, security
- authorization
- credentials, supplying user name password
- authentication
- IPsec
ms.assetid: 09d40a05-3678-4002-9e08-2f97c2d5c686
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: eb27f87bceaba6039588ddcad6b5dcb2d3ce79ce
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22215702"
---
# <a name="security-between-the-oracle-database-and-the-adapter"></a>Oracle 資料庫與配接器之間的安全性
[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]不提供支援以便它與 Oracle 資料庫之間的安全通訊。 您必須提供安全性機制，以協助確保適當的授權、 驗證、 資料隱私權和資料配接器與 Oracle 資料庫之間的交換的資料完整性層級。  
  
 一個可能的機制，可協助在網路上提供更高的安全性是網際網路通訊協定安全性 (IPsec)。 IPsec 是來保護通訊，網際網路通訊協定 (IP) 網路上的開放式標準的架構。 如需有關 IPsec 以及使用 IPsec 與 Microsoft 產品的詳細資訊，請參閱 Microsoft TechNet 文章"IPsec 」 在[http://go.microsoft.com/fwlink/?LinkId=196851](http://go.microsoft.com/fwlink/?LinkId=196851)。  
  
 不過，安全性機制，例如 IPsec 不存在，系統管理員必須設定原生的 Oracle 資料加密和完整性，以確保配接器用戶端與 Oracle 資料庫之間的安全資料交換。 如需設定原生的 Oracle 資料加密及完整性的詳細資訊，請參閱[http://go.microsoft.com/fwlink/p/?LinkId=140032](http://go.microsoft.com/fwlink/p/?LinkId=140032)。  
  
 您必須提供使用者名稱密碼認證，才能[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。 [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]來驗證使用者的 Oracle 資料庫上，開啟連接時，會使用這些認證。 這些認證提供連接的 Oracle 資料庫上的層級的授權。  
  
> [!NOTE]
>  所使用的認證[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]建立 Oracle 資料庫上的連線不提供訊息層級或傳輸層級的驗證或授權的網路上傳輸的資料。 它們只用來開啟連接和驗證使用者的 Oracle 資料庫上。  
  
 [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]提供多種方法，您可以透過此提供這些認證。 如需如何更安全地提供 BizTalk 方案中的 Oracle 認證資訊，請參閱[安全性與 Oracle 資料庫配接器和 Biztalk Server](../../adapters-and-accelerators/adapter-oracle-database/security-with-the-oracle-database-adapter-and-biztalk-server.md)。 如需如何更安全地提供程式設計的方案中的 Oracle 資料庫認證資訊，請參閱[安全使用 Oracle 資料庫配接器程式設計](../../adapters-and-accelerators/adapter-oracle-database/secure-programming-with-the-oracle-database-adapter.md)。  
  
## <a name="managing-audit-logs"></a>管理稽核記錄檔  
 稽核記錄檔可讓您將儲存企業軟體及 「 協助使用量監視和追蹤問題的各種用戶端所執行之動作的相關資訊。 不過，[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]不提供任何方法來管理配接器用戶端的 Oracle 資料庫上所執行之動作的稽核記錄檔。 因為配接器用戶端可以 repudiate 的 Oracle 資料庫上所執行的動作，這可能會造成安全性威脅。 若要減輕這個問題，您必須啟用稽核記錄在 Oracle 中記錄的 Oracle 資料庫上的配接器用戶端所執行的動作。  
  
## <a name="see-also"></a>另請參閱  
[保護您的 Oracle 資料庫應用程式](../../adapters-and-accelerators/adapter-oracle-database/secure-your-oracle-database-applications.md)   
[最佳作法](../../adapters-and-accelerators/adapter-oracle-database/best-practices-to-secure-the-oracle-database-adapter.md)