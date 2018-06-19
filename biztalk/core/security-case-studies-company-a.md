---
title: 安全性個案研究： 公司 A |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- security, examples
- security, architecture
- architecture, security
- security, case studies
ms.assetid: 9417ecf9-e340-479f-b120-552c62f3b189
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3c1f48edfc2ab2228d910a0729025fd7b4da117f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22269942"
---
# <a name="security-case-studies-company-a"></a>安全性個案研究： 公司 A
公司 A 是工業方面材料與服務的主要供應商。 其商務模型需仰賴與重要客戶與供應商的電子交易。 公司 A 使用 Microsoft BizTalk Application 來管理內部與外部環境之間的交易與通訊。  
  
## <a name="potential-threats-and-security-concerns"></a>潛在威脅與安全性考量  
 公司 A 要確定它只會處理來自已驗證來源的訊息。 BizTalk Server 處理的一些文件可以包含敏感性資訊，像是財務與個人資料。 公司 A 使用自訂的加密 API 來驗證內送訊息。 它還建置自己的實體架構來處理安全性需求。  
  
 公司 A 使用檔案傳輸通訊協定 (FTP) 提供其部分訊息流量。 雖然 FTP 基本上並不安全，但公司 A 可接受相關風險，因為它有許多防火牆來協助保護其他對外應用程式的安全。 因為公司 A 會透過 HTTPS 接受一些內送資料，所以來自外部來源的拒絕服務 (DoS) 攻擊是一個考量點。 若是發生 DoS 攻擊，公司有對應的機制可以立即警示適當的人員。  
  
## <a name="security-architecture"></a>安全性架構  
 下圖顯示公司 A 使用的安全性架構。 請注意，它以防火牆將其環境分段，以協助保護它的前端應用程式與內容伺服器、後端資料庫與商務邏輯伺服器，以及外送訊息基礎結構。  
  
 **圖 1 公司 A 安全性架構**  
  
 ![公司 A 安全性架構](../core/media/airproductsbiztalkinfrastructure.gif "AirProductsBizTalkInfrastructure")  
  
 公司 A 有兩個主要方法來傳送和接收 BizTalk Server 的資訊。 第一種方法是使用 FTP。 公司 A 使用協力廠商轉譯服務提供者來支援電子資料交換 (EDI)，以和它的供應商及夥伴通訊。 此協力廠商轉譯服務提供者以 EDI 格式處理 BizTalk Server 必須處理的內送與外送訂單。  
  
 公司 A 所使用的第二種方法是 HTTPS。 公司 A 還使用協力廠商服務提供者做為其工業的中樞，並使公司 A 銷售和消費產品的採購與銷售更容易。  
  
## <a name="secure-digital-certificates"></a>安全數位憑證  
 公司 A 實作它自己的安全數位憑證。 它只管理少數憑證。 因為它使用協力廠商服務提供者，所以比較不關注數位憑證。 公司 A 瞭解服務提供者比較關注數位憑證，因為服務提供者會和許多不同的機構互動。  
  
## <a name="see-also"></a>另請參閱  
 [小型與中型公司的安全性案例研究](../core/security-case-studies-for-small-to-medium-sized-companies.md)    
 [威脅模型分析的範例案例](../core/sample-scenarios-for-threat-model-analysis.md)