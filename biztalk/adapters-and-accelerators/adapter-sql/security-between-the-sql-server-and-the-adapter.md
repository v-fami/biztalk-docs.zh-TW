---
title: "SQL Server 與配接器之間的安全性 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c4b0fd11-6753-4f52-9be7-3b6fa330fb8b
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8673aee316a8a2ef83011ab3dd85016a99df1162
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="security-between-the-sql-server-and-the-adapter"></a>SQL Server 與配接器之間的安全性
[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]是相容的標準方法，例如 SSO 和 IPSEC 來保護資料交換與資料庫伺服器。 不安全的資料交換可以將資料公開給未經授權的動作項目。 如需與 SQL Server 的安全性問題的資訊，請參閱[的 SQL Server 的安全性考量](http://go.microsoft.com/fwlink/p/?LinkId=196954)SQL 文件中。  
  
 您可以使用網際網路通訊協定安全性 (IPsec) 來改善資料交換的安全性。 IPsec 是來保護通訊，網際網路通訊協定 (IP) 網路上的開放式標準的架構。 使用 IPSec，任何資料之間的交換[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]與 SQL 加密在網路上的伺服器，讓未經授權的動作項目来使用的資料。 如需有關 IPsec 以及使用 IPsec 與 Microsoft 產品的詳細資訊，請參閱 Microsoft TechNet 文章[IPsec](http://go.microsoft.com/fwlink/p/?LinkId=196955)。  
  
 [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]支援 SSO 和整合式安全性進行驗證，它會建立與資料庫的連接。 使用 SSO，這些認證會加密並儲存在登錄中。 系統會使用這些認證，來決定存取權限，而不需要使用者輸入，可能會看到它們由未經授權的動作項目。 整合式的安全性以存取 SQL server 使用登入的使用者的認證。 這也就不需要使用者輸入認證。 資料庫管理員必須設定為接受正常運作的整合式安全性的使用者認證的 SQL。  
  
## <a name="see-also"></a>另請參閱  
[保護 SQL 應用程式](../../adapters-and-accelerators/adapter-sql/secure-your-sql-applications.md)