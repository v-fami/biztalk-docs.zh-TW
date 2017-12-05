---
title: "減少阻絕服務攻擊 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IPSec, message protection
- messages, size
- security, configuring
- Authentication Required property
- security, Internet Information Services (IIS) Lockdown Tool
- security, Denial of Service attacks
- discretionary access control lists (DACLs)
- IPSec, data protection
- Internet Information Services (IIS) Lockdown Tool
- Denial of Service attacks
ms.assetid: f39c0d0a-b890-4c48-874d-5cafbc71473c
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a02e3eddcd43acf67e8e928e1a8f172c0019c616
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="mitigating-denial-of-service-attacks"></a>減少阻絕服務攻擊
建議您使用下列防護技術，協助保護 BizTalk Server 與服務免於遭受拒絕服務的攻擊。 您必須決定其中哪些防護技術適用於您的環境。  
  
-   **接收埠中使用的所需的驗證屬性。** 依照預設，BizTalk 會將它接收的所有訊息傳送到 MessageBox 資料庫，即使訊息是來自不明或無法解析的合作對象 (來賓使用者) 也一樣。若要減少潛在的攻擊者傳送大量訊息至 BizTalk Server，而灌爆 （塞滿） MessageBox 資料庫中，您可以使用**需要驗證**接收埠只接收中的屬性來自 BizTalk Server 知道的合作對象的訊息。 您可以選擇捨棄來自不明合作對象的訊息，或是擱置那些訊息。 如需有關**需要驗證**屬性，請參閱[驗證訊息的傳送者](../core/authenticating-the-sender-of-a-message.md)。 除了**需要驗證**屬性，您應該考慮使用外部機制，例如防火牆連接埠篩選或 IP 位址封鎖來防止阻絕服務攻擊。  
  
-   **限制 BizTalk 可接收的訊息大小。** 例如，當您使用 SOAP 接收配接器，您可以避免接收非常大型的訊息大小的 maxRequestLength 屬性設定\<httpRuntime\>項目為可接受的大小。 \<HttpRuntime\>項目會定義在 Machine.config 檔案中，位於\<*磁碟機*\>:\\<*Windows目錄*\>\Microsoft.NET\Framework\vX.X.XXXXX\CONFIG 目錄。 如需有關\<httpRuntime\>項目，請參閱 Microsoft MSDN 網站，網址[http://go.microsoft.com/fwlink/?LinkId=60948](http://go.microsoft.com/fwlink/?LinkId=60948)。  
  
-   **使用強式 Dacl，為接收位置。** 建議您在接收位置的放置位置使用強式判別存取控制清單 (DACL)。 例如，您必須在目錄中使用強式 DACL，檔案接收位置在此目錄拾取訊息，使得只有授權的使用者可以在此位置放置訊息。  
  
-   **使用 IPSec。** 若您不使用硬體或軟體防火牆，請使用網際網路通訊協定安全性 (IPSec) 來協助保護 BizTalk 將訊息從伺服器傳送到另一個伺服器時訊息與資料的安全。 如需 IPSec 的詳細資訊，請參閱 Microsoft 下載中心[http://go.microsoft.com/fwlink/?LinkId=60949](http://go.microsoft.com/fwlink/?LinkId=60949)。  
  
## <a name="see-also"></a>請參閱  
 [識別潛在威脅](../core/identifying-potential-threats.md)   
 [安全性規劃](../core/planning-for-security.md)